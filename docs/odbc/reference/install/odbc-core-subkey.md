---
title: ODBC Core sottochiave | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- subkeys [ODBC], core subkey
- registry entries for components [ODBC], core subkey
- core subkey [ODBC]
ms.assetid: 055b31fc-f96c-450b-a596-d4570079fbf2
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 85c4e842ef48f412696c4a0c851480915f5d9b27
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="odbc-core-subkey"></a>ODBC Core sottochiave
Il valore della sottochiave ODBC Core fornisce il conteggio di utilizzi per i componenti di base (gestione Driver, libreria di cursori, programma di installazione DLL e così via). Nella tabella seguente è illustrato il formato di questo valore.  
  
|Nome|Tipo di dati|data|  
|----------|---------------|----------|  
|UsageCount|REG_DWORD|*count*|  
  
 Si supponga, ad esempio, che sono stati installati i componenti principali di ODBC per i programmi di installazione per tre applicazioni e i due diversi driver. Il valore della sottochiave ODBC Core sarebbe:  
  
```  
UsageCount : REG_DWORD : 0x5  
```
