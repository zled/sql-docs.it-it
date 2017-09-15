---
title: ODBC Core sottochiave | Documenti Microsoft
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
- subkeys [ODBC], core subkey
- registry entries for components [ODBC], core subkey
- core subkey [ODBC]
ms.assetid: 055b31fc-f96c-450b-a596-d4570079fbf2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ad7a45f0f3272e1e2d7ae799ab1ca86bfb90b9be
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

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
