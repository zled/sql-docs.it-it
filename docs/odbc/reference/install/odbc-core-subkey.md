---
title: ODBC Core sottochiave | Documenti Microsoft
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
- subkeys [ODBC], core subkey
- registry entries for components [ODBC], core subkey
- core subkey [ODBC]
ms.assetid: 055b31fc-f96c-450b-a596-d4570079fbf2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cf8e143a8d5d329fe3eb68185a3ebdf8f7f6cd6b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
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
