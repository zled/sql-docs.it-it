---
title: SQLGetInfo (libreria di cursori) | Documenti Microsoft
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
- SQLGetInfo function [ODBC], Cursor Library
ms.assetid: 1b4d220d-2c07-4f56-987e-36813bb1a6ce
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c8a3cfcc70ddb26403b73895d71cafc923b8a655
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlgetinfo-cursor-library"></a>SQLGetInfo (libreria di cursori)
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 In questo argomento viene illustrato l'utilizzo del **SQLGetInfo** funzione nella libreria di cursori. Per informazioni generali su **SQLGetInfo**, vedere [funzione SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md).  
  
 La libreria di cursori vengono restituiti valori per i seguenti valori *InfoType* (&#124; rappresenta un'operazione OR), per tutti gli altri valori di *InfoType*, chiama **SQLGetInfo** nel driver.  
  
|*InfoType*|Valore restituito|  
|----------------|--------------------|  
|SQL_BOOKMARK_PERSISTENCE|SQL_BP_SCROLL|  
|SQL_DYNAMIC_CURSOR_ATTRIBUTES1|0|  
|SQL_DYNAMIC_CURSOR_ATTRIBUTES2|0|  
|SQL_FETCH_DIRECTION [1]|SQL_FD_FETCH_ABSOLUTE &AMP;#124; SQL_FD_FETCH_FIRST &AMP;#124; SQL_FD_FETCH_LAST &AMP;#124; SQL_FD_FETCH_NEXT &AMP;#124; SQL_FD_FETCH_PRIOR &AMP;#124; SQL_FD_FETCH_RELATIVE &AMP;#124; SQL_FD_FETCH_BOOKMARK|  
|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1|SQL_CA1_NEXT &AMP;#124; SQL_CA1_ABSOLUTE &AMP;#124; SQL_CA1_RELATIVE &AMP;#124; SQL_CA1_LOCK_NO_CHANGE &AMP;#124; SQL_CA1_POS_POSITION &AMP;#124; SQL_CA1_POSITIONED_DELETE &AMP;#124; SQL_CA1_POSITIONED_UPDATE &AMP;#124; SQL_CA1_SELECT_FOR_UPDATE|  
|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2|SQL_CA2_READ_ONLY_CONCUR &AMP;#124; SQL_CA2_OPT_VALUES_CONCURRENCY &AMP;#124; SQL_CA2_SENSITIVITY_UPDATES|  
|SQL_GETDATA_EXTENSIONS|SQL_GD_BLOCK &#124; tutti i valori restituiti dal driver **Nota:** quando i dati vengono recuperati con **SQLFetchScroll**, **SQLGetData** supporta la funzionalità specificata con le maschere di bit SQL_GD_ANY_COLUMN e SQL_GD_BOUND.|  
|SQL_KEYSET_DRIVEN_CURSOR_ATTRIBUTES1|0|  
|SQL_KEYSET_DRIVEN_CURSOR_ATTRIBUTES2|0|  
|SQL_LOCK_TYPES [1]|SQL_LCK_NO_CHANGE|  
|SQL_STATIC_CURSOR_ATTRIBUTES1|SQL_CA1_NEXT &AMP;#124; SQL_CA1_ABSOLUTE &AMP;#124; SQL_CA1_RELATIVE &AMP;#124; SQL_CA1_BOOKMARK &AMP;#124; SQL_CA1_LOCK_NO_CHANGE &AMP;#124; SQL_CA1_POS_POSITION &AMP;#124; SQL_CA1_POSITIONED_DELETE &AMP;#124; SQL_CA1_POSITIONED_UPDATE &AMP;#124; SQL_CA1_SELECT_FOR_UPDATE|  
|SQL_STATIC_CURSOR_ATTRIBUTES2|SQL_CA2_READ_ONLY_CONCUR &AMP;#124; SQL_CA2_OPT_VALUES_ CONCORRENZA &AMP;#124; SQL_CA2_SENSITIVITY_UPDATES|  
|SQL_POS_OPERATIONS [1]|SQL_POS_POSITION|  
|SQL_POSITIONED_STATEMENTS [1]|SQL_PS_POSITIONED_DELETE &AMP;#124; SQL_PS_POSITIONED_UPDATE &AMP;#124; SQL_PS_SELECT_FOR_UPDATE|  
|SQL_ROW_UPDATES|"Y"|  
|SQL_SCROLL_CONCURRENCY [1]|SQL_SCCO_READ_ONLY &AMP;#124; SQL_SCCO_OPT_VALUES|  
|SQL_SCROLL_OPTIONS|SQL_SO_FORWARD_ONLY &AMP;#124; SQL_SO_STATIC|  
|SQL_STATIC_SENSITIVITY [1]|SQL_SS_UPDATES|  
  
 [1] utilizzato solo quando la libreria di cursori viene utilizzata con un driver ODBC di 2. x.  
  
> [!IMPORTANT]  
>  Quando le transazioni vengono eseguito il commit o rollback come origine dati, la libreria di cursori implementa il comportamento del cursore stesso. Ovvero, il commit o il rollback di una transazione, tramite la chiamata a **SQLEndTran** o utilizzando l'attributo di connessione SQL_ATTR_AUTOCOMMIT, può causare l'origine dati eliminare i piani di accesso e chiudere i cursori per tutte le istruzioni in una connessione. Per ulteriori informazioni, vedere i tipi di informazioni SQL_CURSOR_COMMIT_BEHAVIOR e SQL_CURSOR_ROLLBACK_BEHAVIOR in [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md).
