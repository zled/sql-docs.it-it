---
title: SQLSetDescField e SQLSetDescRec (libreria di cursori) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLSetDescField function [ODBC], Cursor Library
- SQLSetDescRec function [ODBC], Cursor Library
ms.assetid: 4ccff067-85cd-4bfa-a6cd-7f28051fb5b9
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 04c3fd1c3c64140b7669cdeeb35937498249ac66
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32910276"
---
# <a name="sqlsetdescfield-and-sqlsetdescrec-cursor-library"></a>SQLSetDescField e SQLSetDescRec (libreria di cursori)
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 In questo argomento viene illustrato l'utilizzo del **SQLSetDescField** e **SQLSetDescRec** funzioni della libreria di cursori. Per informazioni generali su queste funzioni, vedere [funzione SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) e [funzione SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).  
  
 La libreria di cursori esegue **SQLSetDescField** quando viene chiamato per restituire il valore dei campi impostata per le colonne di segnalibro:  
  
 SQL_DESC_DATA_PTR  
  
 SQL_DESC_INDICATOR_PTR  
  
 SQL_DESC_OCTET_LENGTH_PTR  
  
 SQL_DESC_LENGTH  
  
 SQL_DESC_OCTET_LENGTH  
  
 SQL_DESC_DATETIME_INTERVAL_CODE  
  
 SQL_DESC_SCALE  
  
 SQL_DESC_PRECISION  
  
 SQL_DESC_TYPE  
  
 SQL_DESC_NAME  
  
 SQL_DESC_UNNAMED  
  
 SQL_DESC_NULLABLE  
  
 La libreria di cursori esegue chiamate a **SQLSetDescRec** per una colonna del segnalibro.  
  
 Quando si lavora con un ODBC 2. *x* driver, la libreria di cursori restituisce SQLSTATE HY090 (stringa di lunghezza o non valida del buffer) quando **SQLSetDescField** o **SQLSetDescRec** viene chiamato per impostare il SQL_DESC_OCTET_ Campo di lunghezza per il record di segnalibro di un ARD su un valore non è uguale a 4. Quando si lavora con un'applicazione ODBC 3*x* driver, la libreria di cursori consente il buffer di qualsiasi dimensione.  
  
 La libreria di cursori esegue **SQLSetDescField** quando viene chiamato per restituire il valore del campo SQL_DESC_BIND_OFFSET_PTR, SQL_DESC_BIND_TYPE, SQL_DESC_ROW_ARRAY_SIZE o SQL_DESC_ROW_STATUS_PTR. Questi campi possono essere restituiti per ogni riga, non solo la riga del segnalibro.  
  
 La libreria di cursori non esegue **SQLSetDescField** per modificare qualsiasi campo di descrizione diverso da campi indicato in precedenza. Se un'applicazione chiama **SQLSetDescField** per impostare qualsiasi altro campo durante il caricamento della libreria di cursori, la chiamata viene passata tramite il driver.  
  
 La libreria di cursori supporta la modifica in modo dinamico i campi SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR e SQL_DESC_OCTET_LENGTH_PTR di qualsiasi riga di un descrittore della riga di applicazione (dopo una chiamata a **SQLExtendedFetch**, **SQLFetch**, o **SQLFetchScroll**). Il campo SQL_DESC_OCTET_LENGTH_PTR può essere modificato in un puntatore null solo per disassociare il buffer di lunghezza per una colonna.  
  
 La libreria di cursori non supporta la modifica il campo SQL_DESC_BIND_TYPE un'APD o ARD quando un cursore è aperto. Il campo SQL_DESC_BIND_TYPE può essere modificato solo dopo il cursore è chiuso e prima dell'apertura di un nuovo cursore. I campi di descrizione solo che la libreria di cursori supporta la modifica di quando è aperto un cursore sono SQL_DESC_ARRAY_STATUS_PTR, SQL_DESC_BIND_OFFSET_PTR, SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, SQL_DESC_OCTET_LENGTH_PTR e SQL_DESC_ROWS_PROCESSED_ PTR.  
  
 La libreria di cursori non supporta la modifica il campo SQL_DESC_COUNT del ARD dopo **SQLExtendedFetch** o **SQLFetchScroll** è stato chiamato e prima che il cursore è stato chiuso.
