---
title: Stored procedure di Data Mining (Analysis Services - Data Mining) | Documenti Microsoft
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 86de302df302ae12ca83216dff998b4c7b39333b
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="data-mining-stored-procedures-analysis-services---data-mining"></a>Stored procedure di data mining (Analysis Services - Data mining)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  A partire da [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supporta stored procedure che possono essere scritte in qualsiasi linguaggio gestito. I linguaggi gestiti supportati includono [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET, C# e C++ gestito. In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]è possibile chiamare direttamente le stored procedure tramite l'istruzione **CALL** o come parte di una query DMX (Data Mining Extensions).  
  
 Per altre informazioni sulla chiamata di stored procedure [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , vedere [Chiamata di stored procedure](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/calling-stored-procedures.md).  
  
 Per informazioni generali sulla programmabilità, vedere [dati di Data Mining programmazione](../../analysis-services/data-mining-programming.md).  
  
 Per informazioni aggiuntive sulla programmazione di oggetti di data mining, vedere l'articolo "[SQL Server Data Mining Programmability](http://go.microsoft.com/fwlink/?LinkId=93735)" in MSDN Library.  
  
> [!NOTE]  
>  Quando si eseguono query su modelli di data mining, in particolare quando si testano nuove soluzioni di data mining, potrebbe risultare utile chiamare le stored procedure di sistema utilizzate internamente dal motore di data mining. È possibile visualizzare i nomi di queste stored procedure di sistema mediante [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] per creare una traccia nel server [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e quindi creare, esplorare ed eseguire query sui modelli di data mining. [!INCLUDE[msCoName](../../includes/msconame-md.md)] non garantisce tuttavia la compatibilità delle stored procedure di sistema tra le versioni ed è pertanto consigliabile non usare mai chiamate alle stored procedure di sistema in un sistema di produzione. Per garantire la compatibilità, è invece consigliabile creare query mediante DMX o XML/A.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
-   [SystemGetCrossValidationResults &#40;Analysis Services - Data mining&#41;](../../analysis-services/data-mining/systemgetcrossvalidationresults-analysis-services-data-mining.md)  
  
-   [SystemGetClusterCrossValidationResults & #40; Analysis Services - Data Mining & #41;](../../analysis-services/data-mining/systemgetclustercrossvalidationresults-analysis-services-data-mining.md)  
  
-   [SystemGetAccuracyResults &#40;Analysis Services - Data mining&#41;](../../analysis-services/data-mining/systemgetaccuracyresults-analysis-services-data-mining.md)  
  
-   [SystemGetClusterAccuracyResults & #40; Analysis Services - Data Mining & #41;](../../analysis-services/data-mining/systemgetclusteraccuracyresults-analysis-services-data-mining.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Convalida incrociata &#40;Analysis Services - Data mining&#41;](../../analysis-services/data-mining/cross-validation-analysis-services-data-mining.md)   
 [Scheda convalida incrociata &#40;visualizzazione Grafico accuratezza modello di Data Mining&#41;](http://msdn.microsoft.com/library/bd215a68-1ad7-4046-9c44-ec8e2be13a64)   
 [Chiamata di una stored procedure](../../relational-databases/native-client-odbc-stored-procedures/calling-a-stored-procedure.md)  
  
  
