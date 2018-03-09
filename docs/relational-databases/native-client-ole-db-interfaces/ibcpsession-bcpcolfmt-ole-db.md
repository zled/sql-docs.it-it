---
title: 'Ibcpsession:: BCPColFmt (OLE DB) | Documenti Microsoft'
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-interfaces
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IBCPSession::BCPColFmt (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPColFmt method
ms.assetid: 2852f4ba-f1c6-4c4c-86b2-b77e4abe70de
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: af34e779db0662bd0fe35cef8cf8a8178ec134d9
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2018
---
# <a name="ibcpsessionbcpcolfmt-ole-db"></a>IBCPSession::BCPColFmt (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Crea un'associazione tra variabili di programma e colonne di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
HRESULT BCPColFmt(   
      DBORDINAL idxUserDataCol,  
      int eUserDataType,  
      int cbIndicator,  
      int cbUserData,  
      BYTE *pbUserDataTerm,  
      int cbUserDataTerm,  
      DBORDINAL idxServerCol);  
```  
  
## <a name="remarks"></a>Osservazioni  
 Il **BCPColFmt** metodo viene utilizzato per creare un'associazione tra campi del file di dati BCP e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] colonne. Accetta come parametri la lunghezza, il tipo, il carattere di terminazione e la lunghezza del prefisso di una colonna e imposta ciascuna di queste proprietà per i singoli campi.  
  
 Se l'utente sceglie la modalità interattiva, questo metodo viene chiamato due volte, una volta per impostare il formato della colonna in base ai valori predefiniti (che dipendono dal tipo di colonna del server) e una volta per impostare il formato in base al tipo di client selezionato durante la modalità interattiva, per ogni colonna.  
  
 Nelle modalità non interattive, viene chiamato una sola volta per colonna per impostare il tipo di ogni colonna sul carattere o sul tipo nativo e impostare i caratteri di terminazione di colonna e riga.  
  
 Il **BCPColFmt** metodo consente di specificare il formato di file utente per le copie bulk. Per la copia bulk, un formato contiene le parti seguenti:  
  
-   Un mapping dai campi del file utente alle colonne del database.  
  
-   Il tipo di dati di ogni campo del file utente.  
  
-   La lunghezza dell'indicatore facoltativo per ogni campo.  
  
-   La lunghezza massima dei dati per ogni campo del file utente.  
  
-   La sequenza di byte di terminazione facoltativa per ogni campo.  
  
-   La lunghezza della sequenza di byte di terminazione facoltativa.  
  
 Ogni chiamata a **BCPColFmt** specifica il formato per un campo del file utente. Ad esempio, per modificare le impostazioni predefinite per tre campi in un file di dati utente cinque campi, chiamare innanzitutto `BCPColumns(5)`e quindi chiamare **BCPColFmt** cinque volte, con tre di queste chiamate impostano il formato personalizzato. Per le due chiamate rimanenti, impostare *eUserDataType* su BCP_TYPE_DEFAULT e *cbIndicator*, *cbUserData*, e *cbUserDataTerm*su 0, BCP_VARIABLE_LENGTH e 0 rispettivamente. Questa procedura consente di copiare tutte e cinque le colonne, tre con il formato personalizzato e due con il formato predefinito.  
  
> [!NOTE]  
>  Il [ibcpsession:: BCPColumns](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md) metodo deve essere chiamato prima delle chiamate a **BCPColFmt**. È necessario chiamare **BCPColFmt** una volta per ogni colonna nel file utente. La chiamata **BCPColFmt** più di una volta per qualsiasi file utente colonna, viene generato un errore.  
  
 Non è necessario copiare tutti i dati di un file utente in una tabella [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per ignorare una colonna, specificare il formato dei dati per la colonna impostando il parametro idxServerCol su 0. Per ignorare un campo, è necessario comunque disporre di tutte le informazioni affinché il metodo possa funzionare correttamente.  
  
 **Nota** il [ibcpsession:: Bcpwritefmt](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md) funzione può essere utilizzata per rendere persistente la specifica di formato fornita tramite **BCPColFmt**.  
  
## <a name="arguments"></a>Argomenti  
 *idxUserDataCol*[in]  
 Indice del campo nel file di dati dell'utente.  
  
 *eUserDataType*[in]  
 Il tipo di dati del campo nel file di dati dell'utente. I tipi di dati disponibili sono elencati nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] formato di file di intestazione di Native Client (SQLNCLI. h) con BCP_TYPE_XXX, ad esempio, BCP_TYPE_SQLINT4. Se viene specificato il valore BCP_TYPE_DEFAULT, il provider tenta di utilizzare lo stesso tipo della colonna della tabella o della vista. Per le operazioni di copia bulk di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e in un file quando il **eUserDataType** argomento è BCP_TYPE_SQLDECIMAL o BCP_TYPE_SQLNUMERIC:  
  
-   Se la colonna di origine non è decimal o numeric, vengono utilizzate la precisione e la scala predefinite.  
  
-   Se la colonna di origine è decimal o numeric, vengono utilizzate la precisione e la scala della colonna di origine.  
  
 *cbIndicator*[in]  
 Lunghezza del prefisso per il campo. Il prefisso predefinito è BCP_PREFIX_DEFAULT. Le lunghezze valide per il prefisso sono 0, 1, 2, 4 e 8. Una dimensione del prefisso pari a 8 in genere viene utilizzata per indicare che il campo è Chunked e consente di eseguire in modo efficace la copia bulk di colonne del tipo valore di grandi dimensioni.  
  
 *cbUserData*[in]  
 Lunghezza massima, espressa in byte, dei dati del campo nel file utente, senza includere la lunghezza di un carattere di terminazione o di un indicatore di lunghezza.  
  
 Impostazione **cbUserData** su BCP_LENGTH_NULL indica che tutti i valori nei dati di file i campi sono o dovrebbero essere impostati su NULL. Impostazione **cbUserData** su BCP_LENGTH_VARIABLE indica che il sistema deve determinare la lunghezza dei dati per ogni campo. Per alcuni campi, questo potrebbe indicare che viene generato un indicatore di lunghezza o Null da anteporre ai dati in una copia da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o che l'indicatore è previsto nei dati copiati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] caratteri e i tipi di dati binari, **cbUserData** può essere BCP_LENGTH_VARIABLE, BCP_LENGTH_NULL, 0 o un valore positivo. Se **cbUserData** è BCP_LENGTH_VARIABLE, il sistema utilizza l'indicatore di lunghezza, se presente, o una sequenza di caratteri di terminazione per determinare la lunghezza dei dati. Se vengono specificati sia un indicatore di lunghezza che una sequenza di caratteri di terminazione, la copia bulk utilizza la modalità che comporta la copia del minor numero di dati. Se **cbUserData** è BCP_LENGTH_VARIABLE, i dati di tipo è un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo carattere o binario, e se viene specificata né un indicatore di lunghezza né una sequenza di caratteri di terminazione, il sistema restituisce un messaggio di errore.  
  
 Se **cbUserData** è 0 o un valore positivo, il sistema utilizza **cbUserData** come lunghezza massima dei dati. Tuttavia, se, oltre a un valore positivo **cbUserData**, viene specificato un carattere di terminazione o di un indicatore di lunghezza sequenza, il sistema determina la lunghezza dei dati tramite il metodo che comporta la quantità minima di dati da copiare.  
  
 Il **cbUserData** valore rappresenta il numero di byte di dati. Se i dati di tipo carattere vengono rappresentati come caratteri wide Unicode, un numero positivo **cbUserData** valore del parametro rappresenta il numero di caratteri moltiplicato per la dimensione, in byte, di ogni carattere.  
  
 *pbUserDataTerm*[size_is][in]  
 Sequenza di caratteri di terminazione da utilizzare per il campo. Questo parametro risulta particolarmente utile per i dati di tipo carattere, in quanto tutti gli altri tipi hanno una lunghezza fissa o, nel caso dei dati binari, richiedono un indicatore di lunghezza per registrare in modo accurato il numero di byte presenti.  
  
 Per evitare di terminare i dati estratti o per indicare che i dati di un file utente non devono essere terminati, impostare questo parametro su NULL.  
  
 Se si utilizzano più modalità per definire la lunghezza delle colonne di un file utente, ad esempio un carattere di terminazione e un indicatore di lunghezza o un carattere di terminazione e una lunghezza di colonna massima, la copia bulk sceglierà quella che comporta la copia del minor numero di dati.  
  
 L'API della copia bulk esegue la conversione dei caratteri da Unicode a MBCS in base alle necessità. Verificare attentamente che la stringa di byte del carattere di terminazione e la lunghezza della stringa di byte siano impostate correttamente.  
  
 *cbUserDataTerm*[in]  
 Lunghezza, espressa in byte, della sequenza di caratteri di terminazione da utilizzare per la colonna. Se non sono presenti caratteri di terminazione nei dati o non si desidera includerli, impostare questo valore su 0.  
  
 *idxServerCol*[in]  
 Posizione ordinale della colonna nella tabella del database. Il numero della prima colonna è 1. La posizione ordinale di una colonna è indicata da **IColumnsInfo:: GetColumnInfo** o metodi simili. Se questo valore è 0, la copia bulk ignora il campo nel file di dati.  
  
## <a name="return-code-values"></a>Valori restituiti  
 S_OK  
 Il metodo è riuscito.  
  
 E_FAIL  
 Si è verificato un errore specifico del provider, per informazioni dettagliate, utilizzare il [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) interfaccia.  
  
 E_UNEXPECTED  
 La chiamata al metodo non era prevista. Ad esempio, il [ibcpsession:: BCPInit](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md) (metodo) non è stato chiamato prima di chiamare questo metodo.  
  
 E_INVALIDARG  
 L'argomento non è valido.  
  
 E_OUTOFMEMORY  
 Errore di memoria insufficiente.  
  
## <a name="see-also"></a>Vedere anche  
 [OLE DB IBCPSession &#40; &#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md)   
 [Esecuzione di operazioni di copia bulk](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)  
  
  
