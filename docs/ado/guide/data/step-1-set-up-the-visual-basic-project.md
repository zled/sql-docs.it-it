---
title: 'Passaggio 1: Configurare il progetto di Visual Basic | Documenti Microsoft'
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77d3bfa5-fc9f-4a72-93b4-790c7d227988
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a7b27969d78328118f98911c68eb555357bc3118
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

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
 [Passaggio 2: Inizializzare la casella di riepilogo principale](../../../ado/guide/data/step-2-initialize-the-main-list-box.md)
