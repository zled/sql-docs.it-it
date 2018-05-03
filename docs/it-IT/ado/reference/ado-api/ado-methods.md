---
title: Metodi ADO | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, methods
- methods [ADO]
ms.assetid: a38c5670-ba28-44f3-bd5b-fcb46880e904
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c94c32ce964f7b8d1501ea30067e81a9d4357bf9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="ado-methods"></a>Metodi ADO
|||  
|-|-|  
|[AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)|Crea un nuovo record per un aggiornabile **Recordset** oggetto.|  
|[Accoda](../../../ado/reference/ado-api/append-method-ado.md)|Aggiunge un oggetto a una raccolta. Se la raccolta è **campi**, un nuovo **campo** oggetto può essere creato prima di essere aggiunto alla raccolta.|  
|[AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md)|Aggiunge dati a un testo di grandi dimensioni o dati binari **campo**, o a un **parametro** oggetto.|  
|[BeginTrans, CommitTrans e RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)|All'interno di elaborazione delle transazioni gestisce un **connessione** come illustrato di seguito:<br /><br /> **BeginTrans** , inizia una nuova transazione.<br /><br /> **CommitTrans** , Salva le modifiche e termina la transazione corrente. È possibile anche avviare una nuova transazione.<br /><br /> **RollbackTrans** , ovvero Annulla tutte le modifiche e termina la transazione corrente. È possibile anche avviare una nuova transazione.|  
|[Annulla](../../../ado/reference/ado-api/cancel-method-ado.md)|Annulla l'esecuzione di un in sospeso, chiamata asincrona.|  
|[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|Annulla un aggiornamento batch in sospeso.|  
|[CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)|Annulla le modifiche apportate alla riga corrente o nuova di un **Recordset** oggetto, o **campi** raccolta di un **Record** oggetto, prima di chiamare il  **Aggiornamento** metodo.|  
|[Clear](../../../ado/reference/ado-api/clear-method-ado.md)|Rimuove tutti i **errore** oggetti dal **errori** insieme.|  
|[Clone](../../../ado/reference/ado-api/clone-method-ado.md)|Crea un duplicato **Recordset** oggetto da un oggetto esistente **Recordset** oggetto. Facoltativamente, specifica che il clone è di sola lettura.|  
|[Chiudi](../../../ado/reference/ado-api/close-method-ado.md)|Chiude un oggetto aperto e gli eventuali oggetti dipendenti.|  
|[CompareBookmarks](../../../ado/reference/ado-api/comparebookmarks-method-ado.md)|Confronta due segnalibri e restituisce un'indicazione dei relativi valori.|  
|[CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md)|Copia un file o directory e il relativo contenuto, in un'altra posizione.|  
|[CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md)|Copia il numero specificato di caratteri o byte (in base alle **tipo**) nei **flusso** a un altro **flusso** oggetto.|  
|[CreateParameter](../../../ado/reference/ado-api/createparameter-method-ado.md)|Crea un nuovo **parametro** oggetto contenente le proprietà specificate.|  
|[Delete (raccolta di parametri ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)|Elimina un oggetto di **parametri** insieme.|  
|[Elimina (raccolta di campi ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)|Elimina un oggetto di **campi** insieme.|  
|[Delete (Recordset ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|Elimina il record corrente o un gruppo di record.|  
|[DeleteRecord](../../../ado/reference/ado-api/deleterecord-method-ado.md)|Elimina un file o directory e tutte le relative sottodirectory.|  
|[Eseguire (comando ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md)|Esegue la query, l'istruzione SQL o stored procedure specificata nel **CommandText** proprietà.|  
|[Eseguire (connessione ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md)|Esegue query specificata, istruzione SQL, stored procedure o il testo del provider.|  
|[Trova](../../../ado/reference/ado-api/find-method-ado.md)|Cerca un **Recordset** per la riga che soddisfa i criteri specificati.|  
|[Scaricamento](../../../ado/reference/ado-api/flush-method-ado.md)|Forza il contenuto del **flusso** rimanenti nel buffer di ADO per l'oggetto sottostante a cui il **flusso** associata.|  
|[Metodo get_OLEDBCommand](../../../ado/reference/ado-api/get-oledbcommand-method.md)|Restituisce il comando OLE DB sottostanti, innanzitutto propaga qualsiasi informazione di parametro impostato sul comando ADO al comando OLE DB.|  
|[GetChildren](../../../ado/reference/ado-api/getchildren-method-ado.md)|Restituisce un **Recordset** le cui righe rappresentano i file e sottodirectory della directory rappresentato da questo **Record**.|  
|[GetChunk](../../../ado/reference/ado-api/getchunk-method-ado.md)|Restituisce tutto o in parte, il contenuto di un testo di grandi dimensioni o dati binari **campo** oggetto.|  
|[Metodo GetDataProviderDSO](../../../ado/reference/ado-api/getdataproviderdso-method.md)|Recupera l'oggetto origine dati OLE DB sottostante dal provider di forma.|  
|[GetRows](../../../ado/reference/ado-api/getrows-method-ado.md)|Recupera i record multipli di un **Recordset** oggetto in una matrice.|  
|[GetString](../../../ado/reference/ado-api/getstring-method-ado.md)|Restituisce il **Recordset** sotto forma di stringa.|  
|[LoadFromFile](../../../ado/reference/ado-api/loadfromfile-method-ado.md)|Carica il contenuto di un file esistente in un **flusso**.|  
|[Sposta](../../../ado/reference/ado-api/move-method-ado.md)|Sposta la posizione del record corrente in un **Recordset** oggetto.|  
|[MoveFirst, MoveLast, MoveNext e MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Sposta il primo, ultimo, successivo o precedente record in un oggetto specificato **Recordset** oggetto e imposta tale record come record corrente.|  
|[MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md)|Sposta un file o una directory e il relativo contenuto, in un'altra posizione.|  
|[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)|Cancella il contenuto del **Recordset** dell'oggetto e restituisce il successivo **Recordset** anticipando attraverso una serie di comandi.|  
|[Open (connessione ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)|Apre una connessione a un'origine dati.|  
|[Open (Record ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)|Apre un oggetto esistente **Record** dell'oggetto o creare un nuovo file o directory.|  
|[Aprire (Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|Apre un cursore.|  
|[Open (flusso ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)|Apre un **flusso** oggetto per gestire i flussi di dati binario o di testo.|  
|[OpenSchema](../../../ado/reference/ado-api/openschema-method.md)|Ottiene informazioni sullo schema di database dal provider.|  
|[Metodo put_OLEDBCommand](../../../ado/reference/ado-api/put-oledbcommand-method.md)|Questo metodo non esegue alcuna operazione, viene sempre restituito S_OK.|  
|[Lettura](../../../ado/reference/ado-api/read-method.md)|Legge un numero specificato di byte da un **flusso** oggetto.|  
|[ReadText](../../../ado/reference/ado-api/readtext-method.md)|Legge un numero specificato di caratteri da un testo **flusso** oggetto.|  
|[Aggiorna](../../../ado/reference/ado-api/refresh-method-ado.md)|Aggiorna gli oggetti in una raccolta in modo da riflettere gli oggetti disponibili e specifiche del provider.|  
|[Requery](../../../ado/reference/ado-api/requery-method.md)|Aggiorna i dati in un **Recordset** oggetto rieseguendo la query in cui si basa l'oggetto.|  
|[Risincronizzazione](../../../ado/reference/ado-api/resync-method.md)|Aggiorna i dati nell'oggetto **Recordset** oggetto, o **campi** raccolta di un **Record** oggetto dal database sottostante.|  
|[Salva](../../../ado/reference/ado-api/save-method.md)|Salva il **Recordset** in un file o **flusso** oggetto.|  
|[SaveToFile](../../../ado/reference/ado-api/savetofile-method.md)|Salva il contenuto binario di un **flusso** in un file.|  
|[Ricerca](../../../ado/reference/ado-api/seek-method.md)|Cerca l'indice di un **Recordset** per individuare rapidamente la riga che corrisponde ai valori specificati e modifica la posizione della riga corrente di tale riga.|  
|[SetEOS](../../../ado/reference/ado-api/seteos-method.md)|Imposta la posizione che rappresenta la fine del flusso.|  
|[SkipLine](../../../ado/reference/ado-api/skipline-method.md)|Ignora un'intera riga durante la lettura di un flusso di testo.|  
|[Stat](../../../ado/reference/ado-api/stat-method.md)|Ottiene informazioni statistiche su un flusso aperto.|  
|[Supporti](../../../ado/reference/ado-api/supports-method.md)|Determina se un oggetto **Recordset** oggetto supporta un determinato tipo di funzionalità.|  
|[Update](../../../ado/reference/ado-api/update-method.md)|Salva le modifiche apportate alla riga corrente di un **Recordset** oggetto, o **campi** raccolta di un **Record** oggetto.|  
|[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)|Scrive tutti gli aggiornamenti di batch in sospeso sul disco.|  
|[Scrittura](../../../ado/reference/ado-api/write-method.md)|Scrive dati binari in un **flusso** oggetto.|  
|[WriteText](../../../ado/reference/ado-api/writetext-method.md)|Scrive una stringa di testo specificato in un **flusso** oggetto.|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ADO](../../../ado/reference/ado-api/ado-api-reference.md)   
 [Raccolte di ADO](../../../ado/reference/ado-api/ado-collections.md)   
 [Proprietà dinamiche ADO](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [Costanti enumerate ADO](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [Appendice b: errori di ADO](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [Eventi ADO](../../../ado/reference/ado-api/ado-events.md)   
 [Modello a oggetti ADO](../../../ado/reference/ado-api/ado-object-model.md)   
 [Le interfacce e gli oggetti ADO](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [Proprietà ADO](../../../ado/reference/ado-api/ado-properties.md)
