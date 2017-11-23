---
title: I commenti sulle HelloData | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: hellodata sample application [ADO]
ms.assetid: a2831d77-7040-4b73-bbae-fe0bf78107ed
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: adda58b0be044229cc4efc26c65b1af1c4ca3dc0
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="comments-on-hellodata"></a>Commenti sulle HelloData
L'applicazione HelloData scorre le operazioni di base di una tipica applicazione ADO: recupero, esame, la modifica e aggiornamento dei dati. Quando si avvia l'applicazione, fare clic sul pulsante prima, **recupera dati**. Verrà eseguito il **GetData** subroutine.  
  
## <a name="getdata"></a>GetData  
 **GetData** inserisce una stringa di connessione valido in una variabile a livello di modulo, *m_sConnStr*. Per ulteriori informazioni sulle stringhe di connessione, vedere [creazione della stringa di connessione](../../../ado/guide/data/creating-a-connection-string.md).  
  
 Assegnare un gestore degli errori utilizzando Visual Basic **OnError** istruzione. Per ulteriori informazioni sulla gestione degli errori in ADO, vedere [Error Handling](../../../ado/guide/data/error-handling.md). Un nuovo **connessione** oggetto viene creato e **CursorLocation** è impostata su **adUseClient** perché l'esempio HelloData crea un  *set di record disconnesso*. Ciò significa che non appena i dati sono stati trasferiti dall'origine dati, la connessione fisica con l'origine dati viene interrotta, ma è ancora possibile utilizzare con i dati memorizzati nella cache in locale nel **Recordset** oggetto.  
  
 Dopo aver aperto la connessione, è possibile assegnare una stringa SQL a una variabile (sSQL). Quindi creare un'istanza di un nuovo **Recordset** oggetto `m_oRecordset1`. Nella riga successiva del codice, aprire il **Recordset** su esistente **connessione**, passando `sSQL` come origine il **Recordset**. Consente di ADO in effettua la determinazione di stringa SQL superati come origine per il **Recordset** è una definizione di un comando testuale passando **adCmdText** nell'argomento finale per il **Apertura di un Recordset** metodo. Questa riga imposta inoltre il **LockType** e **CursorType** associato il **Recordset**.  
  
 La riga successiva del set di codice il **MarshalOptions** proprietà è uguale a **adMarshalModifiedOnly**. **MarshalOptions** indica di effettuare il marshalling dei record al livello intermedio (o al server Web). Per ulteriori informazioni sul marshalling, vedere la documentazione di COM. Quando si utilizza **adMarshalModifiedOnly** con un cursore sul lato client ([CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) = **adUseClient**), solo i record che sono stati modificati sul client vengono scritte nel livello intermedio. Impostazione **MarshalOptions** a **adMarshalModifiedOnly** può migliorare le prestazioni in quanto un minor numero di righe vengono eseguito il marshalling.  
  
 Successivamente, disconnettere il **Recordset** impostando il relativo **ActiveConnection** proprietà è uguale a **nulla**. Per ulteriori informazioni, vedere la sezione "Disconnessione e riconnessione di Recordset il" in [aggiornamento e il mantenimento dati](../../../ado/guide/data/updating-and-persisting-data.md).  
  
 Chiudere la connessione all'origine dati ed eliminare esistente **connessione** oggetto. Rilascia le risorse che utilizzata.  
  
 Il passaggio finale consiste nell'impostare il **Recordset** come il **DataSource** per Microsoft DataGrid controllo nel form in modo che è possibile visualizzare facilmente i dati dal **Recordset** sul modulo.  
  
 Fare clic sul secondo pulsante, **esaminare dati**. Viene eseguita la **ExamineData** subroutine.  
  
