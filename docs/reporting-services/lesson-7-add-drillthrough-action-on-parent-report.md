---
title: "Lesson 7: Add Drillthrough Action on Parent Report (Lezione 7: Aggiungere un'azione drill-through in un report padre) | Microsoft Docs"
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
ms.assetid: aad2da1a-d7b1-4afa-a66a-1ff102e8306f
caps.latest.revision: 13
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: afb72e601ef9715cf0951cbff46c1033aa1c1854
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33015288"
---
# <a name="lesson-7-add-drillthrough-action-on-parent-report"></a>Lezione 7: Aggiungere un'azione drill-through in un report padre
Dopo aver aggiunto un controllo ReportViewer all'applicazione del sito Web, il passaggio successivo consiste nell'aggiunta di un'azione drill-through nel report padre.  
  
### <a name="to-add-drillthrough-action-on-the-parent-report"></a>Per aggiungere un'azione drill-through nel report padre  
  
1.  Andare al report padre.  
  
2.  Selezionare la casella di testo contenente il valore **Nome**.  
  
3.  Fare clic con il pulsante destro del mouse sulla casella di testo, quindi selezionare **Proprietà casella di testo**.  
  
4.  Andare alla scheda **Azione** e selezionare l'opzione **Vai al report** .  
  
5.  Immettere il nome del report figlio nella sezione **Specifica un report** .  
  
    > [!NOTE]
    > Non includere l'estensione del file per il nome del report.  
  
6.  Fare clic su **Aggiungi** nella sezione **Utilizza i parametri seguenti per eseguire il report** .  
  
7.  Digitare **productid** nella casella **nome** , quindi scegliere **ProductID** nell'elenco a discesa **Valore** .  
  
8.  Al termine, fare clic su **OK** .  
  
## <a name="next-task"></a>Attività successiva  
È stata aggiunta correttamente un'azione drill-through nel report padre. Successivamente, verrà creato un filtro di dati per la tabella di dati definita per il report figlio. Vedere [Lezione 8: Creare un filtro di dati](../reporting-services/lesson-8-create-a-data-filter.md).  
  
  
  

