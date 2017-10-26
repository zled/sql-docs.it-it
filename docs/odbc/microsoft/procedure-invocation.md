---
title: Chiamata della stored procedure | Documenti Microsoft
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
- SQL grammar [ODBC], procedure invocation
- procedure invocation [ODBC]
ms.assetid: b9ff2c3a-2003-4832-adbe-08dd0f5ad948
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fd42836285c29e36e6bb64ebe594df570876ff6e
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="procedure-invocation"></a>Chiamata della stored procedure
Quando viene utilizzato il driver Microsoft Access, procedure possono essere richiamate dal driver tramite il **SQLExecDirect** o **SQLPrepare** funzione con la sintassi seguente: {CHIAMARE *-nome della routine * [(*parametro*[,*parametro*]...)]}. Si noti che le espressioni non sono supportate come parametri per una routine chiamata.  
  
 Se un nome della stored procedure include un trattino, il nome deve essere delimitato con virgolette indietro (').  
  
 Una query con parametri può essere chiamata utilizzando l'istruzione precedente.

