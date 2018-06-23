---
title: SQLCloseCursor | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLCloseCursor function
ms.assetid: e7134d65-5c1c-4ae2-b119-d9b4b9a42483
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b78467ae9648639051480f16eb073a9c48ccb645
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36170795"
---
# <a name="sqlclosecursor"></a>SQLCloseCursor
  **SQLCloseCursor** sostituisce [SQLFreeStmt](sqlfreestmt.md) con un *opzione* valore SQL_CLOSE. Al momento della ricezione della **SQLCloseCursor**, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client Elimina righe del set di risultati in sospeso. Notare che le associazioni di parametro e colonna dell'istruzione, se presenti, non vengono modificate da **SQLCloseCursor**.  
  
## <a name="see-also"></a>Vedere anche  
 [SQLCloseCursor](http://go.microsoft.com/fwlink/?LinkId=59331)   
 [Dettagli di implementazione dell'API ODBC](odbc-api-implementation-details.md)  
  
  