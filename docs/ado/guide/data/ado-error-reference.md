---
title: Riferimento all'errore ADO | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: H1Hack27Feb2017
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors [ADO], number reference
- errors [ADO], ErrorValueEnum
- ErrorValueEnum enumeration [ADO]
ms.assetid: f653393e-d4b0-4c34-ad5f-2bdf56bc1305
caps.latest.revision: 4
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2604f09ecffab3e0f5519731acffa00111af9677
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="ado-errors"></a>Errori ADO
Il **ErrorValueEnum** costante descrive i valori di errore ADO. Per un elenco completo delle costanti enumerate, inclusi i valori, vedere [appendice b: errori di ADO](../../../ado/guide/appendixes/appendix-b-ado-errors.md). In questa sezione verrà esaminare alcuni degli errori più interessanti e vengono descritte alcune situazioni specifiche che possono generare o soluzioni per risolvere il problema. Entrambi i **ErrorValueEnum** costante e il numero di decimale positivo breve sono elencati.

|Number|Costante ErrorValueEnum|Descrizione/possibili cause|
|------------|-----------------------------|----------------------------------|
|**3000**|**adErrProviderFailed**|Errore del provider eseguire l'operazione richiesta.|
|**3001**|**adErrInvalidArgument**|Gli argomenti sono di tipo errato, sono compreso nell'intervallo accettabile o sono in conflitto. Questo errore è spesso causato da un errore di battitura in un'istruzione SQL SELECT. Ad esempio, un nome di campo errato o un nome di tabella può generare questo errore. Questo errore può verificarsi anche quando un campo o una tabella denominata in un'istruzione SELECT non esiste nell'archivio dati.|
|**3002**|**adErrOpeningFile**|Impossibile aprire il file. È stato specificato un nome file errato o un file è stato spostato, rinominato o eliminato. In una rete, l'unità potrebbe essere temporaneamente non disponibile oppure potrebbe essere il traffico di rete che impediscono la connessione.|
|**3003**|**adErrReadFile**|Non è stato possibile leggere i file. Il nome del file è stato specificato correttamente, il file potrebbe essere stato spostato o eliminato o il file potrebbe essere danneggiato.|
|**3004**|**adErrWriteFile**|Impossibile scrivere nel file. È un file potrebbe essere stato chiuso e ha cercato di scrittura o il file potrebbe essere danneggiato. Se il file si trova in un'unità di rete, condizioni temporanee della rete potrebbero impedire la scrittura in un'unità di rete.|
|**3021**|**adErrNoCurrentRecord**|Entrambi **BOF** o **EOF** è True, o il record corrente è stato eliminato. Operazione richiesta richiede un record corrente.<br /><br /> Si è verificato un tentativo di aggiornare i record utilizzando **trovare** o **Seek** per spostare il puntatore del record nel record desiderato. Se non viene trovato il record, **EOF** sia impostato su True. Questo errore può verificarsi anche dopo un errore **AddNew** o **eliminare** perché non sono presenti record corrente quando questi metodi hanno esito negativo.|
|**3219**|**adErrIllegalOperation**|Operazione non è consentita in questo contesto.|
|**3220**|**adErrCantChangeProvider**|Il provider specificato è diverso da quello già in uso.|
|**3246**|**adErrInTransaction**|**Connessione** oggetto non può essere chiusa in modo esplicito in una transazione. Oggetto **Recordset** o **connessione** oggetto che fa attualmente parte di una transazione non può essere chiuso. Chiamare **RollbackTrans** o **CommitTrans** prima di chiudere l'oggetto.|
|**3251**|**adErrFeatureNotAvailable**|L'oggetto o il provider non è in grado di eseguire l'operazione richiesta. Alcune operazioni dipendono da una versione specifica del provider.|
|**3265**|**adErrItemNotFound**|Impossibile trovare l'elemento nella raccolta corrispondente al nome richiesto o per ordinale. È stato specificato un nome di campo o una tabella non corretto.|
|**3367**|**adErrObjectInCollection**|Oggetto è già nella raccolta. Impossibile accodare. Un oggetto non può essere aggiunto due volte nella stessa raccolta.|
|**3420**|**adErrObjectNotSet**|Oggetto non è più valido.|
|**3421**|**adErrDataConversion**|Applicazione utilizza un valore di tipo errato per l'operazione corrente. Una stringa a un'operazione che prevede un flusso, ad esempio potrebbe essere stato specificato.|
|**3704**|**adErrObjectClosed**|Operazione non è consentita quando l'oggetto viene chiuso. Il **connessione** o **Recordset** è stata chiusa. Ad esempio, alcune altre routine potrebbe chiuso un oggetto globale. È possibile impedire questo errore selezionando il **stato** proprietà prima di tentare un'operazione.|
|**3705**|**adErrObjectOpen**|Operazione non è consentita quando l'oggetto è aperto. Impossibile aprire un oggetto che è aperto. Non è possibile aggiungere campi a un oggetto aperto **Recordset**.|
|**3706**|**adErrProviderNotFound**|Impossibile trovare il provider. Si potrebbe non essere installato correttamente.<br /><br /> Il nome del provider può essere specificato in modo non corretto, il provider specificato potrebbe non essere installato nel computer in cui viene eseguito il codice o l'installazione potrebbe essere danneggiato.|
|**3707**|**adErrBoundToCommand**|Il **ActiveConnection** proprietà di un **Recordset** object, che contiene un **comando** come origine dell'oggetto, non può essere modificato. L'applicazione ha tentato di assegnare un nuovo **connessione** l'oggetto in un **Recordset** che ha un **comando** oggetto come origine.|
|**3708**|**adErrInvalidParamInfo**|**Parametro** oggetto non è definito correttamente. Informazioni incomplete o è state specificate.|
|**3709**|**adErrInvalidConnection**|La connessione non può essere utilizzata per eseguire questa operazione. È chiuso o non valido in questo contesto.|
|**3710**|**adErrNotReentrant**|Impossibile eseguire l'operazione durante l'elaborazione dell'evento. Impossibile eseguire un'operazione all'interno di un gestore dell'evento che causa l'evento che attiva nuovamente. Ad esempio, metodi di navigazione non devono essere chiamati dall'interno un **WillMove** gestore dell'evento.|
|**3711**|**adErrStillExecuting**|Impossibile eseguire l'operazione durante l'esecuzione in modo asincrono.|
|**3712**|**adErrOperationCancelled**|Operazione annullata dall'utente. L'applicazione ha chiamato la **CancelUpdate** o **CancelBatch** (metodo) e l'operazione corrente è stata annullata.|
|**3713**|**adErrStillConnecting**|Impossibile eseguire l'operazione durante la connessione in modo asincrono.|
|**3714**|**adErrInvalidTransaction**|Il coordinamento della transazione non è valido o non è stato avviato.|
|**3715**|**adErrNotExecuting**|Operazione non può essere eseguita anche se non in esecuzione.|
|**3716**|**adErrUnsafeOperation**|Le impostazioni di sicurezza nel computer non consentono l'accesso a un'origine dati in un altro dominio.|
|**3717**|**adWrnSecurityDialog**|Solo per uso interno. Non usare. (Voce è stata inclusa per ragioni di completezza. Questo errore non deve essere visualizzati nel codice.)|
|**3718**|**adWrnSecurityDialogHeader**|Solo per uso interno. Non usare. (Voce è stata inclusa per ragioni di completezza. Questo errore non deve essere visualizzati nel codice.)|
|**3719**|**adErrIntegrityViolation**|Il valore dei dati è in conflitto con i vincoli di integrità del campo. Un nuovo valore per un **campo** causerebbe una chiave duplicata. Un valore corrispondente a un lato di una relazione tra due record potrebbe non essere aggiornabile.|
|**3720**|**adErrPermissionDenied**|Autorizzazioni insufficienti impediscono la scrittura del campo. L'utente specificato nella stringa di connessione non dispone delle autorizzazioni appropriate per scrivere un **campo**.|
|**3721**|**adErrDataOverflow**|Il valore di dati è troppo grande per essere rappresentato dal tipo di dati di campo. È stato assegnato un valore numerico che è troppo grande per il campo desiderato. Ad esempio, un valore long integer è stato assegnato a un campo valore short integer.|
|**3722**|**adErrSchemaViolation**|Il valore dei dati è in conflitto con il tipo di dati o i vincoli del campo. L'archivio dati presenta vincoli di convalida che differiscono dal **campo** valore.|
|**3723**|**adErrSignMismatch**|Conversione non riuscita perché il valore dei dati è con segno mentre il tipo di dati di campo utilizzato dal provider è senza segno.|
|**3724**|**adErrCantConvertvalue**|Impossibile convertire il valore di dati per motivi diversi overflow di dati o non corrispondenza del segno. Ad esempio, conversione causi il troncamento dei dati.|
|**3725**|**adErrCantCreate**|Valore di dati non può essere impostato o recuperato perché il tipo di dati del campo è sconosciuto, o il provider ha risorse insufficienti per eseguire l'operazione.|
|**3726**|**adErrColumnNotOnThisRow**|Record non contiene questo campo. È stato specificato un nome di campo errato o un campo non presente nella **campi** raccolta del record corrente è stato fatto riferimento.|
|**3727**|**adErrURLDoesNotExist**|L'URL di origine o l'elemento padre dell'URL di destinazione non esiste. Si verifica un errore di battitura nell'URL di origine o di destinazione. Potrebbe essere `http://mysite/photo/myphoto.jpg` quando è effettivamente necessario `http://mysite/photos/myphoto.jpg` invece. Errore di battitura nell'URL padre (in questo caso, *foto* anziché *foto*) che ha causato l'errore.|
|**3728**|**adErrTreePermissionDenied**|Autorizzazioni non sono sufficienti per accedere a struttura ad albero o sottoalbero. L'utente specificato nella stringa di connessione non dispone delle autorizzazioni appropriate.|
|**3729**|**adErrInvalidURL**|L'URL contiene caratteri non validi. Verificare che l'URL sia stato digitato correttamente. L'URL segue lo schema registrato per il provider corrente (ad esempio, Internet Publishing Provider è registrato per http).|
|**3730**|**adErrResourceLocked**|Oggetto rappresentato dall'URL specificato è bloccato da uno o più processi. Attendere il termine del processo e ripetere l'operazione. L'oggetto a cui che si sta tentando di accedere è stato bloccato da un altro utente o da un altro processo all'interno dell'applicazione. Questo è più probabile che si verificano in un ambiente multiutente.|
|**3731**|**adErrResourceExists**|Impossibile eseguire l'operazione di copia. Oggetto denominato dall'URL di destinazione già esistente. Specificare **adCopyOverwrite** di sostituire l'oggetto. Se non si specifica **adCopyOverwrite** quando si copiano i file in una directory, la copia ha esito negativo quando si tenta di copiare un elemento già esistente nel percorso di destinazione.|
|**3732**|**adErrCannotComplete**|Il server non è possibile completare l'operazione. È possibile che il server è occupato con altre operazioni o potrebbe essere risorse insufficiente.|
|**3733**|**adErrVolumeNotFound**|Impossibile individuare il dispositivo di archiviazione indicato dall'URL. Verificare che l'URL sia stato digitato correttamente. L'URL del dispositivo di archiviazione potrebbe non essere corretto, ma questo errore può verificarsi per altri motivi. Il dispositivo potrebbe essere offline o un volume elevato di traffico di rete potrebbe impedire la connessione venga eseguito.|
|**3734**|**adErrOutOfSpace**|Impossibile eseguire l'operazione. Il provider non è possibile ottenere spazio di archiviazione sufficiente. Si potrebbe non essere sufficiente RAM o spazio su disco rigido per i file temporanei nel server.|
|**3735**|**adErrResourceOutOfScope**|URL di origine o di destinazione è all'esterno dell'ambito del record corrente.|
|**3736**|**adErrUnavailable**|Impossibile completare l'operazione e lo stato non è disponibile. Il campo può essere non disponibile o non è stata tentata l'operazione. Potrebbe modificato o eliminato il campo che si sta tentando di accedere a un altro utente.|
|**3737**|**adErrURLNamedRowDoesNotExist**|Il record specificato da questo URL non esiste. Durante il tentativo di aprire un file utilizzando un **Record** dell'oggetto, il nome del file o il percorso del file è stato digitato correttamente.|
|**3738**|**adErrDelResOutOfScope**|L'URL dell'oggetto da eliminare è all'esterno dell'ambito del record corrente.|
|**3747**|**adErrCatalogNotSet**|Operazione richiede un valore valido **ParentCatalog**.|
|**3748**|**adErrCantChangeConnection**|Connessione è stata negata. La nuova richiesta di connessione ha caratteristiche diverse rispetto a quella già in uso.|
|**3749**|**adErrFieldsUpdateFailed**|Impossibile aggiornare i campi. Per ulteriori informazioni, esaminare il **stato** proprietà degli oggetti singoli campi. Questo errore può verificarsi in due casi: quando si modifica un **campo** il valore dell'oggetto in corso la modifica o aggiunta di un record per il database e quando si modificano le proprietà del **campo** oggetto stesso.<br /><br /> Il **Record** o **Recordset** aggiornamento non è riuscito a causa di un problema con uno dei campi nel record corrente. Enumerare i **campi** insieme e verificare il **stato** proprietà di ogni campo per determinare la causa del problema.|
|**3750**|**adErrDenyNotSupported**|Provider non supporta le restrizioni di condivisione. Si è verificato un tentativo di limitare la condivisione di file e il provider non supporta il concetto.|
|**3751**|**adErrDenyTypeNotSupported**|Provider non supporta il tipo richiesto restrizione della condivisione. Si è verificato un tentativo di stabilire un particolare tipo di condivisione file restrizione che non è supportato dal provider. Vedere la documentazione del provider per determinare le limitazioni di condivisione file sono supportate.|

