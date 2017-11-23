---
title: Chiamata della stored procedure | Documenti Microsoft
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
- SQL grammar [ODBC], procedure invocation
- procedure invocation [ODBC]
ms.assetid: b9ff2c3a-2003-4832-adbe-08dd0f5ad948
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 793209ab716d720266e834fcbbb846dea56950ed
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="procedure-invocation"></a>Chiamata della stored procedure
Quando viene utilizzato il driver Microsoft Access, procedure possono essere richiamate dal driver tramite il **SQLExecDirect** o **SQLPrepare** funzione con la sintassi seguente: {CHIAMARE *-nome della routine*  [(*parametro*[,*parametro*]...)]}. Si noti che le espressioni non sono supportate come parametri per una routine chiamata.  
  
 Se un nome della stored procedure include un trattino, il nome deve essere delimitato con virgolette indietro (').  
  
 Una query con parametri può essere chiamata utilizzando l'istruzione precedente.
