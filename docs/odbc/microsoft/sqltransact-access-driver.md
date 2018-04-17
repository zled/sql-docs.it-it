---
title: SQLTransact (Driver di accesso) | Documenti Microsoft
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
- Access driver [ODBC], SQLTransact
- SQLTransact function [ODBC], Access Driver
ms.assetid: 892b79c7-9e20-4d1f-bc60-d4b25694ca25
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: aeed0fc0d6bb19c7440c35f39094c05bf17bfbf7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sqltransact-access-driver"></a>SQLTransact (Driver di accesso)
> [!NOTE]  
>  In questo argomento fornisce informazioni di accesso specifici del Driver. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Quando viene utilizzato il driver Microsoft Access, SQL_COMMIT e SQL_ROLLBACK sono supportati per il *fType* argomento in una chiamata a **SQLTransact**.  
  
 Se si verifica un errore durante il processo di commit, il database interessato può essere ripristinato tramite l'opzione di Database di ripristino nel programma di installazione di driver Microsoft Access o tramite la parola chiave REPAIR_DB nel **SQLConfigDataSource** funzione.
