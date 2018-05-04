---
title: SQLGetDescField e SQLGetDescRec (libreria di cursori) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLGetDescField function [ODBC], Cursor Library
- SQLGetDescRec function [ODBC], Cursor Library
ms.assetid: 1a801f22-6fea-48aa-a723-3187a2ad852b
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4df2bb337eeff7e6d2661fa0809deb5e7cc4a3e1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlgetdescfield-and-sqlgetdescrec-cursor-library"></a>SQLGetDescField e SQLGetDescRec (libreria di cursori)
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 In questo argomento viene illustrato l'utilizzo del **SQLGetDescField** e **SQLGetDescRec** funzioni della libreria di cursori. Per informazioni generali su queste funzioni, vedere [funzione SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md) e [funzione SQLGetDescRec](../../../odbc/reference/syntax/sqlgetdescrec-function.md).  
  
 La libreria di cursori esegue **SQLGetDescRec** per restituire i metadati per le colonne di segnalibro. La libreria di cursori esegue **SQLGetDescField** per restituire gli stessi campi restituiti da **SQLGetDescRec**, che sono SQL_DESC_NAME, SQL_DESC_TYPE, SQL_DESC_DATETIME_INTERVAL_CODE, SQL_DESC_OCTET_ LUNGHEZZA, SQL_DESC_PRECISION, SQL_DESC_SCALE e SQL_DESC_NULLABLE. Per coerenza, **SQLGetDescField** restituisce inoltre SQL_DESC_UNNAMED.  
  
 La libreria di cursori esegue **SQLGetDescField** quando viene chiamato per restituire il valore dei seguenti campi che vengono impostate per l'associazione delle colonne segnalibri: SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR e SQL_DESC_OCTET_LENGTH_PTR, e SQL_DESC_LENGTH.  
  
 La libreria di cursori esegue **SQLGetDescField** quando viene chiamato per restituire il valore del campo SQL_DESC_BIND_OFFSET_PTR, SQL_DESC_BIND_TYPE, SQL_DESC_ROW_ARRAY_SIZE o SQL_DESC_ROW_STATUS_PTR. Questi campi possono essere restituiti per ogni riga, non solo la riga del segnalibro.  
  
 Se un'applicazione chiama **SQLGetDescField** per restituire il valore di qualsiasi campo diverse da quelle indicate in precedenza, la libreria di cursori passa la chiamata al driver.
