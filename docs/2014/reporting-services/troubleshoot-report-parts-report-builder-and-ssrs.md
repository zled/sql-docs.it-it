---
title: Risoluzione dei problemi relativi a parti del Report (Generatore Report e SSRS) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d9fe1932-46e7-421b-a8a9-4c54d9576e94
caps.latest.revision: 6
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: d3f8e675ff62ec000b3b9dd3c7c692c63f7fc8b1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065304"
---
# <a name="troubleshoot-report-parts-report-builder-and-ssrs"></a>Risoluzione dei problemi relativi alle parti del report (Generatore report e SSRS)
  Questi suggerimenti possono risultare utili durante l'utilizzo di parti del report.  
  
## <a name="why-do-my-co-worker-and-i-see-different-instances-of-the-same-report-part-when-we-search-for-it"></a>Visualizzazione di istanze diverse della stessa parte del report tra colleghi di lavoro durante la relativa ricerca  
 In un server di report o in un sito di SharePoint integrato con un server di report possono essere presenti più istanze di una sola parte di report, tutte dotate dello stesso identificatore univoco globale (GUID). Nell'elenco di risultati ricerca viene visualizzata solo l'istanza più recente. In alcuni casi, istanze diverse di una singola parte di report possono avere autorizzazioni differenti. Se un collega di lavoro dispone di autorizzazioni sul server diverse da un altro collega, quest'ultimo non visualizzerà la stessa istanza. Si supponga, ad esempio, che più copie di una parte di report, tutte con lo stesso GUID, vengano salvate in cartelle diverse su un server di report in modalità integrata SharePoint. Se le cartelle dispongono di autorizzazioni diverse, anche le parti di report in esse contenute disporranno di autorizzazioni diverse.  
  
 Per conoscere le autorizzazioni di cui dispongono i colleghi, chiedere all'amministratore del server di report.  
  
## <a name="when-i-search-for-report-parts-that-i-uploaded-to-a-sharepoint-server-i-do-not-see-them-why-not"></a>Impossibilità di visualizzare parti di report caricate in un server SharePoint in seguito alla relativa ricerca  
 È possibile che le parti di report caricate manualmente in una raccolta documenti di SharePoint, anziché pubblicate tramite Generatore report, non vengano visualizzate nella relativa raccolta. Potrebbe essere necessario sincronizzare il server di report utilizzato per la ricerca nella raccolta con il contenuto della raccolta documenti di SharePoint. Per altre informazioni, vedere [attivare la funzionalità sincronizzazione File Server di Report in Amministrazione centrale SharePoint](../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md) in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [documentazione Online di](http://go.microsoft.com/fwlink/?LinkId=154888) sul sito msdn.microsoft.com.  
  
## <a name="why-cant-others-see-the-image-in-their-reports"></a>Impossibilità di visualizzare l'immagine nei report di altri utenti  
 Se si pubblica una parte di report rappresentata da un collegamento a un file di immagine, tale parte di report costituirà in effetti un semplice collegamento. Se altri utenti non riescono a visualizzare l'immagine quando aggiungono la parte di report immagine nei relativi report, potrebbero non disporre delle autorizzazioni per l'immagine a cui ci si sta collegando.  
  
 Esistono diverse soluzioni possibili:  
  
-   Creare una parte di report con il file di immagine, anziché con il collegamento al file di immagine.  
  
-   Spostare il file di immagine in un percorso per il quale gli altri utenti dispongono delle autorizzazioni.  
  
-   Chiedere all'amministratore del server di report di modificare le autorizzazioni.  
  
## <a name="why-do-i-get-a-circular-reference-error-message-when-i-try-to-publish-my-report-part"></a>Visualizzazione di un messaggio di errore relativo a un "riferimento circolare" durante il tentativo di pubblicazione della parte di report  
 Se gli elementi del report presentano un riferimento circolare, non sarà possibile pubblicarli come parti di report. Un elemento del report punta, ad esempio, a un set di dati che a sua volta punta a un parametro. Il parametro, infine, punta nuovamente al set di dati. Sarà necessario anzitutto eliminare uno dei riferimenti prima di poter pubblicare la parte di report.  
  
## <a name="see-also"></a>Vedere anche  
 [Parti di report &#40;SSRS e Generatore Report&#41;](report-parts-report-builder-and-ssrs.md)  
  
  