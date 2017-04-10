---
title: "Risolvere i problemi relativi all&#39;installazione di PowerPivot per SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 97bc2ce7-af04-4372-ad79-c96b8c3417ab
caps.latest.revision: 10
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 10
---
# Risolvere i problemi relativi all&#39;installazione di PowerPivot per SharePoint
  Se vengono generati errori anziché le pagine e le caratteristiche previste, effettuare le operazioni riportate di seguito.  
  
-   Esaminare le note sulla versione di SharePoint e di [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] per ottenere soluzioni alternative a problemi di installazione noti. Le note sulla versione vengono fornite con il supporto di installazione oppure sono disponibili nel sito Microsoft da cui si scarica il software.  
  
    -   [Note sulla versione di SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)  
  
-   Vedere l'argomento del Wiki di TechNet dedicato alla [risoluzione dei problemi relativi alle installazioni di PowerPivot (e altri componenti aggiuntivi)](http://social.technet.microsoft.com/wiki/contents/articles/13737.troubleshooting-installations-of-powerpivot-and-other-add-ins.aspx).  
  
## Problemi  
  
### Le immagini di anteprima per Raccolta PowerPivot sono visualizzate come una X rossa  
 Una delle cause possibile potrebbe essere che **[!INCLUDE[ssGemini](../includes/ssgemini-md.md)] per le raccolte siti** non è attiva. Completare la procedura seguente:  
  
1.  Nella libreria della Raccolta [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] fare clic su **Impostazioni sito** dall'icona dell'ingranaggio ![Impostazioni di SharePoint](../analysis-services/media/as-sharepoint2013-settings-gear.png "Impostazioni di SharePoint") o dall'elenco **Home**.  
  
2.  Nella sezione **Amministrazione raccolta siti** fare clic su **Funzionalità raccolta siti**.  
  
3.  Fare clic su **Funzionalità raccolta siti**.  
  
4.  Verificare che **[!INCLUDE[ssGemini](../includes/ssgemini-md.md)] per le raccolte siti** sia **Attiva**.  
  
 Per altre cause di questo problema, vedere [PowerPivot Gallery shows Red X's for Icons](http://support.microsoft.com/kb/2361559) (Icone visualizzate come X rosse in Raccolta PowerPivot) (http://support.microsoft.com/kb/2361559).  
  
  