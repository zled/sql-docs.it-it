---
title: DataSources e DataSets (Generatore Report e SSRS) | Documenti Microsoft
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
ms.assetid: f951a4aa-da55-4e43-8579-4a5d4480d11f
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: a1e556a8c6ac712d61d262c4d96993a9ab3ecf11
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="built-in-collections---datasources-and-datasets-references-report-builder"></a>Raccolte predefinite - origini dati e i riferimenti di set di dati (Generatore Report)
  La raccolta **DataSources** rappresenta tutte le origini dati usate in un report. Analogamente, la raccolta **DataSets** rappresenta tutti i set di dati per tutte le origini dati disponibili in un report. Usare il riquadro **Dati report** per ottenere una visualizzazione gerarchica dei set di dati del report organizzati sotto l'origine dati cui fanno riferimento. Se si includono riferimenti a queste raccolte, durante l'anteprima del report questi valori non verranno visualizzati. Le raccolte sono disponibili solo dopo la pubblicazione del report in un server di report.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="datasources"></a>DataSources  
 La raccolta **DataSources** rappresenta le origini dati a cui si fa riferimento nella definizione del report pubblicato. È possibile scegliere di includere queste informazioni nel report per documentare l'origine dei relativi dati, Questa raccolta non è disponibile in modalità **Anteprima** . La tabella seguente descrive le variabili della raccolta **DataSources** .  
  
|**Variabile**|**Tipo**|**Description**|  
|------------------|--------------|---------------------|  
|**DataSourceReference**|**String**|Percorso completo della definizione dell'origine dati nel server di report. Ad esempio, è possibile includere un elenco di tutte le origini dati utilizzate da un report come parte di una cronologia di report. Nell'esempio seguente è illustrato il percorso completo per l'origine dati denominata AdventureWorks2012:<br /><br /> `/DataSources/AdventureWorks2012`.|  
|**Tipo**|**String**|Tipo di provider di dati per l'origine dati. Ad esempio, `SQL`.|  
  
## <a name="datasets"></a>DataSets  
 La raccolta **DataSets** rappresenta i set di dati a cui si fa riferimento nella definizione del report. È possibile scegliere di includere la query nel report in una casella di testo, in modo che un utente interessato ai dati effettivi contenuti nel report possa vedere il testo del comando originale. Questa raccolta non è disponibile in modalità **Anteprima** . La tabella seguente descrive i membri della raccolta **DataSets** .  
  
|**Membro**|**Tipo**|**Description**|  
|----------------|--------------|---------------------|  
|**CommandText**|**String**|Per le origini dei dati database, si tratta della query utilizzata per recuperare dati dall'origine dei dati. Se la query è un'espressione, si tratta dell'espressione valutata.|  
|**RewrittenCommandText**|**String**|Valore CommandText espanso del provider di dati. Viene in genere utilizzato per i report con parametri query su cui viene eseguito il mapping a parametri report. Il provider di dati imposta questa proprietà quando espande i riferimenti ai parametri di testo di comando nei valori costanti selezionati per i parametri report su cui viene eseguito il mapping.|  
  
### <a name="using-query-expressions"></a>Utilizzo di espressioni di query  
 È possibile utilizzare le espressioni per definire la query contenuta in un set di dati. È possibile utilizzare questa funzionalità per progettare report in cui la query viene modificata in base all'input dell'utente, ai dati di altri set di dati o ad altre variabili. Per altre informazioni sulle query, vedere [Set di dati condivisi e incorporati del report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Espressioni &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)   
 [Esempi di espressioni &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)  
  
  
