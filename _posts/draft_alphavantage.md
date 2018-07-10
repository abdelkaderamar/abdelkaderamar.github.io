---
layout: single
title:  "Alphavantage"
date:   2018-06-12 16:00:00 +0100
categories:
  - Posts
tags:
  - C++
---

{% include toc %}

[AlphaVantage](https://alphavantage.co) est un service web qui donne la possibilité de récupérer (gratuitement) des données historiques sur des instruments financiers.
Pour les actions, ce service (qui rappelle *Yahoo Finance*) offre une API web REST pour consulter les données suivantes :
- Données intraday : OHLC (*Open*, *High*, *Low* et *Close*) et volume de la journée courante (ou précédente si le marché est fermée). On doit préciser l'intervalle de temps (1, 5, 15, 30 ou 60 minutes) et le nombre de données à récupérer (les 100 dernières par défaut ou toute la journée). Malheureusement, ce service n'est proposé que pour les actions américaines.
- Données journalières : le volume et l'OHLC de l'instrument pour les 100 derniers jours ou depuis Janvier 2000.
- Données hebdomadaires : le dernier jour de la semaine courante et les données des vendredi depuis Janvier 2000.
- Données mensuelles.

Pour les données journalières, hebdomadaires et mensuelles, le service propose deux type de fonction, adjustée et non adjustée pour prendre en compte les dividendes. Ces informations (le montant du dividende et le close adjusté) ne sont pas proposées pour les instruments européens.

Pour utiliser le service, il faut obtenir une clé. Cette opération est très simple et se fait en remplissant un simple formulaire.

> Screenshot

Voici quelques exemple de requêtes (remplacer API_KEY par votre clé) :
1. Les données journalières de *Saint-Gobain* des 20 dernières années
```
https://www.alphavantage.co/query?function=TIME_SERIES_DAILY&symbol=SGO.PA&outputsize=full&apikey=API_KEY
```
2. Les données journalières de *Société Générale* des 100 derniers jours
```
https://www.alphavantage.co/query?function=TIME_SERIES_DAILY&symbol=GLE.PA&apikey=XD6HTE47G8ZZIDRB
```
3. Les données mensuelles de *LVMH*
```
https://www.alphavantage.co/query?function=TIME_SERIES_MONTHLY&symbol=MC.PA&apikey=API_KEY
```

## AV.NET

### Installation

L’API peut être installée via le gestionnaire de package nuget. La page sur le site nuget.org est la suivante : [https://www.nuget.org/packages/Av.API/](https://www.nuget.org/packages/Av.API/).

### Utilisation

Pour récupérer les données d’Alpha Vantage, l’API propose le type AvStockProvider. Le constructeur de ce dernier reçoit en paramètre votre clé personnelle pour accéder aux services d’Alpha Vantage (pour rappel, l’obtention de cette clé peut se faire facilement à cette adresse https://www.alphavantage.co/support/#api-key).  Le type AvStockProvider fournit les méthodes pour récupérer les différents types de données historiques : 
1.	Données journalières 
```csharp
AvStockProvider provider = new AvStockProvider(avKey);
StockData stockData = provider.RequestDaily("SGO.PA");
```
2.	Données hebdomadaires :
```csharp
AvStockProvider provider = new AvStockProvider(avKey);
StockData stockData = provider.RequestWeekly("SGO.PA");
```
3.	Données mensuelles : 
```csharp
AvStockProvider provider = new AvStockProvider(avKey);
StockData stockData = provider.RequestMonthly("SGO.PA");
```
4.	Données en mode Batch : pour rappel, seul les stocks américains sont 
disponibles par cette fonction et uniquement pendant les heures d’ouverture 
du marché (ceci est dû au fait que cette source est fourni par 
[IEX](https://iextrading.com/) pour lequel je suis également entrain de
 développer une API [IEX.Net]( https://github.com/abdelkaderamar/av.net)).
 
```csharp
AvStockProvider provider = new AvStockProvider(avKey);
IDictionary<string, StockRealtime> batchData = provider.BatchRequest(new string[] { "MSFT", "IBM", "AAPL" });
```

L'objet `StockData` contient un ensemble de données de type `StockRealtime`. 
Chaque données de type `StockRealtime` est associée à une date. La définition 
d'un objet `StockRealtime` est la suivante : 

```csharp
    public class StockDataItem
    {
        public StockDataItem(DateTime dateTime)
        {
            DateTime = dateTime;
        }

        public DateTime DateTime { get; set; }
        public double Open { get; set; }
        public double High { get; set; }
        public double Low { get; set; }
        public double Close { get; set; }
        public long Volume { get; set; }
        public double AdjustedClose { get; set; }
    }
```

Alors qu'un objet `StockData` est défini comme ci-dessous : 
```csharp
   public class StockData
    {
        public StockData(string symbol)
        {
            Symbol = symbol;
            Data = new SortedDictionary<DateTime, StockDataItem>();
        }

        public string Symbol { get; }

        public IDictionary<DateTime, StockDataItem> Data { get; }
		
		// ...
	}
```

#### Utilisation de *AvRequestManager*
L’accès aux services d’Alpha Vantage a une contrainte sur la fréquence des requêtes à exécuter. La page [support d’Alpha Vantage]( https://www.alphavantage.co/support/#support) ne précise pas une limite de fréquence pour l’envoi des requêtes mais recommande d’envoyer les requêtes de manière espacée dans le temps. D’après les tests que j’ai effectués, un délai de deux secondes entre deux requêtes successives m’a permis d’éviter le problème. Lorsque le service reçoit trop de requêtes, le message suivant est retourné 

```
{
  "Information": "Please consider optimizing your API call frequency."
}
```

Pour cela, l’API fournit le type `AvRequestManager` qui permet de gérer les appels successifs.  Le constructeur reçoit en paramètre l’objet `AvStockProvider` et doit être démarré avec la méthode `start`

```csharp
AvRequestManager requestManager = new AvRequestManager(provider);
requestManager.Start();
```

C’est la méthode `Add` qui permet d’ajouter une requête à Alpha Vantage. La signature de cette fonction est la suivante :

```csharp
Add(RequestType requestType, string symbol, Action<RequestType, string, StockData> callback)
```

Le type RequestType est une enum qui définit les différents types de requêtes disponibles 

```csharp 
public enum RequestType { Daily, DailyAdjusted, Weekly, WeeklyAdjusted, Monthly, MonthlyAdjusted}
```

Voici un exemple d’utilisation de l’objet `AvRequestManager`

```csharp
AvStockProvider provider = new AvStockProvider(avKey);
AvRequestManager requestManager = new AvRequestManager(provider);
string[] stocks = new string[] { "SGO.PA", "GLE.PA", "BNP.PA", "VIV.PA", "RNO.PA", "CS.PA" };
requestManager.Start();
foreach (var stock in stocks)
{
         requestManager.Add(RequestType.Daily, stock, Callback);
         requestManager.Add(RequestType.Weekly, stock, Callback);
         requestManager.Add(RequestType.Monthly, stock, Callback);
}
requestManager.Stop(true);
```
On remarque à la fin l’appel à la méthode `AvRequestManager.Stop` avec le paramètre `true`. La valeur `true` permet d’exécuter toutes les requêtes en attente avant d’arrêter le thread du `AvRequestManager`.


