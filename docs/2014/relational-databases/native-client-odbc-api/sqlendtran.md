---
title: SQLEndTran | Documenti Microsoft
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
- SQLEndTran function
ms.assetid: 95cff841-c2d5-4e1e-a18d-f3d4696a5b85
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 360c015dba746f110327804a457bb6e5c1e83212
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36167242"
---
# <a name="sqlendtran"></a>SQLEndTran
  Per impostazione predefinita, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client chiude cursore associato dell'istruzione quando **SQLEndTran** viene eseguito il commit o il rollback di un'operazione. I cursori del server vengono chiusi a meno che non siano statici. Quando si **SQLEndTran** viene eseguito il commit o il rollback di un'operazione, il comportamento del cursore associato dell'istruzione è determinato dal valore dell'attributo specifiche del driver di connessione ODBC SQL_COPT_SS_PRESERVE_CURSORS, l'impostazione [SQLSetConnectAttr](sqlsetconnectattr.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Dettagli di implementazione di API ODBC](odbc-api-implementation-details.md)   
 [Funzione SQLEndTran](http://go.microsoft.com/fwlink/?LinkId=59342)  
  
  