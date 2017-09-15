---
title: Funzioni API di livello 2, il Driver ODBC per Oracle | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC level 2 API functions [ODBC]
- functions [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], functions
- ODBC API functions [ODBC]
- API functions [ODBC]
- level 2 API functions [ODBC]
ms.assetid: d9f49520-72d7-4234-8635-260d0ce4199c
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: eb35e0e2dde90261e913ffd9ba3dc28e5859e012
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="level-2-api-functions-odbc-driver-for-oracle"></a>Funzioni API di livello 2 (Driver ODBC per Oracle)
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. In alternativa, utilizzare il driver ODBC fornito da Oracle.  
  
 Funzioni a questo livello forniscono la conformità di interfaccia di livello 1 oltre a funzionalità aggiuntive quali il supporto per l'esecuzione asincrona delle funzioni ODBC segnalibri e i parametri dinamici.  
  
|Funzione API|Note|  
|------------------|-----------|  
|**SQLBindParameter**|Associa un buffer con un marcatore di parametro in un'istruzione SQL.|  
|**SQLBrowseConnect**|Restituisce i livelli successivi di attributi e valori di attributo.|  
|**SQLDataSources**|Elenca i nomi delle origini dati. Implementato da Gestione Driver.|  
|**SQLDescribeParam**|Restituisce la descrizione di un marcatore di parametro associato a un'istruzione SQL preparata.<br /><br /> Restituisce una stima del quale il parametro è, in base all'analisi dell'istruzione. Se non è possibile determinare il tipo di parametro, con lunghezza 2000 SQL_VARCHAR.|  
|**SQLDrivers**|Implementato da Gestione Driver.|  
|**SQLExtendedFetch.**|Simile a **SQLFetch** ma restituisce più righe utilizzando una matrice per ogni colonna. Il set di risultati forward-scorrevole e può essere effettuato con le versioni precedenti scorrevole se il cursore è definito come non forward-only, statici. Per i cursori forward-only con l'associazione di colonna predefinito, vengono recuperati i dati della colonna dei set di dati più grande rispetto all'attributo di connessione BUFFERSIZE direttamente nel buffer di dati. Non supporta segnalibri a lunghezza variabile e non supporta il recupero di un set di righe a un offset specifico (diverso da 0) da un segnalibro.|  
|**SQLForeignKeys**|Restituisce un elenco di chiavi esterne in una singola tabella o un elenco di chiavi esterne in altre tabelle che fanno riferimento a una singola tabella.|  
|**SQLMoreResults**|Determina se più risultati sono in sospeso su un handle di istruzione, hstmt, contenente le istruzioni SELECT, UPDATE, INSERT o DELETE e in tal caso, inizializza l'elaborazione di tali risultati.<br /><br /> Oracle supporta più set di risultati solo dalle stored procedure, quando si usa sequenze di escape {resultset}.|  
|**SQLNativeSql**|Per informazioni sull'utilizzo, vedere [la restituzione di parametri di matrice dalle Stored procedure](../../odbc/microsoft/returning-array-parameters-from-stored-procedures.md).|  
|**SQLNumParams**|Restituisce il numero di parametri in un'istruzione SQL. Il numero di parametri deve essere uguale il numero di punti interrogativi nell'istruzione SQL passata al **SQLPrepare**.|  
|**SQLPrimaryKeys**|Restituisce i nomi delle colonne che costituiscono la chiave primaria per una tabella.|  
|**SQLProcedureColumns**|Restituisce un elenco di parametri di input e output, il valore restituito, le colonne nel set di risultati di una sola stored procedure e due colonne aggiuntive, OVERLOAD e ORDINAL_POSITION. OVERLOAD è l'OVERLOAD di colonna dalla tabella ALL_ARGUMENTS della vista di dizionario di dati Oracle. ORDINAL_POSITION è la colonna di sequenza della tabella ALL_ARGUMENTS della vista di dizionario di dati Oracle. Per le procedure in pacchetto, nella colonna nome della stored PROCEDURE si *packagename.procedurename* formato. Non restituisce le colonne di routine di un sinonimo creato che fa riferimento a una procedura o funzione.|  
|**SQLProcedures**|Restituisce un elenco di procedure nell'origine dati. Per le procedure in pacchetto, nella colonna nome della stored PROCEDURE si *packagename.procedurename* formato.<br /><br /> Poiché Oracle non fornisce un modo per distinguere le procedure in pacchetto da funzioni incluse nel pacchetto, il driver restituisce SQL_PT_UNKNOWN per la colonna PROCEDURE_TYPE.|  
|**SQLSetPos**|Imposta la posizione del cursore in un set di righe. È possibile utilizzare **SQLSetPos** con **SQLGetData** per recuperare righe da colonne non associate dopo posizionando il cursore in una riga specifica nel set di righe. Righe aggiunte per il set di risultati utilizzando *fOption* SQL_ADD vengono aggiunti dopo l'ultima riga nel set di risultati.|  
|**SQLSetScrollOptions**|Imposta le opzioni che controllano il comportamento dei cursori associata a un handle di istruzione, hstmt. Per informazioni dettagliate, vedere [combinazioni di concorrenza e il tipo di cursore](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md).|
