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
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLTransact
- SQLTransact function [ODBC], Access Driver
ms.assetid: 892b79c7-9e20-4d1f-bc60-d4b25694ca25
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5f157d3423f6a409ea165a32d058f16d14d1d949
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqltransact-access-driver"></a>SQLTransact (Driver di accesso)
> [!NOTE]  
>  In questo argomento fornisce informazioni di accesso specifici del Driver. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Quando viene utilizzato il driver Microsoft Access, SQL_COMMIT e SQL_ROLLBACK sono supportati per il *fType* argomento in una chiamata a **SQLTransact**.  
  
 Se si verifica un errore durante il processo di commit, il database interessato può essere ripristinato tramite l'opzione di Database di ripristino nel programma di installazione di driver Microsoft Access o tramite la parola chiave REPAIR_DB nel **SQLConfigDataSource** funzione.
