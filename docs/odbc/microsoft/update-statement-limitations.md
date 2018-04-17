---
title: Limitazioni di istruzione UPDATE | Documenti Microsoft
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
- UPDATE statement limitations [ODBC]
- ODBC SQL grammar, UPDATE statement limitations
ms.assetid: 14700aac-e135-4dc0-9138-4b01224461d5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ca36c4ae277aa36e9cbf2e4787b6131ce099ce17
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="update-statement-limitations"></a>Limitazioni di istruzione di aggiornamento
Per il driver Paradox aggiornare una tabella, la tabella deve includere un indice univoco (chiave primaria). Quando si utilizza il driver Paradox senza implementare Borland Database Engine, non è possibile aggiornare una tabella di Paradox.  
  
 Non è supportata dal driver del testo.  
  
 Quando viene utilizzato il driver per Microsoft Excel, è possibile aggiornare i valori, ma non può essere eliminata una riga da una tabella in base a un foglio di calcolo di Microsoft Excel. Di conseguenza, l'istruzione UPDATE non è considerata ufficialmente supportata dal driver Microsoft Excel. Solo l'istruzione INSERT è considerato supportato.
