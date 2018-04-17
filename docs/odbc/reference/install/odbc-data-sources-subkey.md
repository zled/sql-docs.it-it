---
title: Origini dei dati ODBC sottochiave | Documenti Microsoft
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
ms.topic: article
helpviewer_keywords:
- subkeys [ODBC], for data sources
- data sources [ODBC], subkeys
- registry entries for data sources [ODBC], subkeys
ms.assetid: 0a8ccb80-c573-4418-84e5-f04a2b0e2ac1
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bbe6d0e7e424f2bea8d90eb4e9c5993f50370848
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="odbc-data-sources-subkey"></a>Sottochiave di origini dati ODBC
I valori nella sottochiave origini dati ODBC elencare le origini dati. Il formato di questi valori è come illustrato nella tabella seguente.  
  
|Nome|Tipo di dati|data|  
|----------|---------------|----------|  
|*nome dell'origine dati*|REG_SZ|*Descrizione del driver*|  
  
 Il *nome dell'origine dati* valore è definito dal programma di amministrazione (che in genere richiede all'utente per tale), e *driver descrizione* è definito dallo sviluppatore del driver (in genere è il nome del DBMS associata al driver).  
  
 Ad esempio, si supponga che sono state definite tre origini dati: inventario, che viene utilizzato SQL Server. Retribuzioni, che utilizza dBASE; e personale, che utilizza i file di testo in formato. I valori nella sottochiave origini dati ODBC potrebbero essere come segue:  
  
```  
Inventory : REG_SZ : SQL Server  
Payroll : REG_SZ : dBASE  
Personnel : REG_SZ : Text  
```
