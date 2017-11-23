---
title: Preparare ed eseguire un'istruzione (ODBC) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-how-to
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- statement execution
- statement preparation
ms.assetid: 0adecc63-4da5-486c-bc48-09a004a2fae6
caps.latest.revision: "21"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dd945fdf098773bea47fa6a0f2d395e7841a0459
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="prepare-and-execute-a-statement-odbc"></a>Preparare ed eseguire un'istruzione (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

    
### <a name="to-prepare-a-statement-once-and-then-execute-it-multiple-times"></a>Per preparare un'istruzione da eseguire più volte  
  
1.  Chiamare [funzione SQLPrepare](http://go.microsoft.com/fwlink/?LinkId=59360) per preparare l'istruzione.  
  
2.  È possibile chiamare [SQLNumParams](http://go.microsoft.com/fwlink/?LinkId=58404) per determinare il numero di parametri nell'istruzione preparata.  
  
3.  Per ogni parametro dell'istruzione preparata è possibile:  
  
    -   Chiamare [SQLDescribeParam](../../../relational-databases/native-client-odbc-api/sqldescribeparam.md) per ottenere informazioni sui parametri.  
  
    -   Associare ogni parametro a una variabile di programma utilizzando [SQLBindParameter](../../../relational-databases/native-client-odbc-api/sqlbindparameter.md). Configurare i parametri data-at-execution.  
  
4.  Per ogni esecuzione di un'istruzione preparata:  
  
    -   Se nell'istruzione sono inclusi marcatori di parametro, inserire i valori dei dati nel buffer di parametri associato.  
  
    -   Chiamare [SQLExecute](http://go.microsoft.com/fwlink/?LinkId=58400) per eseguire l'istruzione preparata.  
  
    -   Se si utilizzano parametri di input data-at-execution, [SQLExecute](http://go.microsoft.com/fwlink/?LinkId=58400) restituisce SQL_NEED_DATA. Inviare i dati in blocchi utilizzando [SQLParamData](http://go.microsoft.com/fwlink/?LinkId=58405) e [SQLPutData](../../../relational-databases/native-client-odbc-api/sqlputdata.md).  
  
### <a name="to-prepare-a-statement-with-column-wise-parameter-binding"></a>Per preparare un'istruzione con associazione di parametri a livello di colonna  
  
1.  Chiamare [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) per impostare gli attributi seguenti:  
  
    -   Impostare SQL_ATTR_PARAMSET_SIZE sul numero di set (S) di parametri.  
  
    -   Impostare SQL_ATTR_PARAM_BIND_TYPE su SQL_PARAMETER_BIND_BY_COLUMN.  
  
    -   Impostare l'attributo SQL_ATTR_PARAMS_PROCESSED_PTR in modo che punti a una variabile SQLUINTEGER che contenga il numero di parametri elaborati.  
  
    -   Impostare SQL_ATTR_PARAMS_STATUS_PTR in modo che punti a una matrice [S] di variabili SQLUSSMALLINT che contenga gli indicatori di stato dei parametri.  
  
2.  Chiamare la funzione SQLPrepare per preparare l'istruzione.  
  
3.  È possibile chiamare [SQLNumParams](http://go.microsoft.com/fwlink/?LinkId=58404) per determinare il numero di parametri nell'istruzione preparata.  
  
4.  Per ogni parametro nell'istruzione preparata, è possibile chiamare la funzione SQLDescribeParam per ottenere informazioni sul parametro.  
  
5.  Per ogni marcatore di parametro:  
  
    -   Allocare una matrice di buffer di S parametri per archiviare i valori dei dati.  
  
    -   Allocare una matrice di buffer di S parametri per archiviare le lunghezze dei dati.  
  
    -   Chiamare la funzione SQLBindParameter per associare le matrici di lunghezza parametro valore e i dati del dati al parametro dell'istruzione.  
  
    -   Se il parametro è un testo data-at-execution o un parametro di immagine, configurarlo.  
  
    -   Se vengono utilizzati parametri data-at-execution, configurarli.  
  
6.  Per ogni esecuzione di un'istruzione preparata:  
  
    -   Inserire le S lunghezze e gli S valori di dati nelle matrici di parametri associate.  
  
    -   Chiamare la funzione SQLExecute per eseguire l'istruzione preparata.  
  
    -   Se si utilizzano parametri di input data-at-execution, SQLExecute restituisce SQL_NEED_DATA. Inviare i dati in blocchi utilizzando SQLParamData e SQLPutData.  
  
### <a name="to-prepare-a-statement-with-row-wise-bound-parameters"></a>Per preparare un'istruzione con associazione di parametri a livello di riga  
  
1.  Allocare una matrice [S] di strutture, dove S è il numero di set di parametri. Nella struttura è presente un elemento per ogni parametro e ogni elemento è costituito da due parti:  
  
    -   La prima parte è una variabile del tipo di dati appropriato che contiene i dati dei parametri.  
  
    -   La seconda parte è una variabile SQLINTEGER che deve contenere l'indicatore di stato.  
  
2.  Chiamare [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) per impostare gli attributi seguenti:  
  
    -   Impostare SQL_ATTR_PARAMSET_SIZE sul numero di set (S) di parametri.  
  
    -   Impostare SQL_ATTR_PARAM_BIND_TYPE sulla dimensione della struttura allocata nel Passaggio 1.  
  
    -   Impostare l'attributo SQL_ATTR_PARAMS_PROCESSED_PTR in modo che punti a una variabile SQLUINTEGER che contenga il numero di parametri elaborati.  
  
    -   Impostare SQL_ATTR_PARAMS_STATUS_PTR in modo che punti a una matrice [S] di variabili SQLUSSMALLINT che contenga gli indicatori di stato dei parametri.  
  
3.  Chiamare la funzione SQLPrepare per preparare l'istruzione.  
  
4.  Per ogni marcatore di parametro, chiamare la funzione SQLBindParameter per puntare il parametro e dei valori lunghezza puntatore ai dati alle relative variabili nel primo elemento della matrice di strutture allocate nel passaggio 1. Se il parametro è di tipo data-at-execution, configurarlo.  
  
5.  Per ogni esecuzione di un'istruzione preparata:  
  
    -   Inserire i valori dei dati nella matrice di buffer dei parametri associati.  
  
    -   Chiamare la funzione SQLExecute per eseguire l'istruzione preparata. Il driver esegue in modo efficace l'istruzione SQL S volte, una volta per ogni set di parametri.  
  
    -   Se si utilizzano parametri di input data-at-execution, SQLExecute restituisce SQL_NEED_DATA. Inviare i dati in blocchi utilizzando SQLParamData e SQLPutData.  
  
## <a name="see-also"></a>Vedere anche  
 [L'esecuzione di query procedure &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-how-to/execute-queries/executing-queries-how-to-topics-odbc.md)  
  
  