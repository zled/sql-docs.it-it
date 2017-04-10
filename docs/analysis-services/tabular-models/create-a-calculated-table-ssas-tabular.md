---
title: "Creare una tabella calcolata (SSAS tabulare) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3d7ff98a-82a9-4333-a7d3-7a95a6f2caf7
caps.latest.revision: 10
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 10
---
# Creare una tabella calcolata (SSAS tabulare)
  Una *tabella calcolata* è un oggetto calcolato, basato su una query o un'espressione DAX, derivato per intero o in parte da altre tabelle nello stesso modello.  
  
 Un problema di progettazione comune che possono risolvere le tabelle calcolate è esporre una dimensione con ruoli multipli in un contesto specifico in modo che sia possibile esporla come struttura di query nelle applicazioni client.  Si ricorderà che una dimensione con ruoli multipli è semplicemente una tabella esposta in più contesti. Un esempio classico è la tabella Data, esposta come DataOrdine, DataSpedizione o DataScadenza, in base alla relazione di chiave esterna. Creando una tabella calcolata per DataSpedizione in modo esplicito, è possibile ottenere una tabella autonoma disponibile per le query, utilizzabile in modo completo come qualsiasi altra tabella.  
  
 Un altro possibile uso per una colonna calcolata include la configurazione di un set di righe filtrato o di un subset o superset di colonne da altre tabelle esistenti. Questo consente di mantenere la tabella originale intatta e di creare allo stesso tempo varianti della tabella per supportare scenari specifici.  
  
 Per un uso ottimale delle tabelle calcolate è necessario conoscere i principi di base delle espressioni DAX. Durante la definizione delle espressioni per una tabella, può essere utile sapere che una colonna calcolata contiene una singola partizione con un'origine DAXSource, in cui l'espressione è un'espressione DAX.  
Esiste una sola CalculatedTableColumn per ogni colonna restituita dall'espressione, dove SourceColumn è il nome della colonna restituita (in modo analogo a DataColumn nelle tabelle non calcolate).  
  
## Come creare una tabella calcolata  
  
1.  Verificare innanzitutto che il modello tabulare abbia il livello di compatibilità 1200. È possibile controllare la proprietà **Livello di compatibilità** nel modello in SSDT.  
  
2.  Passare alla vista dati. Non è possibile creare una tabella calcolata nelle vista diagramma.  
  
3.  Selezionare **Tabella** > **Nuova tabella calcolata**.  
  
4.  Digitare o incollare un'espressione DAX (vedere di seguito per alcune idee).  
  
5.  Assegnare un nome alla tabella.  
  
6.  Creare relazioni con altre tabelle nel modello. Per altre informazioni su questo passaggio, vedere [Creare una relazione tra due tabelle &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/create-a-relationship-between-two-tables-ssas-tabular.md).  
  
7.  Fare riferimento alla tabella nei calcoli o nelle espressioni nel modello o usare la funzionalità **Analizza in Excel** per l'esplorazione dei dati ad hoc.  
  
### Replicare una dimensione con ruoli multipli  
 Nella barra della formula immettere una formula DAX che recupera una copia di un'altra tabella. Dopo il popolamento della tabella calcolata, assegnarle un nome descrittivo e quindi impostare una relazione che usa la chiave esterna specifica per il ruolo. Nel database Adventure Works, ad esempio, si potrebbe creare una tabella calcolata per Due Date e usare DueDateKey come base per una relazione con la tabella dei fatti.  
  
```  
=DimDate  
```  
  
### Set di dati riepilogato o filtrato  
 Nella barra della formula immettere un'espressione DAX che consente di filtrare, riepilogare e modificare in altri modi un set di dati in modo che contenga le righe desiderate. Questo esempio raggruppa le vendite per colore e valuta.  
  
```  
=SUMMARIZECOLUMNS(DimProduct[Color]  
, DimCurrency[CurrencyName]   
, "Sales" , SUM(FactInternetSales[SalesAmount])  
)  
```  
  
### Superset che usa le colonne da più tabelle  
 Nella barra della formula immettere un'espressione DAX che combina le colonne da più tabelle. In questo caso, l'output della query elenca la categoria di prodotto per ogni valuta.  
  
```  
=CROSSJOIN(DimProductCategory, DimCurrency)  
```  
  
## Vedere anche  
 [Livello di compatibilità per i modelli tabulari in Analysis Services](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)   
 [Data Analysis Expressions &#40;DAX&#41; in Analysis Services](../Topic/Data%20Analysis%20Expressions%20\(DAX\)%20in%20Analysis%20Services.md)   
 [Informazioni su DAX nei modelli tabulari &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/understanding-dax-in-tabular-models-ssas-tabular.md)  
  
  