---
title: SQLBindParameter | Documenti Microsoft
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords: SQLBindParameter function
ms.assetid: c302c87a-e7f4-4d2b-a0a7-de42210174ac
caps.latest.revision: "46"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6eceb24668a73eb94224f2c4d6f09f272595a92a
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2018
---
# <a name="sqlbindparameter"></a>SQLBindParameter
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **SQLBindParameter** possibile eliminare il carico di lavoro di conversione dei dati quando viene utilizzata per fornire i dati per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client, con miglioramenti significativi delle prestazioni per i componenti client e server di applicazioni. Un altro vantaggio è costituito da un'inferiore perdita di precisione durante l'inserimento o l'aggiornamento di tipi di dati numerici approssimativi.  
  
> [!NOTE]  
>  Quando si inseriscono **char** e **wchar** viene utilizzati dal tipo di dati in una colonna di tipo image, le dimensioni dei dati passati, anziché le dimensioni dei dati dopo la conversione in un formato binario.  
  
 Se il driver ODBC di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client rileva un errore in un singolo elemento di matrice di una matrice di parametri, continua a eseguire l'istruzione per gli elementi di matrice rimanenti. Se l'applicazione ha associato una matrice di elementi di stato dei parametri per l'istruzione, le righe di parametri che generano errori possono essere determinate dalla matrice.  
  
 Quando si utilizza il driver ODBC di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, specificare SQL_PARAM_INPUT quando si associano parametri di input. Specificare solo SQL_PARAM_OUTPUT o SQL_PARAM_INPUT_OUTPUT quando si associano parametri di stored procedure definiti con la parola chiave OUTPUT.  
  
 [SQLRowCount](../../relational-databases/native-client-odbc-api/sqlrowcount.md) è affidabile con il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client se un elemento di matrice di una matrice di parametri associati provoca un errore nell'esecuzione dell'istruzione. L'attributo SQL_ATTR_PARAMS_PROCESSED_PTR dell'istruzione ODBC indica il numero di righe elaborate prima del verificarsi dell'errore. L'applicazione può quindi attraversare la relativa matrice degli stati dei parametri per individuare il numero di istruzioni eseguite correttamente, se necessario.  
  
## <a name="binding-parameters-for-sql-character-types"></a>Associazione di parametri per i tipi di caratteri SQL  
 Se il tipo di dati SQL passato è un tipo di carattere, *ColumnSize* è la dimensione in caratteri (non byte). Se la lunghezza della stringa di dati in byte è maggiore di 8000, *ColumnSize* deve essere impostato su **SQL_SS_LENGTH_UNLIMITED**, indicando che non vi è alcun limite alle dimensioni del tipo SQL.  
  
 Ad esempio, se il tipo di dati SQL è **SQL_WVARCHAR**, *ColumnSize* non deve essere maggiore di 4000. Se la lunghezza effettiva dei dati è maggiore di 4000, quindi *ColumnSize* deve essere impostato su **SQL_SS_LENGTH_UNLIMITED** in modo che **nvarchar (max)** verrà utilizzato dal driver.  
  
## <a name="sqlbindparameter-and-table-valued-parameters"></a>SQLBindParameter e parametri con valori di tabella  
 Come altri tipi di parametro, i parametri con valori di tabella sono legati da SQLBindParameter.  
  
 Una volta associato un parametro con valori di tabella, vengono associate anche le colonne del parametro. Per associare le colonne, si chiama [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) per impostare SQL_SOPT_SS_PARAM_FOCUS sul numero ordinale del parametro con valori di tabella. Chiamare quindi SQLBindParameter per ogni colonna nel parametro con valori di tabella. Per tornare alle associazioni di parametro di livello principale, impostare SQL_SOPT_SS_PARAM_FOCUS su 0.  
  
 Per informazioni sui mapping dei parametri ai campi di descrizione per i parametri con valori di tabella, vedere [associazione e valori di colonna e i parametri Data Transfer of Table-Valued](../../relational-databases/native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).  
  
 Per ulteriori informazioni sui parametri con valori di tabella, vedere [parametri con valori di tabella &#40; ODBC &#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlbindparameter-support-for-enhanced-date-and-time-features"></a>Supporto di SQLBindParameter per le caratteristiche avanzate di data e ora  
 I valori dei parametri di tipi di data/ora vengono convertiti come descritto in [le conversioni da C a SQL](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md). Si noti che per i parametri di tipo **ora** e **datetimeoffset** deve avere *ValueType* specificato come **SQL_C_DEFAULT** o **SQL_C_BINARY** se utilizzano le strutture corrispondenti (**SQL_SS_TIME2_STRUCT** e **valore SQL_SS_TIMESTAMPOFFSET_STRUCT**) vengono utilizzati.  
  
 Per ulteriori informazioni, vedere [data e ora miglioramenti &#40; ODBC &#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlbindparameter-support-for-large-clr-udts"></a>Supporto di SQLBindParameter per i tipi CLR definiti dall'utente di grandi dimensioni  
 **SQLBindParameter** supporta i tipi CLR grandi dimensioni definito dall'utente (UDT). Per ulteriori informazioni, vedere [Large CLR User-Defined tipi &#40; ODBC &#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Dettagli di implementazione di API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [Funzione SQLBindParameter](http://go.microsoft.com/fwlink/?LinkId=59328)  
  
  
