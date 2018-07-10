---
title: 'Ibcpsession:: BCPInit (OLE DB) | Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IBCPSession::BCPInit (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPInit method
ms.assetid: 583096d7-da34-49be-87fd-31210aac81aa
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 653cf3fc07cbdf9178c9554dbc602671607b9f3b
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37430730"
---
# <a name="ibcpsessionbcpinit-ole-db"></a>IBCPSession::BCPInit (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Inizializza la struttura della copia bulk, esegue alcune operazioni di controllo degli errori, verifica che i dati e i nomi dei file di formato siano corretti, quindi li apre.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
HRESULT BCPInit(   
      const wchar_t *pwszTable,  
      const wchar_t *pwszDataFile,  
      const wchar_t *pwszErrorFile,  
      int eDirection);  
```  
  
## <a name="remarks"></a>Note  
 Il **BCPInit** metodo deve essere chiamato prima di qualsiasi altro metodo di copia bulk. Il **BCPInit** metodo esegue le inizializzazioni necessarie per una copia bulk dei dati tra la workstation e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Il **BCPInit** metodo esamina la struttura della tabella di database origine o destinazione, non il file di dati. Specifica i valori relativi al formato dei dati per il file di dati in base a ogni colonna nella vista o nella tabella di database o nel set di risultati SELECT. Questa specifica include il tipo di dati di ogni colonna, la presenza o meno di un indicatore di lunghezza o Null e di stringhe di byte con carattere di terminazione nei dati e la larghezza dei tipi di dati a lunghezza fissa. Il **BCPInit** metodo imposta questi valori come indicato di seguito:  
  
-   Il tipo di dati specificato è quello della colonna della vista o della tabella di database oppure del set di risultati SELECT. Il tipo di dati viene enumerato in base [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] specificati tipi di dati nativi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] file di intestazione di Native Client (SQLNCLI. h). I relativi valori utilizzano il modello BCP_TYPE_XXX. I dati vengono rappresentati nel relativo formato elettronico, ovvero i dati di una colonna di un tipo di dati integer vengono rappresentati da una sequenza a quattro byte, di tipo big o little endian a seconda del computer con il quale è stato creato il file di dati.  
  
-   Se un tipo di dati del database ha una lunghezza fissa, anche i dati del file di dati presenteranno una lunghezza fissa. I metodi di copia bulk che elaborano i dati (ad esempio, [ibcpsession:: BCPExec](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpexec-ole-db.md)) analizzano le righe di dati prevedendo che la lunghezza dei dati nel file di dati sia identica alla lunghezza dei dati specificata nella tabella di database, visualizzazione o selezionare la colonna elenco. I dati di una colonna del database definiti come `char(13)` devono, ad esempio, essere rappresentati da 13 caratteri per ogni riga di dati nel file. I dati a lunghezza fissa possono essere preceduti da un indicatore Null se la colonna del database consente valori Null.  
  
-   Quando si copiano dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il file di dati deve includere dati per ogni colonna nella tabella di database. Quando si copiano dati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], i dati di tutte le colonne della vista o della tabella di database o del set di risultati SELECT vengono copiati nel file di dati.  
  
-   Quando si copiano dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la posizione ordinale di una colonna nel file di dati deve essere identica alla posizione ordinale della colonna nella tabella di database. Quando si copiano dati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il **BCPExec** metodo inserisce dati in base alla posizione ordinale della colonna nella tabella di database.  
  
-   Se un tipo di dati del database ha una lunghezza variabile, ad esempio `varbinary(22)`, o se una colonna del database può contenere valori Null, i dati nel file di dati sono preceduti da un indicatore di lunghezza o Null. La larghezza dell'indicatore varia in base al tipo di dati e alla versione della copia bulk. Il [ibcpsession:: Bcpcontrol](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md) opzione BCP_OPTION_FILEFMT del metodo garantisce la compatibilità tra i file di dati di copia bulk precedenti e i server che eseguono versioni successive di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] indicando quando la larghezza degli indicatori nel i dati sono inferiore a quella prevista.  
  
> [!NOTE]  
>  Per modificare i valori di formato dati specificati per un file di dati, usare il [ibcpsession:: BCPColumns](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md) e [ibcpsession:: BCPColFmt](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md) metodi.  
  
 Copie di massa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può essere ottimizzata per le tabelle che non contengono indici impostando l'opzione di database **select in / bulkcopy**.  
  
## <a name="arguments"></a>Argomenti  
 *pwszTable*[in]  
 Nome della tabella di database per la copia interna o esterna. Il nome può includere il nome del database o del proprietario, ad esempio "pubs.username.titles", "pubs..titles", "username.titles".  
  
 Se l'argomento eDirection è impostato su BCP_DIRECTION_OUT, l'argomento pwszTable può essere il nome di una vista di database.  
  
 Se l'argomento eDirection è impostato su BCP_DIRECTION_OUT e viene specificata un'istruzione SELECT utilizzando il **BCPControl** metodo prima il **BCPExec** viene chiamato il metodo di *pwszTable*argomento deve essere impostato su NULL.  
  
 *pwszDataFile*[in]  
 Nome del file utente per la copia interna o esterna.  
  
 *pwszErrorFile*[in]  
 Nome del file degli errori in cui inserire messaggi di stato, messaggi di errore e copie delle righe che non è stato possibile copiare da un file utente in una tabella. Se il *pwszErrorFile* argomento è impostato su NULL, non viene usato alcun file degli errori.  
  
 *eDirection*[in]  
 Direzione dell'operazione di copia, BCP_DIRECTION_IN o BCP_DIRECTION _OUT. BCP_DIRECTION _IN indica una copia da un file utente in una tabella di database e BCP_DIRECTION _OUT indica una copia da una tabella di database in un file utente.  
  
## <a name="return-code-values"></a>Valori restituiti  
 S_OK  
 Il metodo è riuscito.  
  
 E_FAIL  
 Si è verificato un errore specifico del provider' per informazioni dettagliate, usare il [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) interfaccia.  
  
 E_OUTOFMEMORY  
 Errore di memoria insufficiente.  
  
 E_INVALIDARG  
 Uno o più argomenti non sono stati specificati correttamente, ad esempio è stato immesso un nome file non valido.  
  
## <a name="see-also"></a>Vedere anche  
 [IBCPSession &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md)   
 [Esecuzione di operazioni di copia bulk](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)  
  
  
