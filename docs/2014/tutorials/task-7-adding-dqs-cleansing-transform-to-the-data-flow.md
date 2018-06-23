---
title: 'Attività 7: Aggiunta della trasformazione DQS Cleansing al flusso di dati | Documenti Microsoft'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0b749c71-dfb6-493a-804f-600290d46eef
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 10b0fb12ace5a113bbde03cecf803a37b49b1974
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36170253"
---
# <a name="task-7-adding-dqs-cleansing-transform-to-the-data-flow"></a>Attività 7: Aggiunta della trasformazione DQS Cleansing al flusso di dati
  In questa attività viene aggiunta una trasformazione DQS Cleansing al flusso di dati per pulire i dati di input del fornitore tramite DQS. Vedere **[trasformazione DQS Cleansing](http://msdn.microsoft.com/library/ee677619.aspx)** per ulteriori informazioni sulla trasformazione.  
  
1.  Fare doppio clic su **DQS Cleansing** nel **del flusso di dati** scheda e fare clic su **rinominare**. Tipo di **Pulisci dati fornitore**, quindi premere **invio**.  
  
2.  Selezionare **Leggi dati fornitore dal File di Excel**; trascinare il collegamento blu per **Pulisci dati fornitore**. I componenti sono ora collegati.  
  
     ![Leggi dati fornitore -> Pulisci dati fornitore](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-01.jpg "Leggi dati fornitore -> Pulisci dati fornitore")  
  
3.  Fare doppio clic su **Pulisci dati fornitore**.  
  
4.  Nel **Editor trasformazione DQS Cleansing**, fare clic su **New** accanto al **elenco a discesa gestione connessione Data Quality**.  
  
5.  Nel **gestione connessione DQS Cleansing** della finestra di dialogo tipo **(local)** oppure **periodo** (.) per connettersi al server locale. In questa lezione si presuppone che in un server locale sia installato DQS.  
  
6.  Fare clic su **Test connessione** per testare la connessione al server DQS.  
  
7.  Scegliere **OK** per chiudere la finestra di dialogo.  
  
8.  Selezionare **Suppliers** per il **Data Quality Knowledge Base**.  
  
     ![Editor trasformazione - KB fornitori DQS Cleansing](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-02.jpg "Editor trasformazione - KB fornitori DQS Cleansing")  
  
9. Passare il **Mapping** scheda nella parte superiore.  
  
10. Dal **colonne di Input disponibili**, selezionare **Supplier Name**, **ContactEmailAddress**, **Address Line**, **Città**, **Stato**, **paese**, e **CAP** selezionando le caselle di controllo.  
  
     ![Editor trasformazione - mapping DQS Cleansing](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-03.jpg "Editor trasformazione - mapping DQS Cleansing")  
  
11. Nel riquadro inferiore, eseguire il mapping di queste colonne mediante gli elenchi di elenco a discesa nel **dominio** colonna:  
  
    |colonna|Dominio|  
    |------------|------------|  
    |Supplier Name|Supplier Name|  
    |ContactEmailAddress|Contact Email|  
    |Riga indirizzo|Riga indirizzo|  
    |Città|Città|  
    |State|State|  
    |Country|Country|  
    |Zip Code|CAP|  
  
12. Fare clic su **OK** per chiudere la **Editor trasformazione DQS Cleansing** finestra di dialogo.  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 8: Aggiunta della trasformazione Suddivisione condizionale per l'Output di pulizia della suddivisione](../../2014/tutorials/task-8-adding-conditional-split-transform-to-split-cleansing-output.md)  
  
  