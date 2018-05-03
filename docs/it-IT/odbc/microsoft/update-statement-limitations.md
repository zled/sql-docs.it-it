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
ms.topic: conceptual
helpviewer_keywords:
- UPDATE statement limitations [ODBC]
- ODBC SQL grammar, UPDATE statement limitations
ms.assetid: 14700aac-e135-4dc0-9138-4b01224461d5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bbb1e6cbf0660f7b016391d5881b77d7e89e1f81
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="update-statement-limitations"></a>Limitazioni di istruzione di aggiornamento
Per il driver Paradox aggiornare una tabella, la tabella deve includere un indice univoco (chiave primaria). Quando si utilizza il driver Paradox senza implementare Borland Database Engine, non è possibile aggiornare una tabella di Paradox.  
  
 Non è supportata dal driver del testo.  
  
 Quando viene utilizzato il driver per Microsoft Excel, è possibile aggiornare i valori, ma non può essere eliminata una riga da una tabella in base a un foglio di calcolo di Microsoft Excel. Di conseguenza, l'istruzione UPDATE non è considerata ufficialmente supportata dal driver Microsoft Excel. Solo l'istruzione INSERT è considerato supportato.
