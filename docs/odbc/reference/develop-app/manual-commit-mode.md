---
title: "Modalità di Commit manuale | Documenti Microsoft"
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
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1a5f9d510d1a92ce8faf4fe29f3274afdba6f83b
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="manual-commit-mode"></a>Modalità di Commit manuale
*In modalità di commit manuale,* applicazioni devono essere completata in modo esplicito le transazioni chiamando **SQLEndTran** per eseguirne il commit o il rollback. Si tratta della modalità di transazione normale per la maggior parte dei database relazionali.  
  
 Le transazioni in ODBC non debbano essere avviato in modo esplicito. In alternativa, in modo implicito inizia una transazione ogni volta che viene avviata l'applicazione funziona nel database. Se l'origine dati richiede può avviare le transazioni esplicite, il driver necessario fornirlo ogni volta che l'applicazione esegue un'istruzione che richiedono una transazione e non è presente alcuna transazione corrente.
