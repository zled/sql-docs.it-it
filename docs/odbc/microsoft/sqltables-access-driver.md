---
title: SQLTables (Driver di accesso) | Documenti Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- SQLTables function [ODBC], Access Driver
- Access driver [ODBC], SQLTables
ms.assetid: 94423cf9-341a-4db6-bb10-8f5448df7fc3
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 23b06dd89d816796eda1d2bd35d25d6ea9939516
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqltables-access-driver"></a>SQLTables (Driver di accesso)
> [!NOTE]  
>  In questo argomento fornisce informazioni di accesso specifici del Driver. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Argomento|Commenti|  
|--------------|--------------|  
|*szTableOwner*|L'argomento valido solo per *szTableOwner* è NULL perché nessuno dei driver supporta i nomi dei proprietari. Con *szTableOwner* impostato su NULL, vengono restituite tutte le tabelle. Nella colonna TABLE_OWNER viene restituito NULL.|  
|*szTableQualifier*|Nella colonna TABLE_QUALIFIER **SQLTables** restituirà il percorso in un file di database.|  
|*SzTableType*|Quando viene utilizzato il driver Microsoft Access, "Tabella di sistema" è supportata per *szTableType* per tabelle di sistema "SINONIMO" è supportato per le tabelle collegate e "VIEW" è supportato per la restituzione di riga query.|  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione SQLTables](../../odbc/reference/syntax/sqltables-function.md)
