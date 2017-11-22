---
title: Oggetto Recordset (ADO) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: Recordset
helpviewer_keywords: Recordset object [ADO]
ms.assetid: ede1415f-c3df-4cc5-a05b-2576b2b84b60
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 02d767f733ed8cb3767d49cf092ff67d1e37ef54
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="recordset-object-ado"></a>Oggetto Recordset ADO)
Rappresenta l'intero set di record da una tabella di base o i risultati di un comando eseguito. In qualsiasi momento, il **Recordset** oggetto fa riferimento a un solo record all'interno del set di record corrente.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare **Recordset** oggetti per modificare i dati da un provider. Quando si utilizza ADO, la modifica dei dati quasi esclusivamente tramite **Recordset** oggetti. Tutti **Recordset** oggetti è costituito da record (righe) e campi (colonne). A seconda della funzionalità supportata dal provider, alcuni **Recordset** metodi o proprietà potrebbe non essere disponibili.  
  
 OGGETTO ADODB. Recordset è il valore ProgID che deve essere utilizzato per creare un **Recordset** oggetto. Applicazioni esistenti che fanno riferimento a ADOR obsoleti. Recordset continueranno a funzionare senza ricompilare, ma nuove attività di sviluppo deve fare riferimento a ADODB. Recordset.  
  
 Esistono quattro diversi tipi di cursore definiti in ADO:  
  
-   **Cursore dinamico** consente di visualizzare le aggiunte, modifiche ed eliminazioni da altri utenti; consente a tutti i tipi di spostamento all'interno di **Recordset** che non si basi su segnalibri; e consente i segnalibri, se il provider supporta essi.  
  
-   **Cursore keyset** aggiungere Behaves come un cursore dinamico, ad eccezione del fatto che impedisce la visualizzazione record ad altri utenti e impedisce l'accesso ai record eliminati dagli altri utenti. Le modifiche dei dati da altri utenti saranno ancora visibili. Supporta sempre i segnalibri e consente pertanto di tutti i tipi di spostamento all'interno di **Recordset**.  
  
-   **Cursore statico** fornisce una copia statica di un set di record da usare per trovare i dati o di generare report; consente sempre i segnalibri e pertanto tutti i tipi di spostamento all'interno di **Recordset**. Le aggiunte, modifiche o le eliminazioni eseguite da altri utenti non saranno visibili. Questo è l'unico tipo di cursore consentito quando si apre un lato client **Recordset** oggetto.  
  
