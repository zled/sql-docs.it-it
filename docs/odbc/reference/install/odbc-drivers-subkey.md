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
ms.topic: article
helpviewer_keywords:
- subkeys [ODBC], drivers subkey
- registry entries for components [ODBC], drivers subkey
- drivers subkey [ODBC]
ms.assetid: 8edbf68f-d05d-4d77-92f6-e9500008f520
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 925e24f295602d7e66fe37935b53724b4d162adf
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
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
