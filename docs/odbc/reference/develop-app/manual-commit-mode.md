---
title: Modalità di Commit manuale | Documenti Microsoft
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
- rolling back transactions [ODBC]
- manual-commit mode [ODBC]
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
- transactions [ODBC], rolling back
ms.assetid: 9c4b3931-e48b-4960-89a2-5697537e9f51
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bdf722c77071a3958f115e573bfe227f9561dd01
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="manual-commit-mode"></a>Modalità di Commit manuale
*In modalità di commit manuale* le applicazioni in modo esplicito devono completare le transazioni chiamando **SQLEndTran** per eseguirne il commit o il rollback. Si tratta della modalità di transazione normale per la maggior parte dei database relazionali.  
  
 Le transazioni in ODBC non debbano essere avviato in modo esplicito. In alternativa, in modo implicito inizia una transazione ogni volta che viene avviata l'applicazione funziona nel database. Se l'origine dati richiede può avviare le transazioni esplicite, il driver necessario fornirlo ogni volta che l'applicazione esegue un'istruzione che richiedono una transazione e non è presente alcuna transazione corrente.
