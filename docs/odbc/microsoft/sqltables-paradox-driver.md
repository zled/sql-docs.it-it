---
title: SQLTables (Driver Paradox) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Paradox driver [ODBC], SQLTables
- SQLTables function [ODBC], Paradox Driver
ms.assetid: d68adad6-97bd-4b47-bcf9-0102aafb00d4
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 505bbc8fb606a44d9c3f4bf94115fd5ff41e7d06
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqltables-paradox-driver"></a>SQLTables (Paradox Driver)
> [!NOTE]  
>  In questo argomento fornisce informazioni specifiche del Driver Paradox. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Argomento|Commenti|  
|--------------|--------------|  
|*szTableOwner*|L'argomento valido solo per *szTableOwner* è NULL perché nessuno dei driver supporta i nomi dei proprietari. Con *szTableOwner* impostato su NULL, vengono restituite tutte le tabelle. Nella colonna TABLE_OWNER viene restituito NULL.|  
|*szTableQualifier*|Nella colonna TABLE_QUALIFIER **SQLTables** restituirà il percorso in una directory.|  
|*SzTableType*|Per i file Paradox, "TABLE" è l'unico tipo di tabella è supportato.|  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione SQLTables](../../odbc/reference/syntax/sqltables-function.md)
