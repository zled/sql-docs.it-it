---
title: ODBC Core sottochiave | Documenti Microsoft
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
- subkeys [ODBC], core subkey
- registry entries for components [ODBC], core subkey
- core subkey [ODBC]
ms.assetid: 055b31fc-f96c-450b-a596-d4570079fbf2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f05e36c59d674104dead92ecd7da63f5fb58588a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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
