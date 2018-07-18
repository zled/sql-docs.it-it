---
title: Driver basati su file | Documenti Microsoft
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
- file-based drivers [ODBC]
- ODBC architecture [ODBC], drivers
- drivers [ODBC], file-based drivers
ms.assetid: d92e0c5c-d176-4282-bbe1-d449e2223d50
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e8ce91d6606501d64702c27c6f4915b3ec96b936
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="file-based-drivers"></a>Driver basati su file
Driver basati su file vengono utilizzati con origini dati, ad esempio dBASE che non dispongono di un motore di database autonomo per il driver da utilizzare. Questi driver accedere direttamente i dati fisici e devono implementare un motore di database per elaborare istruzioni SQL. Come procedura standard, i motori di database di driver basati su file implementano il subset di ODBC SQL definite dal livello di conformità SQL minima. per un elenco delle istruzioni SQL in questo livello di conformità, vedere [grammatica SQL di appendice c:](../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
 Nel confronto tra driver basati su DBMS e file, driver basati su file sono meno potenti e più difficili da scrivere, a causa di componente del motore di database, meno complesso da configurare perché non sono presenti rete, perché alcuni utenti hanno il tempo di scrittura del database motori potenti simili a quelli prodotti da aziende di database.  
  
 Nella figura seguente mostra due diverse configurazioni di driver basati su file, uno in cui i dati si trovano in locale e l'altro in cui si trova in un file server di rete.  
  
 ![Due configurazioni di file&#45;basato su driver](../../odbc/reference/media/pr06.gif "pr06")
