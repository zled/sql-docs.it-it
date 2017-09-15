---
title: ODBC driver sottochiave | Documenti Microsoft
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
- subkeys [ODBC], drivers subkey
- registry entries for components [ODBC], drivers subkey
- drivers subkey [ODBC]
ms.assetid: 8edbf68f-d05d-4d77-92f6-e9500008f520
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 21b151256f93d77cd0efecedfa8eef2ddcd6482b
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="odbc-drivers-subkey"></a>ODBC driver sottochiave
I valori nella sottochiave del driver ODBC elenco driver installati. Nella tabella seguente è illustrato il formato di questi valori.  
  
|Nome|Tipo di dati|data|  
|----------|---------------|----------|  
|*Descrizione del driver*|REG_SZ.|**Installato**|  
  
 Il *driver descrizione* nome è definito dallo sviluppatore del driver. In genere è il nome del DBMS associato al driver.  
  
 Si supponga, ad esempio, che sono stati installati i driver per i file di testo formattato e SQL Server. I valori nella sottochiave del driver ODBC potrebbero essere:  
  
```  
Text : REG_SZ : Installed  
SQL Server : REG_SZ : Installed  
```
