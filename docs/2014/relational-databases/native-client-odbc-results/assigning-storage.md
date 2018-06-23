---
title: Assegnazione di archiviazione | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- column-wise binding [ODBC]
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- SQLBindCol function
- storing data [ODBC]
- result sets [ODBC], storage
- SQL Server Native Client ODBC driver, data storage
- row-wise binding
- binding result sets [SQL Server Native Client]
- array binding
ms.assetid: 11c81955-5300-495f-925f-9256f2587b58
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: eb77a63cb3522d86b40742780e44a141dc0a6c15
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156218"
---
# <a name="assigning-storage"></a>Assegnazione di archiviazione
  In un'applicazione è possibile assegnare l'archiviazione per i risultati prima o dopo l'esecuzione di un'istruzione SQL. Se la preparazione o l'esecuzione dell'istruzione SQL avviene prima, è possibile richiedere informazioni sul set di risultati prima di archiviare i risultati. Se ad esempio il set di risultati non è noto, è necessario recuperare il numero di colonne prima dell'assegnazione dell'archiviazione.  
  
 Per associare l'archiviazione per una colonna di dati, un'applicazione chiama [SQLBindCol](../native-client-odbc-api/sqlbindcol.md)e lo passa a:  
  
-   Tipo di dati nel quale devono essere convertiti i dati.  
  
-   Indirizzo di un buffer di output per i dati.  
  
     L'applicazione deve allocare questo buffer, e deve essere di dimensioni sufficienti a contenere i dati nel formato nel quale vengono convertiti.  
  
-   Lunghezza del buffer di output.  
  
     Questo valore viene ignorato se i dati restituiti hanno una larghezza fissa in C, ad esempio un numero intero, un numero reale o una struttura di data.  
  
-   Indirizzo di un buffer di archiviazione nel quale restituire il numero di byte dei dati disponibili.  
  
 Un'applicazione può inoltre associare colonne del set di risultati a matrici di variabili di programma per consentire il supporto del recupero di righe in blocchi. Sono disponibili due tipi diversi di associazione di matrici:  
  
-   L'associazione a livello di colonna è completa quando ogni colonna è associata alla rispettiva matrice di variabili.  
  
     L'associazione per colonna viene specificata chiamando [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) con *attributo* impostato su SQL_ATTR_ROW_BIND_TYPE e *ValuePtr* impostato su SQL_BIND_BY_COLUMN. Tutte le matrici devono avere lo stesso numero di elementi.  
  
-   L'associazione a livello di riga è completa quando tutti i parametri dell'istruzione SQL vengono associati come un'unità a una matrice di strutture contenenti le singole variabili per i parametri.  
  
     L'associazione viene specificata chiamando **SQLSetStmtAttr** con *attributo* impostato su SQL_ATTR_ROW_BIND_TYPE e *ValuePtr* impostato sulla dimensione dell'azienda struttura il le colonne impostate variabili che riceveranno il risultato.  
  
 Viene inoltre impostato SQL_ATTR_ROW_ARRAY_SIZE sul numero di elementi presenti nelle matrici di colonne o di righe e vengono impostati SQL_ATTR_ROW_STATUS_PTR e SQL_ATTR_ROWS_FETCHED_PTR.  
  
## <a name="see-also"></a>Vedere anche  
 [L'elaborazione dei risultati &#40;ODBC&#41;](processing-results-odbc.md)  
  
  