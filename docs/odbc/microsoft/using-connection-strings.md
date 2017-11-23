---
title: Utilizzo delle stringhe di connessione | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connection strings [ODBC]
- connecting to data source [ODBC], Visual FoxPro
- Visual FoxPro data source [ODBC], connecting
ms.assetid: 57634960-47e9-49bf-95c1-6e3702ac8166
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dc75f4b4b90f2845ea18d6e3208806fce2c9179e
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="using-connection-strings"></a>Utilizzo delle stringhe di connessione
È possibile utilizzare una stringa di connessione per connettersi a un'origine dati di Visual FoxPro.  
  
 Ad esempio, per connettersi all'origine dati TasTrade e l'impostazione corrente di esclusivo associata con l'origine dati di sostituzione, utilizzare la stringa:  
  
```  
DSN=TasTrade;Exclusive=Yes  
```  
  
 Per un elenco delle parole chiave di attributo e dei valori è possibile includere nella stringa di connessione, vedere [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md).  
  
 Per una spiegazione completa della sintassi della stringa di connessione, vedere [SQLBrowseConnect](../../odbc/reference/syntax/sqlbrowseconnect-function.md) nel *riferimento per programmatori ODBC*.
