---
title: Limitazioni di istruzione UPDATE | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UPDATE statement limitations [ODBC]
- ODBC SQL grammar, UPDATE statement limitations
ms.assetid: 14700aac-e135-4dc0-9138-4b01224461d5
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 502315916781ae5624f94e099c0cd95c52ffe8a8
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="update-statement-limitations"></a>Limitazioni di istruzione di aggiornamento
Per il driver Paradox aggiornare una tabella, la tabella deve includere un indice univoco (chiave primaria). Quando si utilizza il driver Paradox senza implementare Borland Database Engine, non è possibile aggiornare una tabella di Paradox.  
  
 Non è supportata dal driver del testo.  
  
 Quando viene utilizzato il driver per Microsoft Excel, è possibile aggiornare i valori, ma non può essere eliminata una riga da una tabella in base a un foglio di calcolo di Microsoft Excel. Di conseguenza, l'istruzione UPDATE non è considerata ufficialmente supportata dal driver Microsoft Excel. Solo l'istruzione INSERT è considerato supportato.
