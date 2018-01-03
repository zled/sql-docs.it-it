---
title: 'Alternative: Utilizzo di istruzioni SQL | Documenti Microsoft'
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL statements [ADO]
- editing data [ADO], sql statements
- ADO, SQL statements
ms.assetid: 8b528b23-063d-45ea-8dea-6a90d4060b20
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 00d771042d09ab9dc95a90debbaac94ac15301d5
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="alternatives-using-sql-statements"></a>Alternative: Utilizzo di istruzioni SQL
ADO consente inoltre comandi come alternative per la proprietà e metodi predefiniti per la modifica dei dati. A seconda del provider, tutte le operazioni descritte in questa sezione possono essere eseguite anche passando i comandi all'origine dati. Ad esempio, le istruzioni UPDATE SQL utilizzabile per modificare i dati senza utilizzare il **valore** proprietà di un **campo**. Istruzioni SQL INSERT possono essere utilizzate per aggiungere nuovi record a un'origine dati, anziché il metodo ADO **AddNew**. Per ulteriori informazioni su SQL o il linguaggio di manipolazione dei dati del provider, vedere la documentazione dell'origine dati.  
  
 Ad esempio, è possibile passare una stringa SQL contenente un'istruzione DELETE in un database, come illustrato nel codice seguente:  
  
```  
'BeginSQLDelete  
strSQL = "DELETE FROM Shippers WHERE ShipperID = " & intId  
objConn1.Execute strSQL, , adCmdText + adExecuteNoRecords  
'EndSQLDelete  
```
