---
title: "Stored procedure di data mining (Analysis Services - Data mining) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "stored procedure [Analysis Services], data mining"
ms.assetid: a751856d-33bd-4788-9593-317b2826132d
caps.latest.revision: 26
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 26
---
# Stored procedure di data mining (Analysis Services - Data mining)
  A partire da [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supporta stored procedure che possono essere scritte in qualsiasi linguaggio gestito. I linguaggi gestiti supportati includono [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET, C# e C++ gestito. In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] è possibile chiamare direttamente le stored procedure tramite l'istruzione **CALL** o come parte di una query DMX (Data Mining Extensions).  
  
 Per altre informazioni sulla chiamata di stored procedure [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vedere [Chiamata di stored procedure](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/calling-stored-procedures.md).  
  
 Per informazioni generali sulla programmabilità di [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)], vedere [Programmazione di data mining](../../analysis-services/data-mining-programming.md).  
  
 Per informazioni aggiuntive sulla programmazione di oggetti di data mining, vedere l'articolo "[SQL Server Data Mining Programmability](http://go.microsoft.com/fwlink/?LinkId=93735)" in MSDN Library.  
  
> [!NOTE]  
>  Quando si eseguono query su modelli di data mining, in particolare quando si testano nuove soluzioni di data mining, potrebbe risultare utile chiamare le stored procedure di sistema utilizzate internamente dal motore di data mining. È possibile visualizzare i nomi di queste stored procedure di sistema mediante [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] per creare una traccia nel server [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e quindi creare, esplorare ed eseguire query sui modelli di data mining. [!INCLUDE[msCoName](../../includes/msconame-md.md)] non garantisce tuttavia la compatibilità delle stored procedure di sistema tra le versioni ed è pertanto consigliabile non usare mai chiamate alle stored procedure di sistema in un sistema di produzione. Per garantire la compatibilità, è invece consigliabile creare query mediante DMX o XML/A.  
  
## Argomenti della sezione  
  
-   [SystemGetCrossValidationResults &#40;Analysis Services - Data mining&#41;](../../analysis-services/data-mining/systemgetcrossvalidationresults-analysis-services-data-mining.md)  
  
-   [SystemGetClusterCrossValidationResults &#40;Analysis Services - Data mining&#41;](../../analysis-services/data-mining/systemgetclustercrossvalidationresults-analysis-services-data-mining.md)  
  
-   [SystemGetAccuracyResults &#40;Analysis Services - Data mining&#41;](../../analysis-services/data-mining/systemgetaccuracyresults-analysis-services-data-mining.md)  
  
-   [SystemGetClusterAccuracyResults &#40;Analysis Services - Data mining&#41;](../../analysis-services/data-mining/systemgetclusteraccuracyresults-analysis-services-data-mining.md)  
  
## Riferimento  
 [Creare script per le attività amministrative in Analysis Services](../../analysis-services/instances/script-administrative-tasks-in-analysis-services.md)  
  
## Vedere anche  
 [Convalida incrociata &#40;Analysis Services - Data mining&#41;](../../analysis-services/data-mining/cross-validation-analysis-services-data-mining.md)   
 [Scheda Convalida incrociata &#40;vista Grafico accuratezza modello di data mining&#41;](../Topic/Cross-Validation%20Tab%20\(Mining%20Accuracy%20Chart%20View\).md)   
 [Chiamata di una stored procedure](../../relational-databases/native-client-odbc-stored-procedures/calling-a-stored-procedure.md)  
  
  