---
title: Open (metodo) (Recordset ADO) | Documenti Microsoft
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
apitype: COM
f1_keywords:
- Recordset15::raw_Open
- Recordset15::Open
helpviewer_keywords:
- Open method [ADO]
ms.assetid: 3236749c-4b71-4235-89e2-ccdfaaa9319d
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8aded01fb6fa5bb8c84f21379d10f9b3c76ce731
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="open-method-ado-recordset"></a>Open (metodo) (Recordset ADO)
Apre un cursore su un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
recordset.Open Source, ActiveConnection, CursorType, LockType, Options  
```  
  
#### <a name="parameters"></a>Parametri  
 *Origine*  
 Facoltativa. Oggetto **Variant** che restituisce un valore valido [comando](../../../ado/reference/ado-api/command-object-ado.md) oggetto, un'istruzione SQL, un nome di tabella, una chiamata alla stored procedure, un URL o il nome di un file o [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetto che contiene un memorizzarlo [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
 *ActiveConnection*  
 Facoltativa. Entrambi un **Variant** che restituisce un valore valido [connessione](../../../ado/reference/ado-api/connection-object-ado.md) nome di variabile oggetto o un **stringa** contenente [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) parametri.  
  
 *CursorType*  
 Facoltativa. Oggetto [CursorTypeEnum](../../../ado/reference/ado-api/cursortypeenum.md) valore che determina il tipo di cursore che il provider deve utilizzare quando si apre il **Recordset**. Il valore predefinito è **adOpenForwardOnly**.  
  
 *LockType*  
 Facoltativa. Oggetto [LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md) valore che determina il tipo di blocco (concorrenza) il provider deve utilizzare quando si apre il **Recordset**. Il valore predefinito è **adLockReadOnly**.  
  
 *Opzioni*  
 Facoltativa. A **lungo** valore che indica la modalità con cui il provider deve valutare il *origine* argomento se rappresenta un elemento diverso da un **comando** oggetto o che il **Recordset** deve essere ripristinato da un file in cui è stato salvato in precedenza. Può essere uno o più [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) o [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) valori, che possono essere combinati con un operatore OR bit per bit.  
  
> [!NOTE]
>  Se si apre un **Recordset** da un **flusso** contenente un persistente **Recordset**, usando un [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) valore **adAsyncFetchNonBlocking** non avrà effetto; l'operazione di recupero sarà sincrono e di blocco.  
  
> [!NOTE]
>  Il **ExecuteOpenEnum** valori di **adExecuteStream** o **adExecuteStream** non deve essere utilizzato con **aprire**.  
  
## <a name="remarks"></a>Osservazioni  
 Il cursore predefinito per un oggetto ADO **Recordset** è un cursore forward-only di sola lettura sul server.  
  
 Utilizzando il **aprire** metodo su un **Recordset** oggetto viene aperto un cursore che rappresenta i record da una tabella di base, i risultati di una query o salvato in precedenza **Recordset**.  
  
 Utilizzare l'opzione facoltativa *origine* argomento per specificare un'origine dati utilizzando uno dei seguenti: un **comando** variabile oggetto, un'istruzione SQL, una stored procedure, un nome di tabella, un URL o un nome di percorso completo del file. Se *origine* è un nome di percorso di file, può essere un percorso completo ("c:\dir\file.rst"), un percorso relativo ("... \File.rst"), o un URL ("http://files/file.rst").  
  
 Non è consigliabile utilizzare il *origine* argomento del **aprire** metodo per eseguire una query di azione che restituisce record perché non è un modo semplice per determinare se la chiamata ha avuto esito positivo. Il **Recordset** restituito da ad una query verrà chiusa. Per eseguire una query che restituisce record, ad esempio un'istruzione SQL INSERT, chiamare il [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) metodo di un **comando** oggetto o [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md) metodo di un [Connessione](../../../ado/reference/ado-api/connection-object-ado.md) invece dell'oggetto.  
  
 Il *ActiveConnection* argomento corrisponde alla [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) proprietà e specifica la connessione in cui aprire il **Recordset** oggetto. Se si passa una definizione di connessione per questo argomento, ADO apre una nuova connessione utilizzando i parametri specificati. Dopo aver aperto il **Recordset** con un cursore sul lato client impostando il [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) proprietà **adUseClient**, è possibile modificare il valore di questa proprietà per l'invio aggiornamenti in un altro provider. Oppure è possibile impostare questa proprietà **nulla** (in Microsoft Visual Basic) o NULL per disconnettere il **Recordset** da qualsiasi provider. Modifica *ActiveConnection* per un cursore sul lato server genera un errore, tuttavia.  
  
 Per gli altri argomenti che corrispondono direttamente alle proprietà di un **Recordset** oggetto (*origine*, *CursorType*, e *LockType*), la relazione tra gli argomenti e la proprietà è come segue:  
  
-   La proprietà è di lettura/scrittura prima di **Recordset** viene aperto l'oggetto.  
  
-   Le impostazioni delle proprietà vengono utilizzate solo se si passano gli argomenti corrispondenti quando si esegue il **aprire** metodo. Se si passa un argomento, viene eseguito l'override dell'impostazione della proprietà corrispondente e l'impostazione della proprietà viene aggiornata con il valore dell'argomento.  
  
-   Dopo aver aperto il **Recordset** dell'oggetto, queste proprietà diventano di sola lettura.  
  
> [!NOTE]
>  Il **ActiveConnection** proprietà è di sola lettura per **Recordset** oggetti la cui proprietà [origine](../../../ado/reference/ado-api/source-property-ado-recordset.md) proprietà è impostata su un valore valido **comando** oggetto, anche se il **Recordset** oggetto non è aperto.  
  
 Se si passa un **comando** oggetto di *origine* argomento e passare un *ActiveConnection* si verifica un errore di argomento,. Il **ActiveConnection** proprietà del **comando** oggetto deve essere già impostato su un valore valido **connessione** oggetto o stringa di connessione.  
  
 Se si passa un valore diverso da un **comando** oggetto di *origine* argomento, è possibile utilizzare il *opzioni* argomento per ottimizzare la valutazione del *origine*  argomento. Se il *opzioni* argomento non è definito, è possibile effetti negativi sulle prestazioni poiché ADO deve eseguire chiamate al provider per determinare se l'argomento è un'istruzione SQL, una stored procedure, un URL o un nome di tabella. Se si conosce il *origine* tipo in uso, l'impostazione di *opzioni* argomento indica ad ADO per passare direttamente al codice pertinente. Se il *opzioni* argomento non corrisponde la *origine* digitare, si verifica un errore.  
  
 Se si passa un **flusso** oggetto di *origine* argomento, è consigliabile non passare le informazioni negli altri argomenti. In questo modo verrà generato un errore. Il **ActiveConnection** informazioni non sono mantenute quando un **Recordset** viene aperto da un **flusso**.  
  
 Il valore predefinito per il *opzioni* argomento **adCmdFile** se nessuna connessione è associata il **Recordset**. Ciò corrisponderà in genere il caso per memorizzare in modo persistente **Recordset** oggetti.  
  
 Se l'origine dati viene restituito alcun record, il provider imposta entrambe le [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) e [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) proprietà **True**, e la posizione corrente non è definita. È comunque possibile aggiungere nuovi dati questo vuoto **Recordset** se il tipo di cursore consente dell'oggetto.  
  
 Quando si hanno concluso le operazioni attraverso un **Recordset** oggetto, usare il [Chiudi](../../../ado/reference/ado-api/close-method-ado.md) metodo per liberare le risorse di sistema associate. Chiusura di un oggetto senza rimuoverlo dalla memoria. è possibile modificare le impostazioni delle proprietà e utilizzare il **aprire** metodo aprirlo più tardi. Per eliminare completamente l'oggetto dalla memoria, impostare la variabile oggetto *nulla*.  
  
 Prima di **ActiveConnection** proprietà è impostata, chiamare **aprire** senza operandi per creare un'istanza di un **Recordset** creato aggiungendo campi al  **Recordset** [campi](../../../ado/reference/ado-api/fields-collection-ado.md) insieme.  
  
 Se è stata impostata la [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) proprietà **adUseClient**, è possibile recuperare le righe in modo asincrono in uno dei due modi. Il metodo consigliato consiste nell'impostare *opzioni* a **adAsyncFetch**. In alternativa, è possibile utilizzare la proprietà dinamica "Asynchronous Processing set di righe" nel [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) raccolta, ma gli eventi recuperati correlati possono essere perso se non si imposta la *opzioni* parametro **adAsyncFetch**.  
  
> [!NOTE]
>  Il recupero in background nel provider MS Remote è supportato solo tramite il **aprire** del metodo *opzioni* parametro.  
  
> [!NOTE]
>  Gli URL che utilizzano lo schema http richiamerà automaticamente il [il Provider Microsoft OLE DB per Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Per ulteriori informazioni, vedere [URL assoluti e relativi](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
 Alcune combinazioni di [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) e [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) valori non sono validi. Per informazioni sulle opzioni non possono essere combinate, vedere gli argomenti per il [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md), e [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md).  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di metodi di apertura e chiusura (VB)](../../../ado/reference/ado-api/open-and-close-methods-example-vb.md)   
 [Esempio di metodi di apertura e chiusura (VBScript)](../../../ado/reference/ado-api/open-and-close-methods-example-vbscript.md)   
 [Esempio di metodi di apertura e chiusura (VC + +)](../../../ado/reference/ado-api/open-and-close-methods-example-vc.md)   
 [Salvare e aprire l'esempio di metodi (VB)](../../../ado/reference/ado-api/save-and-open-methods-example-vb.md)   
 [Open (metodo) (connessione ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open (metodo) (Record ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Open (metodo) (flusso ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [Metodo OpenSchema](../../../ado/reference/ado-api/openschema-method.md)   
 [Metodo Save](../../../ado/reference/ado-api/save-method.md)
