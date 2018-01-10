---
title: 'Lesson 6: Add a ReportViewer Control to the Application (Lezione 6: Aggiungere un controllo ReportViewer all''applicazione) | Microsoft Docs'
ms.custom: 
ms.date: 05/18/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: reporting-services
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
ms.assetid: f9492a97-5609-4059-ae76-0fba111d4968
caps.latest.revision: "7"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0b2fbe90e3c3f1e2f109b87de4a07b884fb49d3d
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="lesson-6-add-a-reportviewer-control-to-the-application"></a>Lezione 6: Aggiungere un controllo ReportViewer all'applicazione
Dopo aver progettato il report figlio tramite la Creazione guidata report, il passaggio successivo consiste nell'aggiungere un controllo ReportViewer all'applicazione del sito Web. Se si usa il sito Web report ASP.NET, il controllo ReportViewer viene aggiunto alla pagina default.aspx.   
  
### <a name="to-add-a-reportviewer-control-to-the-application"></a>Per aggiungere un controllo ReportViewer all'applicazione  
  
1.  In **Esplora soluzioni**fare clic con il pulsante destro del mouse su **Default.aspx**e quindi scegliere **Progettazione viste**.  
  
2.  Se default.aspx include già il controllo ReportViewer, andare al **passaggio 4**. In caso contrario, dal gruppo **Estensioni AJAX** nella finestra **Casella degli strumenti** trascinare un controllo **ScriptManager** nell'area di progettazione.  
  
3.  Dal gruppo **Report** trascinare un controllo **ReportViewer** nell'area di progettazione sotto il controllo **ScriptManager** .  
  
4.  Aprire la finestra **Attività di ReportViewer** facendo clic sulla freccia nell'angolo superiore destro del controllo **ReportViewer** .  
  
5.  Nella casella **Scegli report** selezionare il report padre creato.  
  
    Quando si seleziona un report, le istanze delle origini dati utilizzate nel report vengono create automaticamente. Il codice viene generato per la creazione di un'istanza di ogni oggetto DataTable e del relativo contenitore [DataSet](http://msdn.microsoft.com/library/system.data.dataset.aspx) . Un controllo [ObjectDataSource](http://msdn.microsoft.com/library/system.web.ui.webcontrols.objectdatasource.aspx) viene aggiunto all'area di progettazione, corrispondente a ogni origine dati usata nel report. Questo controllo dell'origine dati viene configurato automaticamente.  
  
6.  Scegliere Compila sito Web dal menu Compila.  
  
    Il report viene compilato e tutti gli errori, ad esempio un errore di sintassi in un'espressione del report, vengono visualizzati nell'area **Elenco errori** . Fare clic su **Elenco errori** nella parte inferiore della finestra di Visual Studio per visualizzare l'area **Elenco errori** .  
  
## <a name="next-task"></a>Attività successiva  
È stato aggiunto correttamente un controllo ReportViewer all'applicazione del sito Web. Successivamente, si aggiungerà un'azione drill-through nel report padre. Vedere [Lezione 7: Aggiungere un'azione drill-through in un report padre](../reporting-services/lesson-7-add-drillthrough-action-on-parent-report.md).  
  

