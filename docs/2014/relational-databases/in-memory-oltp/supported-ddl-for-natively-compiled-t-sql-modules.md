---
title: Costrutti è supportato nelle Stored procedure compilate in modo nativo | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6b21f47e-bceb-4054-8b3c-9d39bb9583c0
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c6a118b8d9dfe69f5890c9c66e71c2319a6a27a1
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2018
ms.locfileid: "40396120"
---
# <a name="supported-constructs-on-natively-compiled-stored-procedures"></a>Costrutti supportati su stored procedure compilate in modo nativo
  In questo argomento vengono illustrati i costrutti supportati nelle stored procedure compilate in modo nativo.  
  
 Per altre informazioni su costrutti non supportati, vedere [Costrutti Transact-SQL non supportati da OLTP in memoria](transact-sql-constructs-not-supported-by-in-memory-oltp.md).  
  
## <a name="procedure-ddl"></a>DLL di procedura  
 Sono supportati gli elementi seguenti:  
  
-   CREATE PROCEDURE  
  
-   DROP PROCEDURE  
  
-   SCHEMABINDING (obbligatorio per le stored procedure compilate in modo nativo)  
  
-   NATIVE_COMPILATION  
  
-   I parametri possono essere dichiarati come NOT NULL.  
  
-   Parametri con valori di tabella.  
  
## <a name="security"></a>Security  
 Sono supportati gli elementi seguenti:  
  
-   Per le procedure: EXECUTE AS OWNER, SELF e utente.  
  
-   Autorizzazioni GRANT e DENY per tabelle e procedure.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure compilate in modo nativo](natively-compiled-stored-procedures.md)  
  
  
