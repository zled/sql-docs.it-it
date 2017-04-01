---
title: "Funzionalit&#224; di Analysis Services supportate dalle edizioni di SQL Server 2016 | Microsoft Docs"
ms.custom: ""
ms.date: "09/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
  - "analysis-services/multidimensional-tabular"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f09d7be1-bd63-43f8-b91c-bf19166b4457
caps.latest.revision: 4
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 3
---
# Funzionalit&#224; di Analysis Services supportate dalle edizioni di SQL Server 2016
In questo argomento vengono forniti i dettagli delle funzionalità supportate dalle diverse edizioni di [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
 SQL Server Evaluation Edition è disponibile per un periodo di valutazione di 180 giorni.  
  
 Per le note sulla versione più recenti, vedere [Note sulla versione di SQL Server 2016](../sql-server/sql-server-2016-release-notes.md). Per le ultime informazioni sulle novità, vedere [Novità di Analysis Services](../analysis-services/what-s-new-in-analysis-services.md).
    
 **Per provare SQL Server 2016**    
    
 > [![Download da Evaluation Center](../analysis-services/media/download.png)](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) **[Scaricare SQL Server 2016 da Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**    
    
> ![Macchina virtuale di Azure, small](../analysis-services/media/azure-virtual-machine-small.png) **[Attivare una macchina virtuale con SQL Server 2016 già installato](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016rtmenterprisewindowsserver2012r2/?wt.mc_id=sqL16_vm)**    
    
  
 Per le funzionalità supportate dalle edizioni Evaluation e Developer, vedere SQL Server Enterprise Edition.
  
 Per passare alla tabella per una tecnologia SQL Server, fare clic sul relativo collegamento: 
 
 -  [Analysis Services](#SSAS)  
  
-   [BI Semantic Model (multidimensionale)](#BIMD)  
  
-   [BI Semantic Model (tabulare)](#BIT)  
  
-   [Power Pivot per SharePoint](#PPSP)  
  
-   [Data Mining](#DM)  
  
-   [Client di Business Intelligence](#BIC)  

##  <a name="SSAS"></a> Analysis Services  
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Sviluppatore|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Database condivisi scalabili|Sì||||||Sì|  
|Backup/ripristino e collegamento/scollegamento di database|Sì|Sì|||||Sì|  
|Sincronizzare database|Sì||||||Sì|  
|Istanze del cluster di failover Always On|Sì<br /><br /> Il numero di nodi è il valore massimo del sistema operativo|Sì<br /><br /> Supporto per 2 nodi|||||Sì<br /><br /> Il numero di nodi è il valore massimo del sistema operativo|  
|Programmabilità (AMO, ADOMD.Net, OLEDB, XML/A, ASSL, TMSL)|Sì|Sì|||||Sì|  
  
##  <a name="BIMD"></a> BI Semantic Model (multidimensionale)  
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Sviluppatore|  
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
|Dimensioni e misure collegate|Sì|Sì <sup>2</sup> |||||Sì|  
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
  <sup>2</sup> L'edizione Standard supporta il collegamento di misure e dimensioni all'interno dello stesso database, ma non da altri database o istanze.
   
##  <a name="BIT"></a> BI Semantic Model (tabulare)  
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Sviluppatore|  
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
  
##  <a name="PPSP"></a> Power Pivot per SharePoint  
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Sviluppatore|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Integrazione di farm SharePoint basata sull'architettura di servizi condivisi|Sì||||||Sì|  
|Report sull'utilizzo|Sì||||||Sì|  
|Regole di monitoraggio dell'integrità|Sì||||||Sì|  
|Raccolta Power Pivot|Sì||||||Sì|  
|Aggiornamento dati Power Pivot|Sì||||||Sì|  
|Feed di dati Power Pivot|Sì||||||Sì|  
  
##  <a name="DM"></a> Data Mining  
  
|Nome funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Sviluppatore|  
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
  
##  <a name="BIC"></a> Client di Business Intelligence  
 Le seguenti applicazioni client del software sono disponibili nell'Area download Microsoft e sono disponibili come supporto per la creazione di documenti di Business Intelligence eseguiti in un'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Quando questi documenti vengono ospitati in un ambiente server, usare un'edizione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] supportata per tale tipo di documento. Nella tabella seguente viene indicata l'edizione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] contenente le funzionalità del server richieste per ospitare i documenti creati in queste applicazioni client.  
  
|Nome dello strumento|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Sviluppatore|  
|---------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Componenti aggiuntivi di data mining per Excel e Visio 2010 (.xlsx, .vsdx)|Sì|Sì|||||Sì|  
|[!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] 2010 e 2013 (.xlsx)|Sì||||||Sì|  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] (.xlsx)|Sì||||||Sì|  
  
> [!NOTE]  
>  1.  [!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] è un componente aggiuntivo di Excel per la creazione di cartelle di lavoro con un modello dati.  [!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] non dipende da [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], ma [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)] è necessario per la condivisione e la collaborazione in cartelle di lavoro Excel con un modello dati in SharePoint. Questa funzionalità è disponibile nell'ambito di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Enterprise Edition.  
>   
>      La funzionalità Power Pivot è predefinita in Excel 2016, quindi non è più necessario il componente aggiuntivo Power Pivot.  
> 2.  La tabella sopra riportata identifica le edizioni [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] richieste per abilitare gli strumenti client; le funzionalità possono tuttavia accedere ai dati ospitati in ogni edizione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 ## Vedere anche  
 [Funzionalità supportate dalle edizioni di SQL Server 2016](Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)  
 [Specifiche di prodotto per SQL Server 2016](../Topic/Product%20Specifications%20for%20SQL%20Server%202016.md)   
 [Installazione per SQL Server 2016](../database-engine/install-windows/installation-for-sql-server-2016.md)  

