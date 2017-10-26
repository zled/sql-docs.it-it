---
title: SQLSetEnvAttr e la libreria di cursori | Documenti Microsoft
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
- SQLSetEnvAttr function [ODBC], Cursor Library
ms.assetid: 59cc8eae-09ae-4796-869a-c5806488ae83
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c08fab3b713e1f1a57d7a81f53ed29b1678893cd
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetenvattr-and-the-cursor-library"></a>SQLSetEnvAttr e la libreria di cursori
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 In questo argomento viene illustrato l'utilizzo del **SQLSetEnvAttr** funzione con la libreria di cursori. Per informazioni generali su **SQLSetEnvAttr**, vedere [SQLSetEnvAttr-funzione](../../../odbc/reference/syntax/sqlsetenvattr-function.md).  
  
 La libreria di cursori non è interessata dalla configurazione dell'impostazione dell'attributo environment SQL_ATTR_ODBC_VERSION, indipendentemente dal fatto la versione dell'applicazione o una versione del driver.

