---
title: 'Alternative: Utilizzo di istruzioni SQL | Documenti Microsoft'
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL statements [ADO]
- editing data [ADO], sql statements
- ADO, SQL statements
ms.assetid: 8b528b23-063d-45ea-8dea-6a90d4060b20
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6c1d1da58832a1fbbc133c17f58d940d46f5c6e1
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

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

