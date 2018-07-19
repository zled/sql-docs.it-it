---
title: "Lesson 6: Add a ReportViewer Control to the Application (Lezione 6: Aggiungere un controllo ReportViewer all'applicazione) | Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f9492a97-5609-4059-ae76-0fba111d4968
caps.latest.revision: 7
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: c5fa2bc40982450ac67b82d39db8ee1f6a129604
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37323741"
---
# <a name="lesson-6-add-a-reportviewer-control-to-the-application"></a>Lezione 6: Aggiungere un controllo ReportViewer all'applicazione
  Dopo aver progettato il report figlio tramite la Creazione guidata report, il passaggio successivo consiste nell'aggiungere un controllo ReportViewer all'applicazione del sito Web.  
  
### <a name="to-add-a-reportviewer-control-to-the-application"></a>Per aggiungere un controllo ReportViewer all'applicazione  
  
1.  In **Esplora soluzioni**fare clic con il pulsante destro del mouse su **Default.aspx**, quindi scegliere **Progettazione viste**.  
  
2.  Dal gruppo **Estensioni AJAX** nella finestra della **casella degli strumenti** trascinare un controllo **ScriptManager** nell'area di progettazione.  
  
3.  Dal gruppo **Report** trascinare un controllo **ReportViewer** nell'area di progettazione sotto il controllo **ScriptManager** .  
  
4.  Aprire la finestra **Attività di ReportViewer** facendo clic sulla freccia nell'angolo superiore destro del controllo **ReportViewer** .  
  
5.  Nella casella **Scegli report** selezionare il report padre creato.  
  
     Quando si seleziona un report, le istanze delle origini dati utilizzate nel report vengono create automaticamente. Il codice viene generato per la creazione di un'istanza di ogni oggetto DataTable e del relativo contenitore [DataSet](http://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx) . Un controllo [ObjectDataSource](http://msdn.microsoft.com/library/system.web.ui.webcontrols.objectdatasource\(v=vs.100\).aspx) viene aggiunto all'area di progettazione, corrispondente a ogni origine dati utilizzata nel report. Questo controllo dell'origine dati viene configurato automaticamente.  
  
     Se si utilizza Microsoft Visual Studio 2012, verificare che il controllo ObjectDataSource sia associato a DataSet1, completo dello spazio dei nomi di progetto, se il nome completo è indicato nell'elenco a discesa **Seleziona oggetto business** , ad esempio Projectnamespace.DataSet1TableAdapters.ProductTableAdapter. Accedere alla casella di riepilogo facendo clic con il pulsante destro del mouse su ObjectDataSource e scegliendo **Configura origine dati**.  
  
6.  Scegliere Compila sito Web dal menu Compila.  
  
     Il report viene compilato e tutti gli errori, ad esempio un errore di sintassi in un'espressione del report, vengono visualizzati nell'area **Elenco errori** . Fare clic su **Elenco errori** nella parte inferiore della finestra di Visual Studio per visualizzare l'area **Elenco errori** .  
  
## <a name="next-task"></a>Attività successiva  
 È stato aggiunto correttamente un controllo ReportViewer all'applicazione del sito Web. Successivamente, si aggiungerà un'azione drill-through nel report padre.  
  
  
