---
title: 'Lesson 3: Design the Parent Report using the Report Wizard (Lezione 3: Progettare il report padre tramite la Creazione guidata report) | Microsoft Docs'
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
ms.assetid: 2f69dcd3-cd6d-45a9-a62a-ba6f5f3179d8
caps.latest.revision: "9"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 4de8072efe47f62d59f13f7a1e4ed936ee7d1887
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="lesson-3-design-the-parent-report-using-the-report-wizard"></a>Lezione 3: Progettare il report padre tramite la Creazione guidata report
Dopo aver creato una connessione dati e una tabella di dati per il report padre, il passaggio successivo consiste nel progettare il report padre utilizzando la Creazione guidata report in Progettazione report. Per altre informazioni sulla progettazione dei report, vedere [Progettare report con Progettazione report &#40;SSRS&#41;](../reporting-services/tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md).  
  
### <a name="to-design-the-parent-report-using-the-report-wizard"></a>Per progettare il report padre tramite la Creazione guidata report  
  
1.  Verificare che in **Esplora soluzioni**sia selezionato il sito Web principale.  
  
2.  Fare clic con il pulsante destro del mouse sul sito Web e selezionare **Add New Item**(Aggiungi nuovo elemento).  
  
3.  Nella finestra di dialogo **Add New Item** (Aggiungi nuovo elemento) selezionare **Creazione guidata report**, immettere un nome per il file di report e scegliere **Aggiungi**.  
  
    Verrà avviata la Creazione guidata report.  
  
4.  Nella pagina **Proprietà set di dati** , nella casella **Origine dati** selezionare il set di dati **DataSet1** creato nella [Lezione 2: definire una connessione dati e una tabella di dati per il report padre](../reporting-services/lesson-2-define-a-data-connection-and-data-table-for-parent-report.md).  
  
    La casella **Available datasets** (Set di dati disponibili) viene aggiornata automaticamente con l'oggetto **DataTable** creato in precedenza.  
  
5.  Fare clic su **Avanti**.  
  
6.  Nella pagina **Disponi campi** eseguire le operazioni seguenti:  
  
    1.  Trascinare **ProductID**, **Name**, **ProductNumber**, **SafetyStockLevel**, e **ReorderLevel** da **Campi disponibili** alla casella **Valori** .  
  
    2.  Fare clic sulla freccia accanto a **Sum(ProductID)**, **Sum(SafetyStockLevel)**, **Sum(ReorderLevel)** e deselezionare **Sum** .  
  
7.  Fare clic due volte su **Avanti** e selezionare **Fine** per chiudere la **Creazione guidata report**.  
  
    È stato creato il file con estensione rdlc. Il file viene aperto in Progettazione report. La Tablix che è stata progettata è ora visualizzata nell'area di progettazione.  
  
8.  Salvare il file con estensione rdlc.  
  
## <a name="next-task"></a>Attività successiva  
È stato progettato correttamente il report padre tramite la Creazione guidata report. Successivamente, verranno create una connessione dati e una tabella di dati per il report figlio. Vedere [Lezione 4: Definire una connessione dati e una tabella di dati per il report figlio](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md).  
  
  
  

