---
title: Rilascio di un Handle di istruzione | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- reusing statement handles
- freeing statement handles
- statements [ODBC], statement handles
- SQLFreeStmt function
- ODBC applications, statements
- statement handles [ODBC]
ms.assetid: 96fdff84-0ca7-460a-a240-94ee826ea41c
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3da32585644e0bd7d3a572ef2052f387e4d33232
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37426730"
---
# <a name="freeing-a-statement-handle"></a>Rilascio di un handle di istruzione
  È più efficiente riutilizzare handle di istruzione anziché eliminarli e allocarne di nuovi. Prima di eseguire una nuova istruzione SQL su un handle di istruzione, le applicazioni devono verificare che le impostazioni delle istruzioni correnti siano corrette. Tra le impostazioni sono inclusi gli attributi di istruzione, le associazioni di parametri e le associazioni dei set di risultati. In generale, imposta i parametri e il risultato per l'istruzione SQL precedente necessario disassociarlo tramite la chiamata [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) con il SQL_RESET_PARAMS e SQL_UNBIND opzioni e quindi eseguire nuove associazioni per la nuova istruzione SQL.  
  
 Quando l'applicazione ha terminato di utilizzare l'istruzione, chiama [SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md) per liberare l'istruzione. Si noti che **SQLDisconnect** libera automaticamente tutte le istruzioni in una connessione.  
  
## <a name="see-also"></a>Vedere anche  
 [L'esecuzione di query &#40;ODBC&#41;](executing-queries-odbc.md)  
  
  
