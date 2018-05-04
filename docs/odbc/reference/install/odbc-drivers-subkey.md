---
title: ODBC driver sottochiave | Documenti Microsoft
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
- subkeys [ODBC], drivers subkey
- registry entries for components [ODBC], drivers subkey
- drivers subkey [ODBC]
ms.assetid: 8edbf68f-d05d-4d77-92f6-e9500008f520
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0359547122a9ee5537ae4634e6907e39f12916d0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="odbc-drivers-subkey"></a>ODBC driver sottochiave
I valori nella sottochiave del driver ODBC elenco driver installati. Nella tabella seguente è illustrato il formato di questi valori.  
  
|Nome|Tipo di dati|data|  
|----------|---------------|----------|  
|*Descrizione del driver*|REG_SZ|**Installato**|  
  
 Il *driver descrizione* nome è definito dallo sviluppatore del driver. In genere è il nome del DBMS associato al driver.  
  
 Si supponga, ad esempio, che sono stati installati i driver per i file di testo formattato e SQL Server. I valori nella sottochiave del driver ODBC potrebbero essere:  
  
```  
Text : REG_SZ : Installed  
SQL Server : REG_SZ : Installed  
```