-   **Cursore forward-only** consente solo mediante lo scorrimento in avanti il **Recordset**. Le aggiunte, modifiche o le eliminazioni eseguite da altri utenti non saranno visibili. Ciò migliora le prestazioni in situazioni in cui è necessario apportare solo una singola iterazione un **Recordset**.  
  
 Impostare il [CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md) proprietà prima apertura di **Recordset** di scegliere il tipo di cursore o di passare un *CursorType* argomento con il [aprire](../../../ado/reference/ado-api/open-method-ado-recordset.md)metodo. Alcuni provider non supporta tutti i tipi di cursore. Consultare la documentazione per il provider. Se non si specifica un tipo di cursore, ADO apre un cursore forward-only per impostazione predefinita.  
  
 Se il [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) è impostata su **adUseClient** per aprire un **Recordset**, **UnderlyingValue** proprietà [Campo](../../../ado/reference/ado-api/field-object.md) oggetti non è disponibile nell'oggetto restituito **Recordset** oggetto. Se usato con alcuni provider (ad esempio, il Provider di Microsoft ODBC per OLE DB in combinazione con Microsoft SQL Server), è possibile creare **Recordset** oggetti in modo indipendente da un oggetto definito in precedenza [connessione](../../../ado/reference/ado-api/connection-object-ado.md)oggetto passando una stringa di connessione con il **aprire** metodo. ADO verrà comunque creato un [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto, ma tale oggetto non viene assegnato a una variabile oggetto. Tuttavia, se si sta aprendo più **Recordset** oggetti tramite la stessa connessione, creare e aprire in modo esplicito un **connessione** oggetto; questa assegna il **connessione**oggetto a una variabile oggetto. Se non si esegue questa variabile di oggetto quando si apre il **Recordset** gli oggetti ADO crea un nuovo **connessione** oggetto per ogni nuovo **Recordset**, anche se si passa la stessa stringa di connessione.  
  
 È possibile creare tante **Recordset** oggetti in base alle esigenze.  
  
 Quando si apre un **Recordset**, il record corrente è posizionato sul primo record (se presente) e [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) e [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) sono impostate su **False**. Se non sono presenti record, il **BOF** e **EOF** sono le impostazioni delle proprietà **True**.  
  
 È possibile utilizzare il [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), **MoveLast**, **MoveNext**, e **MovePrevious** metodi; [spostare](../../../ado/reference/ado-api/move-method-ado.md) metodo. e [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md), [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md), e [filtro](../../../ado/reference/ado-api/filter-property.md) proprietà per riposizionare il record corrente, presupponendo che il provider supporta rilevanti funzionalità. Forward-only **Recordset** oggetti supportano solo il [MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) metodo. Quando si utilizza il **spostare** metodi per visitare ogni record (o enumerare le **Recordset**), è possibile utilizzare il **BOF** e **EOF** proprietà Se si è andati oltre l'inizio o fine di determinare il **Recordset**.  
  
 Prima di utilizzare qualsiasi funzionalità di un **Recordset** dell'oggetto, è necessario chiamare il **supporta** metodo sull'oggetto per verificare che la funzionalità è disponibile o supportato. Non è necessario utilizzare la funzionalità quando la **supporta** metodo restituisce false. Ad esempio, è possibile utilizzare il **MovePrevious** metodo solo se `Recordset.Supports(adMovePrevious)` restituisce **True**. In caso contrario, si verificherà un errore, perché il **Recordset** oggetto potrebbe essere stato chiuso e la funzionalità di rendering non disponibile nell'istanza. Se non è supportata una funzionalità che si è interessati, **supporta** restituirà false anche. In questo caso, è consigliabile evitare la chiamata di proprietà corrispondente o il metodo sul **Recrodset** oggetto.  
  
 **Recordset** oggetti possono supportare due tipi di aggiornamento: immediato e in batch. Aggiornamento immediato, tutte le modifiche ai dati vengono scritti immediatamente all'origine dati sottostante non appena viene chiamato il [aggiornamento](../../../ado/reference/ado-api/update-method.md) metodo. È inoltre possibile passare matrici di valori come parametri con il [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) e **aggiornare** metodi e aggiornare contemporaneamente più campi in un record.  
  
 Se un provider supporta l'aggiornamento in batch, è possibile eseguire il provider di memorizzare nella cache le modifiche a più di un record e quindi trasmessi in una singola chiamata al database con il [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) metodo. Questo vale per le modifiche apportate con il **AddNew**, **aggiornamento**, e [eliminare](../../../ado/reference/ado-api/delete-method-ado-recordset.md) metodi. Dopo aver chiamato il **UpdateBatch** (metodo), è possibile utilizzare il [stato](../../../ado/reference/ado-api/status-property-ado-recordset.md) proprietà per cercare eventuali conflitti di dati per risolverli.  
  
> [!NOTE]
>  Per eseguire una query senza utilizzare un [comando](../../../ado/reference/ado-api/command-object-ado.md) dell'oggetto, passare una stringa di query per il **aprire** metodo di un **Recordset** oggetto. Tuttavia, un **comando** oggetto sono obbligatorie quando si desidera mantenere il testo del comando ed eseguirla nuovamente o utilizzare i parametri di query.  
  
 Il [modalità](../../../ado/reference/ado-api/mode-property-ado.md) proprietà determina le autorizzazioni di accesso.  
  
 Il **campi** insieme è il membro predefinito del **Recordset** oggetto. Di conseguenza, le due istruzioni di codice seguenti sono equivalenti.  
  
```  
Debug.Print objRs.Fields.Item(0)  ' Both statements print   
Debug.Print objRs(0)              '  the Value of Item(0).  
```  
  
 Quando un **Recordset** oggetto viene passato tra processi, solo il **set di righe** sono marshalling valori e le proprietà del **Recordset** oggetto vengono ignorati. Durante l'unmarshalling, il **set di righe** viene decompresso in un oggetto appena creato **Recordset** oggetto, che imposta inoltre le proprietà per i valori predefiniti.  
  
 Il **Recordset** oggetto è sicuro per lo script.  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Le proprietà dell'oggetto Recordset, metodi ed eventi](../../../ado/reference/ado-api/recordset-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto di connessione (ADO.NET)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Raccolta di campi (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Raccolta delle proprietà (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Appendice A: Provider](../../../ado/guide/appendixes/appendix-a-providers.md)
