---
title: 'Attività 13: Aggiunta della destinazione OLE DB per scrivere dati nella tabella di Staging MDS | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: e6c67fa9-bb52-44a9-82f6-d86551cf12b2
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: bf8a96891040a6a751e0a6e34c902d77cec9dd35
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48223101"
---
# <a name="task-13-adding-ole-db-destination-to-write-data-to-mds-staging-table"></a>Attività 13: Aggiunta di Destinazione OLE DB a Scrivi dati fornitore nella tabella di gestione temporanea MDS
  Ora che sono stati aggiunti **ImportType** e **BatchTag** valori a tutti i record, si è pronti per inviarli a MDS per la gestione temporanea. In questa attività si utilizza la destinazione OLE DB per scrivere i dati in **stg. supplier_leaf** tabella di staging.  
  
1.  Trascinare **OLE DB Destination** dalla **altre destinazioni** sezione la **casella degli strumenti SSIS** per il **del flusso di dati** scheda e rilasciarlo sotto  **Aggiungi colonne richieste da MDS**.  
  
2.  Fare doppio clic su **OLE DB Destination** nel **flusso di dati** scheda, quindi scegliere **rinominare**. Tipo di **Scrivi dati fornitore nella tabella di gestione temporanea MDS** , quindi premere **invio**.  
  
3.  Connettere il **Aggiungi colonne richieste da MDS** al **Scrivi dati fornitore nella tabella di gestione temporanea MDS** usando il collegamento blu.  
  
4.  Fare doppio clic su **Scrivi dati fornitore nella tabella di gestione temporanea MDS** nel **flusso di dati** scheda.  
  
5.  Nel **Editor destinazione OLE DB** finestra di dialogo, assicurarsi che **(locale). MDS** (o **localhost. MDS**) sia selezionata per il **gestione connessione OLE DB** campo.  
  
6.  Selezionare **stg. Supplier_Leaf** tabella dall'elenco dei **nome tabella o vista**.  
  
     ![Editor destinazione OLEDB](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-01.jpg "Editor destinazione OLE DB")  
  
7.  Passare al **mapping** , facendo clic su **Mapping** nel menu a sinistra.  
  
8.  Mappa **input** e **destinazione** colonne, come mostrato nella tabella seguente.  
  
     ![Editor destinazione ODBC - mapping](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-02.jpg "Editor destinazione ODBC - mapping")  
  
9. Confermare che si usi **_Output** le colonne per le colonne di Input, non il **_Status** oppure **_Source** colonne. **Output** colonne contengono valori di output di DQS Cleansing.  
  
10. Fare clic su **OK** per chiudere la **Editor destinazione OLE DB** nella finestra di dialogo.  
  
11. Il flusso di dati deve essere simile alla figura seguente.  
  
     ![Completare il flusso di dati](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-03.jpg "completato il flusso di dati")  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 14: Aggiunta dell'Attività Esegui SQL al flusso di controllo per eseguire la stored procedure per MDS](../../2014/tutorials/task-14-add-execute-to-control-flow-run-mds-stored-procedure.md)  
  
  
