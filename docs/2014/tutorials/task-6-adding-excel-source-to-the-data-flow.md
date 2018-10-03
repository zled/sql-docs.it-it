---
title: "Attività 6: Aggiunta dell'origine Excel al flusso di dati | Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: 0209055e-cb6b-4a07-909e-836596727a2c
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f51d2f6f48263e764d73eb9fcd8ee0dcd27b26da
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48071761"
---
# <a name="task-6-adding-excel-source-to-the-data-flow"></a>Attività 6: Aggiunta dell'origine Excel al flusso di dati
  In questa attività viene aggiunta un'origine Excel al flusso di dati per leggere i dati del fornitore dal file di Excel di origine. Tramite l'origine Excel vengono estratti dati da fogli di lavoro o intervalli in cartelle di lavoro di Microsoft Excel. Visualizzare [origine Excel](../integration-services/data-flow/excel-source.md) per altre informazioni.  
  
1.  Trascinare **origine Excel** dal **altre origini** nelle **casella degli strumenti SSIS** per il **del flusso di dati** scheda.  
  
2.  Fare clic su **origine Excel** nel **flusso di dati** scheda, quindi scegliere **rinominare**.  
  
3.  Tipo di **Leggi dati fornitore dal File di Excel** , quindi premere **invio**.  
  
4.  Fare doppio clic su **Leggi dati fornitore dal File di Excel** per avviare la **Editor origine Excel** nella finestra di dialogo.  
  
5.  Nel **Editor origine Excel** finestra di dialogo, fare clic su **New** per creare una connessione di Excel.  
  
6.  Nel **gestione connessione Excel** della finestra di dialogo fare clic su **Sfoglia**e quindi selezionare il **Suppliers. xls** del file nei **esercitazione su EIM** cartella . Verificare che **Microsoft Excel 97-2003** sia selezionato nel **versione di Excel** casella e quindi fare clic su **OK**.  
  
     ![Finestra di dialogo Gestione connessione Excel](../../2014/tutorials/media/et-addingexcelsourcetothedataflow-01.jpg "nella finestra di dialogo Gestione connessione Excel")  
  
7.  Nel **Editor origine Excel** finestra di dialogo **IncomingSuppliers$** nel **nome del foglio di Excel** casella di riepilogo.  
  
     ![Nome del foglio di Excel - fornitori$ in entrata](../../2014/tutorials/media/et-addingexcelsourcetothedataflow-02.jpg "nome del foglio di Excel - fornitori$ in entrata")  
  
8.  Fare clic su **Preview** in anteprima i dati in file di Excel.  
  
9. Scegliere **OK** per chiudere la finestra di dialogo.  
  
10. Trascinare **DQS Cleansing** trasforma nello **altre trasformazioni** sul **casella degli strumenti SSIS** per il **del flusso di dati** disponibile nella scheda  **Leggere i dati fornitore dal File di Excel**. Nella trasformazione DQS Cleansing viene utilizzato Data Quality Services (DQS) per correggere i dati applicando le regole approvate nella Knowledge Base. In fase di esecuzione, tramite questa trasformazione viene creato un progetto DQS Cleansing nel server DQS. Visualizzare [trasformazione DQS Cleansing](http://msdn.microsoft.com/library/ee677619.aspx) per altre informazioni.  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 7: Aggiunta della trasformazione DQS Cleansing al flusso di dati](../integration-services/data-flow/data-flow.md)  
  
  
