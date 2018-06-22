---
title: "Lesson 9: Build and Run the Application (Lezione 9: Compilare ed eseguire l'applicazione) | Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f52d3f3a-0b09-4b34-9112-0b3655271587
caps.latest.revision: 8
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: fdb619e98fe28742ac6b96acc6419513addfae25
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063542"
---
# <a name="lesson-9-build-and-run-the-application"></a>Lesson 9: Build and Run the Application
  Dopo aver creato un filtro di dati per la tabella di dati, il passaggio successivo consiste nel compilare ed eseguire l'applicazione del sito Web.  
  
### <a name="to-build-and-run-the-application"></a>Per compilare ed eseguire l'applicazione  
  
1.  Premere **CTRL+F5** per eseguire la pagina Default.aspx senza eseguire il debug oppure F5 per eseguirla con il debug.  
  
     Durante il processo di compilazione, il report viene compilato e tutti gli errori rilevati, ad esempio un errore di sintassi in un'espressione utilizzata nel report, vengono aggiunti nell' **Elenco attività** nella parte inferiore della finestra di Visual Studio.  
  
     La pagina Web viene visualizzata nel browser. Nel controllo ReportViewer viene visualizzato il report. È possibile utilizzare la barra degli strumenti per esplorare, ingrandire ed esportare il report in Excel.  
  
2.  Posizionare il mouse su una qualsiasi delle righe nella colonna **Nome** . Il cursore del mouse viene visualizzato a forma di mano.  
  
3.  Fare clic su un valore nella colonna **Nome** . Il report figlio viene visualizzato con dati filtrati corrispondenti.  
  
4.  Nella barra degli strumenti **ReportViewer**fare clic sull'icona **Torna al report padre** per passare al report **Padre** .  
  
     ![SSRS il drill-through utilizzando ReportViewer](../../2014/tutorials/media/ssrs-drillthrough-report.png "ssrs il drill-through utilizzando ReportViewer")  
  
5.  Chiudere il browser per uscire.  
  
  