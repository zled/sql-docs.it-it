---
title: Creare un report drill-through (RDLC) con parametri usando ReportViewer | Microsoft Docs
ms.custom: ''
ms.date: 05/18/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: reporting-services
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: 628c8775-c62d-45ac-b349-23db86fa4e6c
caps.latest.revision: 8
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 2efa6c156e1fff67e83c19c53c2c64c834329bd2
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2018
ms.locfileid: "40405459"
---
# <a name="create-drillthrough-rdlc-report-with-parameters---reportviewer"></a>Creare un report drill-through (RDLC) con parametri usando ReportViewer
Un report [drill-through](http://technet.microsoft.com/library/ff519554.aspx) è un report aperto da un utente facendo clic su un collegamento in un altro report. Nei report drill-through sono solitamente disponibili dettagli relativi a un elemento contenuto in un report di riepilogo originale. In questa esercitazione verranno illustrate le seguenti lezioni sulla creazione di un report drill-through con parametri e una query, in [report in modalità locale](report-server-sharepoint/local-mode-vs-connected-mode-reports-in-the-report-viewer.md).  
  
## <a name="requirements"></a>Requisiti  
Per usare questa procedura dettagliata, è necessario poter accedere al database di esempio **AdventureWorks2014** . Per altre informazioni su come ottenere il database di esempio **AdventureWorks2014**, vedere [Database di esempio AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases).  
  
Questa procedura dettagliata presuppone che l'utente abbia familiarità con le query Transaction-SQL e gli oggetti [DataSet](https://msdn.microsoft.com/library/system.data.dataset.aspx) e [DataTable](http://msdn.microsoft.com/library/system.data.datatable.aspx) di ADO.NET.  
  
Usare Visual Studio 2015 e l'applicazione Web ASP.NET per creare una pagina Web ASP.NET con un controllo ReportViewer. Il controllo è configurato per visualizzare un report che viene creato. Per questa procedura dettagliata viene creata l'applicazione in Microsoft Visual C#.  
  
## <a name="tasks"></a>Attività  
[Lezione 1: Creare un nuovo sito Web](../reporting-services/lesson-1-create-a-new-web-site.md)  
[Lezione 2: Definire una connessione dati e una tabella dati per il report padre](../reporting-services/lesson-2-define-a-data-connection-and-data-table-for-parent-report.md)  
[Lezione 3: Progettare il report padre tramite la Creazione guidata report](../reporting-services/lesson-3-design-the-parent-report-using-the-report-wizard.md)  
[Lezione 4: Definire una connessione dati e una tabella dati per il report figlio](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md)  
[Lezione 5: Progettare il report figlio tramite la Creazione guidata report](../reporting-services/lesson-5-design-the-child-report-using-the-report-wizard.md)  
[Lezione 6: Aggiungere un controllo ReportViewer all'applicazione](../reporting-services/lesson-6-add-a-reportviewer-control-to-the-application.md)  
[Lezione 7: Aggiungere un'azione drill-through in un report padre](../reporting-services/lesson-7-add-drillthrough-action-on-parent-report.md)  
[Lezione 8: Creare un filtro di dati](../reporting-services/lesson-8-create-a-data-filter.md)  
[Lesson 9: Build and Run the Application](../reporting-services/lesson-9-build-and-run-the-application.md)  
  
## <a name="see-also"></a>Vedere anche  
[Esercitazioni su Reporting Services &#40;SSRS&#41;](../reporting-services/reporting-services-tutorials-ssrs.md)  
[Progettare report con Progettazione report &#40;SSRS&#41;](../reporting-services/tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  

