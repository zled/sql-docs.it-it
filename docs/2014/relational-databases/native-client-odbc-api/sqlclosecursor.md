---
title: SQLCloseCursor | Documenti di Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLCloseCursor function
ms.assetid: e7134d65-5c1c-4ae2-b119-d9b4b9a42483
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 26b00c4781624bf653ad9a8200a219951dc793c7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48097161"
---
# <a name="sqlclosecursor"></a>SQLCloseCursor
  **SQLCloseCursor** sostituisce [SQLFreeStmt](sqlfreestmt.md) con un *opzione* valore SQL_CLOSE. Dal momento in cui **SQLCloseCursor**, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client Elimina le righe del set di risultati in sospeso. Notare che le associazioni di parametro e colonna dell'istruzione, se presenti, non vengono modificate da **SQLCloseCursor**.  
  
## <a name="see-also"></a>Vedere anche  
 [SQLCloseCursor](http://go.microsoft.com/fwlink/?LinkId=59331)   
 [Dettagli di implementazione dell'API ODBC](odbc-api-implementation-details.md)  
  
  
