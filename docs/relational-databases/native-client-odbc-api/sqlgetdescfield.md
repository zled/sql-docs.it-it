---
title: SQLGetDescField | Microsoft Docs
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
helpviewer_keywords: SQLGetDescField function
ms.assetid: 3e59a37a-28ee-4c91-8968-7fe3b966739d
caps.latest.revision: "52"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ab87d6c5626424a2f6491ed6acec3b3f83fcbfe6
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2018
---
# <a name="sqlgetdescfield"></a>SQLGetDescField
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client espone campi di descrizione specifici del driver per il descrittore riga di implementazione (IRD) solo. Nell'IRD ai, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] campi di descrizione vengono fatto riferimento tramite attributi di colonna specifici del driver. Per informazioni su un elenco completo dei campi di descrizione specifici del driver disponibili, vedere [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md).  
  
 I campi di descrizione che contengono stringhe dell'identificatore di colonna sono spesso stringhe di lunghezza zero. Tutti i valori dei campi di descrizione specifici di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono di sola lettura.  
  
 Ad esempio gli attributi recuperati con SQLColAttribute, i campi di descrizione che gli attributi a livello di riga di report (ad esempio SQL_CA_SS_COMPUTE_ID) vengono indicati per tutte le colonne nel set di risultati.  
  
## <a name="sqlgetdescfield-and-table-valued-parameters"></a>SQLGetDescField e parametri con valori di tabella  
 SQLGetDescField può essere utilizzato per ottenere i valori per gli attributi estesi dei parametri con valori di tabella e le colonne di parametri con valori di tabella. Per ulteriori informazioni sui parametri con valori di tabella, vedere [parametri con valori di tabella &#40; ODBC &#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlgetdescfield-support-for-enhanced-date-and-time-features"></a>Supporto di SQLGetDescField per le caratteristiche avanzate di data e ora  
 Per informazioni sui campi di descrizione disponibili con i tipi di data/ora di nuovo, vedere [metadati per parametri e risultato](../../relational-databases/native-client-odbc-date-time/metadata-parameter-and-result.md).  
  
 Per ulteriori informazioni, vedere [data e ora miglioramenti &#40; ODBC &#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
 A partire da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], può restituire SQLGetDescField **SQL_C_SS_TIME2** (per **ora** tipi) o **SQL_C_SS_TIMESTAMPOFFSET** (per  **DateTimeOffset**) anziché **SQL_C_BINARY**, se l'applicazione utilizza ODBC 3.8.  
  
## <a name="sqlgetdescfield-support-for-large-clr-udts"></a>Supporto di SQLGetDescField per tipi definiti dall'utente CLR di grandi dimensioni  
 **SQLGetDescField** supporta i tipi CLR grandi dimensioni definito dall'utente (UDT). Per ulteriori informazioni, vedere [Large CLR User-Defined tipi &#40; ODBC &#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="sqlgetdescfield-support-for-sparse-columns"></a>Supporto di SQLGetDescField per colonne di tipo sparse  
 SQLGetDescField può essere usato per eseguire una query sul nuovo campo IRD, sql_ca_ss_is_column_set, per determinare se una colonna è un **column_set** colonna.  
  
 Per ulteriori informazioni, vedere [supporto per colonne di tipo Sparse &#40; ODBC &#41;](../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md).  
  
## <a name="example"></a>Esempio  
  
```  
typedef struct tagCOMPUTEBYLIST  
    {  
    SQLSMALLINT nBys;  
    SQLSMALLINT aByList[1];  
    } COMPUTEBYLIST;  
typedef COMPUTEBYLIST* PCOMPUTEBYLIST;   
  
SQLHDESC    hIRD;   
SQLINTEGER  cbIRD;   
SQLINTEGER  nSet = 0;   
  
// . . .  
// Execute a statement that contains a COMPUTE clause,  
//  then get the descriptor handle of the IRD and  
//  get some IRD values.  
  
SQLGetStmtAttr(g_hStmt, SQL_ATTR_IMP_ROW_DESC,  
    (SQLPOINTER) &hIRD, sizeof(SQLHDESC), &cbIRD);  
  
// For statement-wide column attributes, any  
//  descriptor record will do. You know that 1 exists,  
//  so use it.  
SQLGetDescField(hIRD, 1, SQL_CA_SS_NUM_COMPUTES,  
    (SQLPOINTER) &nComputes, SQL_IS_INTEGER, &cbIRD);  
  
if (nSet == 0)  
    {  
    SQLINTEGER      nOrderID;  
  
    printf_s("Normal result set.\n");  
  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        SQLGetDescField(hIRD, nCol+1,  
            SQL_CA_SS_COLUMN_ORDER,  
            (SQLPOINTER) &nOrderID, SQL_IS_INTEGER,  
            &cbIRD);  
  
        if (nOrderID != 0)  
            {  
            printf_s("Col in ORDER BY, pos: %ld",  
                nOrderID);  
            }  
            printf_s("\n");  
        }  
  
    printf_s("\n");  
    }  
else  
    {  
    PCOMPUTEBYLIST  pByList;  
    SQLSMALLINT     nBy;  
    SQLINTEGER      nColID;  
  
    printf_s("Computed result set number: %lu\n",  
        nSet);  
  
    SQLGetDescField(hIRD, 1, SQL_CA_SS_COMPUTE_BYLIST,  
        (SQLPOINTER) &pByList, SQL_IS_INTEGER,  
        &cbIRD);  
  
    if (pByList != NULL)  
        {  
        printf_s("Clause ordered by columns: ");  
        for (nBy = 0; nBy < pByList->nBys; )  
            {  
            printf_s("%u", pByList->aByList[nBy]);  
            nBy++;  
  
            if (nBy == pByList->nBys)  
                {  
                printf_s("\n");  
                }  
            else  
                {  
                printf_s(", ");  
                }  
            }  
        }  
    else  
        {  
        printf_s("Compute clause set not ordered.\n");  
        }  
  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        SQLGetDescField(hIRD, nCol+1,  
            SQL_CA_SS_COLUMN_ID, (SQLPOINTER) &nColID,  
            SQL_IS_INTEGER, &cbIRD);  
        printf_s("ColumnID: %lu, nColID);  
        }  
    printf_s("\n");  
    }  
  
if (SQLMoreResults(g_hStmt) == SQL_SUCCESS)  
    {  
    // Determine the result set indicator.  
    SQLGetDescField(hIRD, 1, SQL_CA_SS_COMPUTE_ID,  
        (SQLPOINTER) &nSet, SQL_IS_INTEGER, &cbIRD);  
    }  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione SQLGetDescField](http://go.microsoft.com/fwlink/?LinkId=59351)   
 [Dettagli di implementazione di API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
