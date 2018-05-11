---
title: Funzionalità supportate dalle edizioni di SQL Server 2016 di Analysis Services | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 51225d83d66a6168760cc0e91e36bd55730cd539
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="analysis-services-features-supported-by-sql-server-editions"></a>Caratteristiche di Analysis Services supportate dalle edizioni di SQL Server
[!INCLUDE[ssas-appliesto-sql2016-later](../includes/ssas-appliesto-sql2016-later.md)]

In questo argomento fornisce i dettagli delle funzionalità supportate dalle diverse edizioni di SQL Server 2016 Analysis Services. Per le funzionalità supportate dalle edizioni Evaluation e Developer, vedere Enterprise edition.

## <a name="analysis-services-servers"></a>Analysis Services (server)
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Database condivisi scalabili|Sì||||||Sì|  
|Backup/ripristino e collegamento/scollegamento di database|Sì|Sì|||||Sì|  
|Sincronizzare database|Sì||||||Sì|  
|Istanze del cluster di failover Always On|Sì<br /><br /> Il numero di nodi è il valore massimo del sistema operativo|Sì<br /><br /> Supporto per 2 nodi|||||Sì<br /><br /> Il numero di nodi è il valore massimo del sistema operativo|  
|Programmabilità (AMO, ADOMD.Net, OLEDB, XML/A, ASSL, TMSL)|Sì|Sì|||||Sì|  
  
## <a name="tabular-models"></a>Modelli tabulari 
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Gerarchie|Sì|Sì|||||Sì|  
|KPI|Sì|Sì|||||Sì|  
|Prospettive|Sì||||||Sì|  
|Traduzioni|Sì|Sì|||||Sì|  
|Calcoli DAX, query DAX, query MDX|Sì|Sì|||||Sì|  
|Sicurezza a livello di riga|Sì|Sì|||||Sì|  
|Più partizioni|Sì||||||Sì|  
|Modalità di archiviazione in memoria|Sì|Sì|||||Sì|  
|Modalità di archiviazione DirectQuery|Sì||||||Sì|  

## <a name="multidimensional-models"></a>Modelli multidimensionali 
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Misure semiadditive|Sì|No <sup>1</sup>|||||Sì|  
|Gerarchie|Sì|Sì|||||Sì|  
|KPI|Sì|Sì|||||Sì|  
|Prospettive|Sì||||||Sì|  
|Azioni|Sì|Sì|||||Sì|  
|Funzionalità di Business Intelligence per la contabilità|Sì|Sì|||||Sì|  
|Business Intelligence per gerarchie temporali|Sì|Sì|||||Sì|  
|Rollup personalizzati|Sì|Sì|||||Sì|  
|Cubo writeback|Sì|Sì|||||Sì|  
|Dimensioni writeback|Sì||||||Sì|  
|Celle writeback|Sì|Sì|||||Sì|  
|Drill-through|Sì|Sì|||||Sì|  
|Tipi di gerarchia avanzati (padre-figlio e gerarchie incomplete)|Sì|Sì|||||Sì|  
|Dimensioni avanzate (dimensioni di riferimento, dimensioni molti-a-molti)|Sì|Sì|||||Sì|  
|Dimensioni e misure collegate|Sì|Sì  <sup>2</sup> |||||Sì|  
|Traduzioni|Sì|Sì|||||Sì|  
|Aggregations|Sì|Sì|||||Sì|  
|Più partizioni|Sì|Sì, fino a 3|||||Sì|  
|Memorizzazione nella cache attiva|Sì||||||Sì|  
|Assembly personalizzati (stored procedure)|Sì|Sì|||||Sì|  
|Query e script MDX|Sì|Sì|||||Sì|  
|Query DAX|Sì|Sì|||||Sì|  
|Modello di sicurezza basato su ruoli|Sì|Sì|||||Sì|  
|Sicurezza a livello di cella e dimensione|Sì|Sì|||||Sì|  
|Archivio di stringhe scalabile|Sì|Sì|||||Sì|  
|Modelli di archiviazione MOLAP, ROLAP e HOLAP|Sì|Sì|||||Sì|  
|Trasporto XML binario e compresso|Sì|Sì|||||Sì|  
|Elaborazione in modalità push|Sì||||||Sì|  
|Writeback diretto|Sì||||||Sì|  
|Espressioni di misura|Sì||||||Sì|  
  
 <sup>1</sup> La misura semiadattiva LastChild è supportata nell'edizione Standard, mentre altre misure semiadattive come None, FirstChild, FirstNonEmpty, LastNonEmpty, AverageOfChildren e ByAccount non lo sono. Le misure additive, ad esempio Sum, Count, Min, Max e quelle non additive (DistinctCount) sono supportate in tutte le edizioni.  
  <sup>2</sup> standard edition supporta il collegamento misure e dimensioni all'interno del database stesso, ma non da altri database o istanze.
  
## <a name="power-pivot-for-sharepoint"></a>PowerPivot per SharePoint  
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Integrazione di farm SharePoint basata sull'architettura di servizi condivisi|Sì||||||Sì|  
|Report sull'utilizzo|Sì||||||Sì|  
|Regole di monitoraggio dell'integrità|Sì||||||Sì|  
|Raccolta Power Pivot|Sì||||||Sì|  
|Aggiornamento dati Power Pivot|Sì||||||Sì|  
|Feed di dati Power Pivot|Sì||||||Sì|  
  
## <a name="data-mining"></a>Data Mining  
  
|Nome funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|------------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Algoritmi standard|Sì|Sì|||||Sì|  
|Strumenti di data mining (procedure guidate, editor, generatori di query)|Sì|Sì|||||Sì|  
|Convalida incrociata|Sì||||||Sì|  
|Modelli in base a subset filtrati di dati della struttura di data mining|Sì||||||Sì|  
|Time Series: combinazione personalizzata tra metodi ARTXP e ARIMA|Sì||||||Sì|  
|Time Series: stima con nuovi dati|Sì||||||Sì|  
|Query di data mining simultanee illimitate|Sì||||||Sì|  
|Opzioni di configurazione e ottimizzazione avanzate per algoritmi di data mining|Sì||||||Sì|  
|Supporto per algoritmi plug-in|Sì||||||Sì|  
|Elaborazione parallela dei modelli|Sì||||||Sì|  
|Time Series: stima incrociata tra serie|Sì||||||Sì|  
|Attributi illimitati per le regole di associazione|Sì||||||Sì|  
|Stima basata su sequenze|Sì||||||Sì|  
|Più destinazioni di stima per gli algoritmi Logistic Regression, Neural Network e Naïve Bayes|Sì||||||Sì|  
  
 ## <a name="see-also"></a>Vedere anche  
 [Specifiche di prodotto per SQL Server 2016](http://msdn.microsoft.com/library/6445fd53-6844-4170-a86b-7fe76a9f64cb)   
 [Installation for SQL Server](../database-engine/install-windows/installation-for-sql-server-2016.md) (Installazione per SQL Server)  


