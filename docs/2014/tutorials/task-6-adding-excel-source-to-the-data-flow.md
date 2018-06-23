---
title: "Attività 6: Aggiunta dell'origine Excel al flusso di dati | Documenti Microsoft"
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
ms.assetid: 0209055e-cb6b-4a07-909e-836596727a2c
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 1cde5dc49851e7d8c808d4a6273f4d4caf6603e2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36171341"
---
# <a name="task-6-adding-excel-source-to-the-data-flow"></a>Attività 6: Aggiunta dell'origine Excel al flusso di dati
  In questa attività viene aggiunta un'origine Excel al flusso di dati per leggere i dati del fornitore dal file di Excel di origine. Tramite l'origine Excel vengono estratti dati da fogli di lavoro o intervalli in cartelle di lavoro di Microsoft Excel. Vedere [origine Excel](http://msdn.microsoft.com/library/ms141683.aspx) per altre informazioni.  
  
1.  Trascinare **origine Excel** da **altre origini** in **casella degli strumenti SSIS** per il **del flusso di dati** scheda.  
  
2.  Fare clic su **origine Excel** nel **del flusso di dati** scheda e fare clic su **rinominare**.  
  
3.  Tipo di **Leggi dati fornitore dal File di Excel** e premere **invio**.  
  
4.  Fare doppio clic su **Leggi dati fornitore dal File di Excel** per avviare la **Editor origine Excel** finestra di dialogo.  
  
5.  Nel **Editor origine Excel** finestra di dialogo, fare clic su **New** per creare una connessione Excel.  
  
6.  Nel **gestione connessione Excel** finestra di dialogo, fare clic su **Sfoglia**e quindi selezionare il **Suppliers. xls** del file nel **esercitazione su EIM** cartella . Verificare che **Microsoft Excel 97-2003** sia selezionato nel **Excel versione** casella e quindi fare clic su **OK**.  
  
     ![Finestra di dialogo Gestione connessione Excel](../../2014/tutorials/media/et-addingexcelsourcetothedataflow-01.jpg "finestra di dialogo Gestione connessione Excel")  
  
7.  Nel **Editor origine Excel** finestra di dialogo **IncomingSuppliers$** nel **nome del foglio di Excel** casella di riepilogo.  
  
     ![Nome del foglio di Excel - fornitori$ in entrata](../../2014/tutorials/media/et-addingexcelsourcetothedataflow-02.jpg "nome del foglio di Excel - fornitori$ in entrata")  
  
8.  Fare clic su **anteprima** in anteprima i dati nel file di Excel.  
  
9. Scegliere **OK** per chiudere la finestra di dialogo.  
  
10. Trascinare **DQS Cleansing** trasforma nello **altre trasformazioni** sul **casella degli strumenti SSIS** per il **del flusso di dati** disponibile nella scheda  **Leggere i dati fornitore dal File di Excel**. Nella trasformazione DQS Cleansing viene utilizzato Data Quality Services (DQS) per correggere i dati applicando le regole approvate nella Knowledge Base. In fase di esecuzione, tramite questa trasformazione viene creato un progetto DQS Cleansing nel server DQS. Vedere [trasformazione DQS Cleansing](http://msdn.microsoft.com/library/ee677619.aspx) per altre informazioni.  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 7: Aggiunta della trasformazione DQS Cleansing al flusso di dati](../integration-services/data-flow/data-flow.md)  
  
  