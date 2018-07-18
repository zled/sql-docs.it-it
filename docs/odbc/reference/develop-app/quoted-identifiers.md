---
title: Gli identificatori tra virgolette | Documenti Microsoft
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
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], quoted identifiers
- quoted identifiers [ODBC]
ms.assetid: 729ba55f-743b-4a04-8c39-ac0a9914211d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e74c39ad73357e50c1040e8a90029c0bf65f7b6e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32911526"
---
# <a name="quoted-identifiers"></a>Identificatori delimitati
In un'istruzione SQL, gli identificatori che contengono caratteri speciali o parole chiave con corrispondenza devono essere racchiuso tra *virgolette identificatore*; gli identificatori racchiusi tra tali caratteri sono note come *identificatoritravirgolette*(noto anche come *identificatori delimitati* in SQL-92). Ad esempio, l'identificatore di contabilità fornitori è racchiuso tra virgolette nell'esempio seguente **selezionare** istruzione:  
  
```  
SELECT * FROM "Accounts Payable"  
```  
  
 Il motivo per racchiudere tra virgolette gli identificatori è rendere analizzabili l'istruzione. Se, ad esempio contabilità fornitori virgolette nell'istruzione precedente, il parser sarebbe si supponga che sono presenti due tabelle, gli account e fornitori e restituire un errore di sintassi che non sono separati da una virgola. L'identificatore di virgolette è specifico del driver e vengono recuperato con l'opzione SQL_IDENTIFIER_QUOTE_CHAR in **SQLGetInfo**. Gli elenchi di caratteri speciali e parole chiave vengono recuperati con le opzioni SQL_SPECIAL_CHARACTERS e SQL_KEYWORDS **SQLGetInfo**.  
  
 Per maggiore sicurezza, applicazioni interoperative offerta spesso tutti gli identificatori, ad eccezione di quelli per pseudo-colonne, ad esempio la colonna ROWID Oracle. **SQLSpecialColumns** restituisce un elenco di pseudocolonne. Inoltre, se sono presenti restrizioni specifiche dell'applicazione in cui i caratteri speciali possono essere visualizzati in un nome di oggetto, è ideale per applicazioni interoperabili di non utilizzare caratteri speciali in tali posizioni.
