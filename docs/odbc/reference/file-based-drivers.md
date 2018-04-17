---
title: Driver basati su file | Documenti Microsoft
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
- file-based drivers [ODBC]
- ODBC architecture [ODBC], drivers
- drivers [ODBC], file-based drivers
ms.assetid: d92e0c5c-d176-4282-bbe1-d449e2223d50
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e63c8026b31140f5ad1f94c99f143670d31c5c78
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="file-based-drivers"></a>Driver basati su file
Driver basati su file vengono utilizzati con origini dati, ad esempio dBASE che non dispongono di un motore di database autonomo per il driver da utilizzare. Questi driver accedere direttamente i dati fisici e devono implementare un motore di database per elaborare istruzioni SQL. Come procedura standard, i motori di database di driver basati su file implementano il subset di ODBC SQL definite dal livello di conformità SQL minima. per un elenco delle istruzioni SQL in questo livello di conformità, vedere [grammatica SQL di appendice c:](../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
 Nel confronto tra driver basati su DBMS e file, driver basati su file sono meno potenti e più difficili da scrivere, a causa di componente del motore di database, meno complesso da configurare perché non sono presenti rete, perché alcuni utenti hanno il tempo di scrittura del database motori potenti simili a quelli prodotti da aziende di database.  
  
 Nella figura seguente mostra due diverse configurazioni di driver basati su file, uno in cui i dati si trovano in locale e l'altro in cui si trova in un file server di rete.  
  
 ![Due configurazioni di file&#45;basato su driver](../../odbc/reference/media/pr06.gif "pr06")
