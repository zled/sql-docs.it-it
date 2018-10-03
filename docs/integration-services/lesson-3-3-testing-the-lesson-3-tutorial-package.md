---
title: "Passaggio 3: Test del pacchetto creato nella lezione 3 dell'esercitazione | Microsoft Docs"
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 1096a476-93cf-4474-86f5-27d6357eb380
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8bad683dc5ad0b49ac464ab3efcb90a652d45aa9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47760819"
---
# <a name="lesson-3-3---testing-the-lesson-3-tutorial-package"></a>Lezione 3-3 - Test del pacchetto creato nella lezione 3 dell'esercitazione
In questa attività verrà eseguito il pacchetto Lesson 3.dtsx. Durante l'esecuzione del pacchetto, nella finestra Registra eventi verranno elencate le voci di log scritte nel file di log. Al termine dell'esecuzione del pacchetto sarà possibile verificare il contenuto del file di log generato dal provider di log.  
  
## <a name="checking-the-package-layout"></a>Verifica del layout del pacchetto  
Prima di testare il pacchetto è consigliabile verificare che il flusso di controllo e il flusso di dati nel pacchetto della lezione 3 contengano gli oggetti visualizzati nelle figure seguenti. Il flusso di controllo deve essere identico a quello nella lezione 2. Il flusso di dati deve essere identico a quello nelle lezioni 1 e 2.  
  
**Flusso di controllo**  
  
![Flusso di controllo nel pacchetto](../integration-services/media/task4lesson2control.gif "Flusso di controllo nel pacchetto")  
  
**Flusso di dati**  
  
![Flusso di dati nel pacchetto](../integration-services/media/task9lesson1data.gif "Flusso di dati nel pacchetto")  
  
### <a name="to-run-the-lesson-4-tutorial-package"></a>Per eseguire il pacchetto creato nella lezione 4 dell'esercitazione  
  
1.  Scegliere Registra eventi dal menu SSIS.  
  
2.  Scegliere **Avvia debug** dal menu **Debug**.  
  
3.  Al termine dell'esecuzione del pacchetto, scegliere **Arresta debug** dal menu **Debug**.  
  
### <a name="to-examine-the-generated-log-file"></a>Per esaminare il file di log generato  
  
-   Aprire il file TutorialLog.log in Blocco note o in un altro editor di testo.  
  
-   Sebbene la semantica delle informazioni generate per gli eventi **PipelineExecutionPlan** e **PipelineExecutionTrees** esuli dall'ambito di questa esercitazione, si può notare che nella prima riga sono elencati i campi di informazione specificati nella scheda **Dettagli** della finestra di dialogo **Configura log SSIS** . È inoltre possibile verificare che i due eventi selezionati, PipelineExecutionPlan e PipelineExecutionTrees, sono stati inseriti nel log per ogni iterazione del ciclo Foreach.  
  
## <a name="next-lesson"></a>Lezione successiva  
[Lezione 4: Aggiungere il reindirizzamento del flusso errato tramite SSIS](../integration-services/lesson-4-add-error-flow-redirection-with-ssis.md)  
  
  
  
