---
title: Commit e Rollback comportamento | Documenti Microsoft
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
- interoperability [ODBC], transaction support
- transactions [ODBC], DBMS support
ms.assetid: 2ac8f012-e46d-41ca-81bb-e4a3246e3241
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7bf7e756c77ceef96502fdacc078b4780f01ce86
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="commit-and-rollback-behavior"></a>Commit e il comportamento di Rollback
Un comportamento comune tra server DBMS consiste nel chiudere i cursori e ignorare le istruzioni preparate quando un'istruzione commit o rollback. I database desktop sono più probabili mantenere i cursori aperti e mantenere le istruzioni preparate. Per ulteriori informazioni, vedere le opzioni SQL_CURSOR_COMMIT_BEHAVIOR e SQL_CURSOR_ROLLBACK_BEHAVIOR il [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) descrizione della funzione e [effettiva delle transazioni su cursori e le istruzioni preparate](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md).

