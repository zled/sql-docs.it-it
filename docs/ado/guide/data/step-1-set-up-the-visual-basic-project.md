---
title: 'Passaggio 1: Configurare il progetto di Visual Basic | Documenti Microsoft'
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77d3bfa5-fc9f-4a72-93b4-790c7d227988
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 22dc4636b248be498317edccfb89f13b235ab525
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="step-1-set-up-the-visual-basic-project"></a>Passaggio 1: Configurare il progetto di Visual Basic
In questo scenario, si presuppone di disporre di Microsoft Visual Basic 6.0, ADO 2.5 o versioni successive e il Provider Microsoft OLE DB per Internet Publishing installato nel sistema. Verrà innanzitutto creato un nuovo progetto e quindi aggiungere alcuni controlli al form predefinito nel progetto.  
  
### <a name="to-create-an-ado-project"></a>Per creare un progetto ADO:  
  
1.  In Microsoft Visual Basic, creare un nuovo progetto Standard EXE.  
  
2.  Dal menu progetto, scegliere i riferimenti.  
  
3.  Selezionare "Libreria Microsoft ActiveX Data Objects 2.5" e fare clic su OK.  
  
### <a name="to-insert-controls-on-the-main-form"></a>Per inserire i controlli nel form principale:  
  
1.  Aggiungere un controllo ListBox a Form1. Impostare la proprietà Name **lstMain**.  
  
2.  Aggiungere un altro controllo ListBox a Form1. Impostare la proprietà Name **lstDetails**.  
  
3.  Aggiungere un controllo casella di testo in Form1. Impostare la proprietà Name **txtDetails**.  
  
## <a name="see-also"></a>Vedere anche  
 [Scenario di pubblicazione su Internet](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Passaggio 2: Inizializzare la casella di riepilogo Main](../../../ado/guide/data/step-2-initialize-the-main-list-box.md)
