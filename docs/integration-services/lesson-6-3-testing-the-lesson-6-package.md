---
title: 'Passaggio 3: Test del pacchetto della lezione 6 | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: tutorial
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: c184c92d-948f-4037-a502-5fabd909c84c
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b2a820947d24a0bad100817274408de973783e31
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="lesson-6-3---testing-the-lesson-6-package"></a>Lezione 6-3 - Test del pacchetto della lezione 6
In fase di esecuzione, il pacchetto ottiene il valore della proprietà Directory dal parametro VarFolderName.  
  
Per verificare che il pacchetto esegua l'aggiornamento della proprietà Directory con il nuovo valore in fase di esecuzione, eseguire semplicemente il pacchetto. Poiché solo tre file di dati di esempio sono stati copiati nella nuova directory, il flusso di dati verrà eseguito solo tre volte anziché essere reiterato nei 14 file della cartella originale.  
  
## <a name="checking-the-package-layout"></a>Verifica del layout del pacchetto  
Prima di testare il pacchetto è consigliabile verificare che il flusso di controllo e il flusso di dati nel pacchetto della lezione 6 contengano gli oggetti visualizzati nelle figure seguenti. Il flusso di controllo deve essere identico a quello nella lezione 5. Il flusso di dati deve essere identico a quello nella lezione 5.  
  
**Flusso di controllo**  
  
![Flusso di controllo](../integration-services/media/task3lesson6control.jpg "Flusso di controllo")  
  
**Flusso di dati**  
  
![Flusso di dati](../integration-services/media/task3lesson6data.jpg "Flusso di dati")  
  
### <a name="to-test-the-lesson-6-tutorial-package"></a>Per testare il pacchetto creato nella lezione 6 dell'esercitazione  
  
1.  Scegliere Avvia debug dal menu Debug.  
  
2.  Al termine dell'esecuzione del pacchetto, scegliere Arresta debug dal menu Debug.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Passaggio 4: Distribuzione del pacchetto della lezione 6](../integration-services/lesson-6-4-deploying-the-lesson-6-package.md)  
  
  
  