## <a name="examinedata"></a>ExamineData  
 ExamineData utilizza diversi metodi e proprietà del **Recordset** oggetto per visualizzare le informazioni relative ai dati di **Recordset**. Restituisce il numero di record mediante il **RecordCount** proprietà. Eseguire un ciclo di **Recordset** e stampa il valore della **AbsolutePosition** proprietà nella casella di testo visualizzato nel form. Anche all'interno del ciclo, il valore di **segnalibro** proprietà per il terzo record viene inserita in una variabile variant, *vBookmark*, per un uso successivo.  
  
 La routine passa direttamente al terzo record utilizzando la variabile di segnalibro memorizzate in precedenza. Le chiamate di routine di **WalkFields** subroutine, che consente di scorrere il **campi** insieme del **Recordset** e Visualizza informazioni dettagliate su ciascuno **campo**  nella raccolta.  
  
 Infine, **ExamineData** utilizza il **filtro** proprietà del **Recordset** sullo schermo solo i record con un **CategoryId** uguale a 2. Il risultato dell'applicazione di questo filtro è immediatamente visibile nella griglia di visualizzazione del form.  
  
 Per ulteriori informazioni sulle funzionalità visualizzate nel **ExamineData** subroutine, vedere [analisi dei dati](../../../ado/guide/data/examining-data.md).  
  
 Successivamente, fare clic sul pulsante terzo, **modifica dati**. Verrà eseguito il **EditData** subroutine.  
  
## <a name="editdata"></a>EditData  
 Quando il codice avvia il **EditData** subroutine, il **Recordset** ancora viene applicato un filtro **CategoryId** è uguale a 2, in modo che solo gli elementi che soddisfano i criteri di filtro visibile. Viene innanzitutto eseguita una ricerca di **Recordset** e aumenta il prezzo di ogni elemento visibile il **Recordset** del 10%. Il valore della **prezzo** campo viene modificato impostando la **valore** proprietà per il campo uguale a una quantità di nuovo, valida.  
  
 Tenere presente che il **Recordset** viene disconnesso dall'origine dati. Le modifiche apportate in **EditData** vengono effettuate solo per la copia memorizzata nella cache locale dei dati. Per ulteriori informazioni, vedere [modifica dei dati](../../../ado/guide/data/editing-data.md).  
  
 Le modifiche verranno apportate non nell'origine dati finché non si sceglie il quarto pulsante **aggiornare i dati**. Verrà eseguito il **UpdateData** subroutine.  
  
## <a name="updatedata"></a>UpdateData  
 UpdateData rimuove innanzitutto il filtro che è stato applicato il **Recordset**. Il codice rimuove e reimposta `m_oRecordset1` come il **DataSource** per Microsoft Bound DataGrid nel form in modo che il non filtrato **Recordset** visualizzato nella griglia.  
  
 Il codice verifica quindi se è possibile spostarsi all'indietro **Recordset** utilizzando il **supporta** metodo con il **adMovePrevious** argomento.  
  
 La routine viene spostato nel primo record usando il **MoveFirst** metodo e visualizza i valori del campo originali e correnti, tramite il **OriginalValue** e **valore** proprietà del **campo** oggetto. Queste proprietà, insieme con il **UnderlyingValue** proprietà (non usato in questo esempio) vengono discussi in [aggiornamento e il mantenimento dati](../../../ado/guide/data/updating-and-persisting-data.md).  
  
 Successivamente, un nuovo **connessione** oggetto viene creato e utilizzato per ristabilire una connessione all'origine dati. Si riconnette il **Recordset** all'origine dati impostando la nuova **connessione** come il **ActiveConnection** per il **Recordset**. Per inviare gli aggiornamenti al server, il codice chiama **UpdateBatch** sul **Recordset**.  
  
 Se l'aggiornamento batch ha esito positivo, la variabile a livello di modulo flag `m_flgPriceUpdated`, è impostata su True. Si ricordi in un secondo momento per pulire tutte le modifiche apportate al database.  
  
 Infine, il codice consente di tornare al primo record di **Recordset** e visualizza i valori originali e correnti. I valori sono la stessa dopo la chiamata a **UpdateBatch**.  
  
 Per informazioni dettagliate su come aggiornare i dati, tra cui operazioni da eseguire quando dati alle modifiche del server durante il **Recordset** è disconnesso, vedere [aggiornamento e il mantenimento dati](../../../ado/guide/data/updating-and-persisting-data.md).  
  
## <a name="formunload"></a>Form_Unload  
 Il **Form_Unload** subroutine è importante per diversi motivi. In primo luogo, poiché si tratta di un'applicazione di esempio, Form_Unload pulisce le modifiche apportate al database prima la chiusura dell'applicazione. In secondo luogo, il codice viene illustrato come un comando può essere eseguito direttamente da open **connessione** oggetto utilizzando il **Execute** metodo. Infine, viene riportato un esempio di esecuzione di una query non – restituiscono righe (una query di aggiornamento) rispetto all'origine dati.
