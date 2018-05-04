---
title: ODBC driver sottochiave | Documenti Microsoft
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
- subkeys [ODBC], drivers subkey
- registry entries for components [ODBC], drivers subkey
- drivers subkey [ODBC]
ms.assetid: 8edbf68f-d05d-4d77-92f6-e9500008f520
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 17e0a418957aa4413d0fd7d02ebdc0243596d013
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
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
