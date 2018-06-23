---
title: Risoluzione dei problemi relativi a PowerPivot for SharePoint Installation | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 97bc2ce7-af04-4372-ad79-c96b8c3417ab
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: b4881ce3be8ede7d97dc2b71fb464b94b8677ca0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069969"
---
# <a name="troubleshoot-a-powerpivot-for-sharepoint-installation"></a>Risoluzione dei problemi di un'installazione di PowerPivot per SharePoint
  Se vengono generati errori anziché le pagine e le caratteristiche previste, effettuare le operazioni riportate di seguito.  
  
-   Esaminare le note sulla versione di SharePoint e di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] per ottenere soluzioni alternative a problemi di installazione noti. Le note sulla versione vengono fornite con il supporto di installazione oppure sono disponibili nel sito Microsoft da cui si scarica il software.  
  
    -   [Note sulla versione di SQL Server 2014](http://technet.microsoft.com/library/dn169381\(v=sql.15\).aspx).  
  
-   Vedere l'argomento di Wiki di TechNet relativo alla [risoluzione dei problemi nelle installazioni di PowerPivot (e altri componenti aggiuntivi)](http://social.technet.microsoft.com/wiki/contents/articles/13737.troubleshooting-installations-of-powerpivot-and-other-add-ins.aspx).  
  
## <a name="issues"></a>Problemi  
  
### <a name="powerpivot-gallery-thumbnail-images-show-as-a-red-x"></a>Le immagini di anteprima per Raccolta PowerPivot sono visualizzate come una X rossa.  
 Una delle cause possibile potrebbe essere che **Integrazione della funzionalità di PowerPivot per le raccolte siti** non è attiva. Completare la procedura seguente:  
  
1.  Nella libreria della raccolta PowerPivot, fare clic su **Impostazioni sito** dall'icona dell'ingranaggio ![le impostazioni di SharePoint](../../../2014/analysis-services/media/as-sharepoint2013-settings-gear.gif "impostazioni di SharePoint") o **Home** elenco.  
  
2.  Nella sezione **Amministrazione raccolta siti** fare clic su **Funzionalità raccolta siti**.  
  
3.  Fare clic su **Funzionalità raccolta siti**.  
  
4.  Verificare che **Integrazione delle funzionalità di PowerPivot per le raccolte siti** sia **Attiva**.  
  
 Per altre cause di questo problema, vedere [raccolta PowerPivot Mostra x rossa per le icone](http://support.microsoft.com/kb/2361559) (http://support.microsoft.com/kb/2361559).  
  
  