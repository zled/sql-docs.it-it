---
title: Stato di transizione controlli | Documenti Microsoft
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
- diagnostic information [ODBC], driver manager error checking
- state transition checks [ODBC]
- driver manager [ODBC], error checking
ms.assetid: 0706db7d-e125-4845-a13a-7fe4308f7360
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9a6873114b5d15bdf9bfbac369dacaea712a0236
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="state-transition-checks"></a>Controlli delle transizioni di stato
Gestione Driver controlla che lo stato dell'ambiente, connessione o istruzione sia appropriato per la funzione chiamata. Ad esempio, una connessione deve essere un allocato stato quando **SQLConnect** viene chiamato deve essere un'istruzione in una stato quando **SQLExecute** viene chiamato. Gestione Driver restituisce SQL_ERROR per gli errori di transizione di stato.

