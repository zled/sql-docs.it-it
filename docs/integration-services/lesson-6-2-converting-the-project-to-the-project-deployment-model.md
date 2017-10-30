---
title: 'Passaggio 2: Conversione del progetto nel modello di distribuzione progetto | Documenti Microsoft'
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 80964293-f1f5-4da7-b1fb-00ab8c30c1c5
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 49fac3d56083932db49125ea4660e89d9808f187
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="lesson-6-2---converting-the-project-to-the-project-deployment-model"></a>Lezione 6-2-conversione del progetto nel modello di distribuzione del progetto
In questa attività verrà usata la Conversione guidata progetto di Integration Services per convertire il progetto nel modello di distribuzione del progetto.  
  
### <a name="converting-the-project-to-the-project-deployment-model"></a>Conversione del progetto nel modello di distribuzione del progetto  
  
1.  Scegliere Converti nel modello di distribuzione del progetto dal menu Progetto.  
  
2.  Nella pagina introduttiva della Conversione guidata progetto di Integration Services verificare i passaggi e quindi fare clic su Avanti.  
  
3.  Nella pagina Seleziona pacchetti deselezionare nell'elenco Pacchetti tutte le caselle di controllo, ad eccezione di Lesson 6.dtsx, quindi fare clic su Avanti.  
  
4.  Nella pagina Specifica proprietà del progetto fare clic su Avanti.  
  
5.  Nella pagina Aggiorna attività Esegui pacchetto fare clic su Avanti.  
  
6.  Nella pagina Seleziona configurazioni assicurarsi che sia selezionato il pacchetto Lesson 6.dtsx nell'elenco Configurazioni e quindi fare clic su Avanti.  
  
7.  Nella pagina Crea parametri assicurarsi che sia selezionato il pacchetto Lesson 6.dtsx e che Ambito sia impostato su Pacchetto nell'elenco Proprietà di configurazione, quindi fare clic su Avanti.  
  
8.  Nella pagina Configura parametri verificare che i valori per Nome e Valore corrispondano al nome e al valore specificato nella lezione 5 per i valori relativi a variabile e configurazione, quindi fare clic su Avanti.  
  
9. Nel riquadro Riepilogo della pagina Verifica si noti che la procedura guidata ha usato le informazioni disponibili nel file di configurazione per impostare le proprietà da convertire.  
  
10. Fare clic su Converti.  
  
    Al termine della conversione, viene visualizzato un messaggio di avviso che indica che le modifiche verranno salvate solo dopo il salvataggio del progetto in Visual Studio. Fare clic su OK nella finestra di dialogo di avviso.  
  
11. Nella Conversione guidata progetto di Integration Services fare clic su Chiudi.  
  
12. In SQL Server Data Tools scegliere Salva dal menu File per salvare il pacchetto convertito.  
  
13. Fare clic sulla scheda Parametri e verificare che il pacchetto includa un parametro per VarFolderName e che il valore corrisponda al percorso specificato per la cartella New Sample Data del file di configurazione della lezione 5.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Passaggio 3: Test del pacchetto della lezione 6](../integration-services/lesson-6-3-testing-the-lesson-6-package.md)  
  
  
  

