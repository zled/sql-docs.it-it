---
title: SQLBindParameter (libreria di cursori) | Documenti Microsoft
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
- SQLBindParameter function [ODBC], Cursor Library
ms.assetid: 04c53e4c-cd1d-40b2-9997-684ebe43499f
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d20324c0d7366573600aa460e3c062a01fd2cc4e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlbindparameter-cursor-library"></a>SQLBindParameter (libreria di cursori)
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 In questo argomento viene illustrato l'utilizzo del **SQLBindParameter** funzione nella libreria di cursori. Per informazioni generali su **SQLBindParameter**, vedere [funzione SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md).  
  
 Un'applicazione può chiamare **SQLBindParameter** per riassociare i parametri, purché il tipo di dati C, le dimensioni di colonna e cifre decimali della colonna associata rimangono invariati.  
  
 La libreria di cursori supporta l'impostazione dell'attributo di istruzione SQL_ATTR_ROW_BIND_OFFSET_PTR per usare gli offset di associazione. (**SQLBindParameter** non deve essere chiamato per la riassociazione avvenga.)  
  
 La libreria di cursori supporta i parametri data-at-execution di associazione.
