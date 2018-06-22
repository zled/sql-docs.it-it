---
title: 'Attività 13: Aggiunta della destinazione OLE DB per scrivere dati nella tabella di gestione temporanea MDS | Documenti Microsoft'
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
ms.assetid: e6c67fa9-bb52-44a9-82f6-d86551cf12b2
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 75e77579857852e607b783534d149367a946318f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064352"
---
# <a name="task-13-adding-ole-db-destination-to-write-data-to-mds-staging-table"></a>Attività 13: Aggiunta di Destinazione OLE DB a Scrivi dati fornitore nella tabella di gestione temporanea MDS
  Ora che è stato aggiunto **ImportType** e **BatchTag** valori da tutti i record, si è pronti per inviarli a MDS per la gestione temporanea. In questa attività, utilizzare la destinazione OLE DB per scrivere i dati nella **stg. supplier_leaf** tabella di gestione temporanea.  
  
1.  Trascinare **OLE DB Destination** da **altre destinazioni** sezione il **casella degli strumenti SSIS** per il **del flusso di dati** scheda e rilasciarlo sotto  **Aggiungi colonne richieste da MDS**.  
  
2.  Fare doppio clic su **OLE DB Destination** nel **del flusso di dati** scheda e fare clic su **rinominare**. Tipo di **Scrivi dati fornitore nella tabella di gestione temporanea MDS** e premere **invio**.  
  
3.  Connettere il **Aggiungi colonne richieste da MDS** alla **Scrivi dati fornitore nella tabella di gestione temporanea MDS** utilizzando il collegamento blu.  
  
4.  Fare doppio clic su **Scrivi dati fornitore nella tabella di gestione temporanea MDS** nel **del flusso di dati** scheda.  
  
5.  Nel **Editor destinazione OLE DB** finestra di dialogo casella, assicurarsi che **(local). MDS** (o **localhost. MDS**) è selezionato per il **gestione connessione OLE DB** campo.  
  
6.  Selezionare **stg. Supplier_Leaf** tabella dall'elenco dei **nome della tabella o vista**.  
  
     ![Editor destinazione OLE DB](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-01.jpg "Editor destinazione OLE DB")  
  
7.  Passare il **mapping** pagina facendo clic su **Mapping** nel menu di sinistra.  
  
8.  Mappa **input** e **destinazione** colonne come illustrato nella tabella seguente.  
  
     ![Editor destinazione ODBC - mapping](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-02.jpg "Editor destinazione ODBC - mapping")  
  
9. Verificare che sia in uso **output** le colonne per le colonne di Input, non il **_Status** oppure **_Source** colonne. **Output** colonne contengono i valori di output di DQS Cleansing.  
  
10. Fare clic su **OK** per chiudere la **Editor destinazione OLE DB** finestra di dialogo.  
  
11. Il flusso di dati deve essere simile alla figura seguente.  
  
     ![Completare il flusso di dati](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-03.jpg "completato il flusso di dati")  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 14: Aggiunta di attività Esegui SQL al flusso di controllo per eseguire la Stored Procedure per MDS](../../2014/tutorials/task-14-add-execute-to-control-flow-run-mds-stored-procedure.md)  
  
  