---
title: SQLPutData | Documenti Microsoft
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
helpviewer_keywords: SQLPutData function
ms.assetid: d39aaa5b-7fbc-4315-a7f2-5a7787e04f25
caps.latest.revision: "49"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2a7a7599ab507710f900a2dba3b0034cbad52008
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="sqlputdata"></a>SQLPutData
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Le restrizioni seguenti si applicano quando si utilizza SQLPutData per inviare più di 65.535 byte di dati (per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versione 4.21 a) o 400 KB di dati (per SQL Server versione 6.0 e versioni successive) per un SQL_LONGVARCHAR (**testo**), SQL_WLONGVARCHAR (**ntext**) o SQL_LONGVARBINARY (**immagine**) colonna:  
  
-   Il parametro di riferimento può essere il *insert_value* in un'istruzione INSERT.  
  
-   Il parametro di riferimento può essere un *espressione* nella clausola SET di un'istruzione UPDATE.  
  
 Annullamento di una sequenza di chiamate SQLPutData che forniscono dati in blocchi a un server che esegue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provoca un aggiornamento parziale del valore della colonna quando si utilizza una versione 6.5 o precedenti. Il **testo**, **ntext**, o **immagine** colonna di riferimento quando è stato chiamato SQLCancel è impostata su un valore di segnaposto intermedio.  
  
> [!NOTE]  
>  Il driver ODBC di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client non supporta la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 e versioni precedenti.  
  
## <a name="diagnostics"></a>Diagnostica  
 È presente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQLSTATE specifico di Native Client per SQLPutData:  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|22026|Lunghezza dei dati non corrispondente.|Se la lunghezza dei dati in byte da inviare è stata specificata da un'applicazione, ad esempio con SQL_LEN_DATA_AT_EXEC (*n*) in cui  *n*  è maggiore di 0, il numero totale di byte fornito dall'applicazione tramite SQLPutData devono corrispondere alla lunghezza specificata.|  
  
## <a name="sqlputdata-and-table-valued-parameters"></a>SQLPutData e parametri con valori di tabella  
 SQLPutData è utilizzato da un'applicazione quando si utilizza l'associazione variabile di righe con parametri con valori di tabella. Il *StrLen_Or_Ind* parametro indica che è pronto per il driver raccogliere dati per la riga o le righe di dati del parametro con valori di tabella o che non le altre righe disponibili:  
  
-   Un valore maggiore di 0 indica che è disponibile il set di valori di riga successivo.  
  
-   Il valore 0 indica che non sono disponibili altre righe da inviare.  
  
-   Qualsiasi valore minore di 0 rappresenta un errore e restituisce un record di diagnostica registrato con SQLState HY090 e il messaggio "Lunghezza di stringa o di buffer non valida".  
  
 Il *DataPtr* parametro viene ignorato, ma deve essere impostata su un valore non NULL. Per ulteriori informazioni, vedere la sezione sull'associazione di righe TVP variabile in [associazione e valori di colonna e i parametri Data Transfer of Table-Valued](../../relational-databases/native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).  
  
 Se *StrLen_Or_Ind* ha un valore diverso da SQL_DEFAULT_PARAM o un numero compreso tra 0 e SQL_PARAMSET_SIZE (vale a dire il *ColumnSize* parametro di SQLBindParameter), è un errore. A causa di questo errore, SQLPutData restituisce SQL_ERROR: SQLSTATE=HY090, "Lunghezza di stringa o di buffer non valida".  
  
 Per ulteriori informazioni sui parametri con valori di tabella, vedere [parametri con valori di tabella &#40; ODBC &#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlputdata-support-for-enhanced-date-and-time-features"></a>Supporto di SQLPutData per le caratteristiche avanzate di data e ora  
 I valori dei parametri di tipi di data/ora vengono convertiti come descritto in [le conversioni da C a SQL](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md).  
  
 Per ulteriori informazioni, vedere [data e ora miglioramenti &#40; ODBC &#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlputdata-support-for-large-clr-udts"></a>Supporto di SQLPutData per i tipi CLR definiti dall'utente di grandi dimensioni  
 **SQLPutData** supporta i tipi CLR grandi dimensioni definito dall'utente (UDT). Per ulteriori informazioni, vedere [Large CLR User-Defined tipi &#40; ODBC &#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Vedere anche  
 [SQLPutData-funzione](http://go.microsoft.com/fwlink/?LinkId=59365)   
 [Dettagli di implementazione dell'API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
