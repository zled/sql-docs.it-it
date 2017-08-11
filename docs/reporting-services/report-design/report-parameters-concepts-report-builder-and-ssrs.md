---
title: Concetti relativi alla parametri (Generatore Report e SSRS) report | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0aa2159-4e49-4713-8824-5ef9a9edbc62
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: cb4044deed8935af354e1c6f15ace89f0b3e5010
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="report-parameters-concepts-report-builder-and-ssrs"></a>Concetti relativi ai parametri di report (Generatore report e SSRS)
  È possibile aggiungere parametri a un report per collegare report correlati, controllare l'aspetto del report, filtrare i dati del report o per limitare l'ambito di un report a percorsi o utenti specifici.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 I parametri di report vengono creati nei modi seguenti:  
  
-   Automaticamente, quando si definisce la query del set di dati contenente le variabili di query. Per ogni variabile di query, vengono creati un parametro del report e un parametro di query del set di dati con lo stesso nome. Un parametro di query può essere un riferimento a una variabile do query o a un parametro di input per una stored procedure.  
  
-   Automaticamente, quando si aggiunge un riferimento a un set di dati condiviso contenente parametri di query.  
  
-   Manualmente, quando si creano parametri del report nel riquadro dei dati del report. I parametri rappresentano una delle raccolte predefinite che è possibile includere in un'espressione di un report. Poiché le espressioni sono usate per definire valori nell'intera definizione di un report, è possibile usare i parametri per controllare l'aspetto del report o per passare i valori ai sottoreport o report correlati che usano anch'essi i parametri.  
  
 Per altre informazioni, vedere [Parametri report &#40;Generatore report e Progettazione report&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md).  
  
 I parametri sono usati di frequente per filtrare i dati del report sia prima che dopo la restituzione dei dati al report. Per altre informazioni, vedere [Filtrare, raggruppare e ordinare i dati &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md).  
  
 Quando si progetta un report, i parametri corrispondenti vengono salvati nella definizione del report. Quando si pubblica un report, i parametri corrispondenti vengono salvati e gestiti separatamente della definizione del report. Una volta salvato il report nel server di report, è possibile eseguire le operazioni seguenti:  
  
-   Modificare i valori dei parametri del report direttamente nel server di report indipendentemente dalla definizione del report.  
  
-   Creare più report collegati in cui ogni report collegato è un collegamento alla definizione del report con un set di valori di parametro separato che può essere gestito indipendentemente nel server di report.  
  
 Se si intende creare snapshot, cronologie o sottoscrizioni di report in un report pubblicato, è necessario capire come i parametri del report influiscono sui requisiti di progettazione per il report.  
  
## <a name="see-also"></a>Vedere anche  
 [Report creazione concetti &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/report-authoring-concepts-report-builder-and-ssrs.md)   
 [Report di set di dati incorporati e condivisi &#40; Generatore report e SSRS &#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Esercitazione: Aggiungere un parametro di Report &#40; Generatore report &#41;](../../reporting-services/tutorial-add-a-parameter-to-your-report-report-builder.md)  
  
  
