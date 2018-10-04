---
title: 'Passaggio 3: Test del pacchetto della lezione 6 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: c184c92d-948f-4037-a502-5fabd909c84c
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9ddacdc7ede5d65132912783464250ff5f0db6bf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48122031"
---
# <a name="step-3-testing-the-lesson-6-package"></a>Passaggio 3: Test del pacchetto della lezione 6
  In fase di esecuzione, il pacchetto ottiene il valore della proprietà Directory dal parametro VarFolderName.  
  
 Per verificare che il pacchetto esegua l'aggiornamento della proprietà Directory con il nuovo valore in fase di esecuzione, eseguire semplicemente il pacchetto. Poiché solo tre file di dati di esempio sono stati copiati nella nuova directory, il flusso di dati verrà eseguito solo tre volte anziché essere reiterato nei 14 file della cartella originale.  
  
## <a name="checking-the-package-layout"></a>Verifica del layout del pacchetto  
 Prima di testare il pacchetto è consigliabile verificare che il flusso di controllo e il flusso di dati nel pacchetto della lezione 6 contengano gli oggetti visualizzati nelle figure seguenti. Il flusso di controllo deve essere identico a quello nella lezione 5. Il flusso di dati deve essere identico a quello nella lezione 5.  
  
 **Flusso di controllo**  
  
 ![Flusso di controllo](../../2014/tutorials/media/task3lesson6control.jpg "flusso di controllo")  
  
 **Flusso di dati**  
  
 ![Flusso di dati](../../2014/tutorials/media/task3lesson6data.jpg "flusso di dati")  
  
### <a name="to-test-the-lesson-6-tutorial-package"></a>Per testare il pacchetto creato nella lezione 6 dell'esercitazione  
  
1.  Scegliere Avvia debug dal menu Debug.  
  
2.  Al termine dell'esecuzione del pacchetto, scegliere Arresta debug dal menu Debug.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [Passaggio 4: Distribuzione del pacchetto della lezione 6](../integration-services/lesson-6-4-deploying-the-lesson-6-package.md)  
  
  
