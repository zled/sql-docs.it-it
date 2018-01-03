---
title: Origini dei dati ODBC sottochiave | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- subkeys [ODBC], for data sources
- data sources [ODBC], subkeys
- registry entries for data sources [ODBC], subkeys
ms.assetid: 0a8ccb80-c573-4418-84e5-f04a2b0e2ac1
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3141bf0b16c6be579bf76a77b13e240ad5befef4
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-data-sources-subkey"></a>Sottochiave di origini dati ODBC
I valori nella sottochiave origini dati ODBC elencare le origini dati. Il formato di questi valori è come illustrato nella tabella seguente.  
  
|nome|Tipo di dati|data|  
|----------|---------------|----------|  
|*nome dell'origine dati*|REG_SZ.|*Descrizione del driver*|  
  
 Il *nome dell'origine dati* valore è definito dal programma di amministrazione (che in genere richiede all'utente per tale), e *driver descrizione* è definito dallo sviluppatore del driver (in genere è il nome del DBMS associata al driver).  
  
 Ad esempio, si supponga che sono state definite tre origini dati: inventario, che viene utilizzato SQL Server. Retribuzioni, che utilizza dBASE; e personale, che utilizza i file di testo in formato. I valori nella sottochiave origini dati ODBC potrebbero essere come segue:  
  
```  
Inventory : REG_SZ : SQL Server  
Payroll : REG_SZ : dBASE  
Personnel : REG_SZ : Text  
```
