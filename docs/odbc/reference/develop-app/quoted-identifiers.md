---
title: Gli identificatori tra virgolette | Documenti Microsoft
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
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], quoted identifiers
- quoted identifiers [ODBC]
ms.assetid: 729ba55f-743b-4a04-8c39-ac0a9914211d
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9a530e24368339305fc510a3a3f6fc9a6193e694
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="quoted-identifiers"></a>Identificatori delimitati
In un'istruzione SQL, gli identificatori che contengono caratteri speciali o parole chiave con corrispondenza devono essere racchiuso tra *virgolette identificatore*; gli identificatori racchiusi tra tali caratteri sono note come *identificatoritravirgolette*(noto anche come *identificatori delimitati* in SQL-92). Ad esempio, l'identificatore di contabilità fornitori è racchiuso tra virgolette nell'esempio seguente **selezionare** istruzione:  
  
```  
SELECT * FROM "Accounts Payable"  
```  
  
 Il motivo per racchiudere tra virgolette gli identificatori è rendere analizzabili l'istruzione. Se, ad esempio contabilità fornitori virgolette nell'istruzione precedente, il parser sarebbe si supponga che sono presenti due tabelle, gli account e fornitori e restituire un errore di sintassi che non sono separati da una virgola. L'identificatore di virgolette è specifico del driver e vengono recuperato con l'opzione SQL_IDENTIFIER_QUOTE_CHAR in **SQLGetInfo**. Gli elenchi di caratteri speciali e parole chiave vengono recuperati con le opzioni SQL_SPECIAL_CHARACTERS e SQL_KEYWORDS **SQLGetInfo**.  
  
 Per maggiore sicurezza, applicazioni interoperative offerta spesso tutti gli identificatori, ad eccezione di quelli per pseudo-colonne, ad esempio la colonna ROWID Oracle. **SQLSpecialColumns** restituisce un elenco di pseudocolonne. Inoltre, se sono presenti restrizioni specifiche dell'applicazione in cui i caratteri speciali possono essere visualizzati in un nome di oggetto, è ideale per applicazioni interoperabili di non utilizzare caratteri speciali in tali posizioni.
