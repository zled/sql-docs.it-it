---
title: Chiamata della stored procedure | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL grammar [ODBC], procedure invocation
- procedure invocation [ODBC]
ms.assetid: b9ff2c3a-2003-4832-adbe-08dd0f5ad948
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6eb0abafb72b0acd9424a31205771c91edbc5529
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="procedure-invocation"></a>Chiamata della stored procedure
Quando viene utilizzato il driver Microsoft Access, procedure possono essere richiamate dal driver tramite il **SQLExecDirect** o **SQLPrepare** funzione con la sintassi seguente: {CHIAMARE *-nome della routine*  [(*parametro*[,*parametro*]...)]}. Si noti che le espressioni non sono supportate come parametri per una routine chiamata.  
  
 Se un nome della stored procedure include un trattino, il nome deve essere delimitato con virgolette indietro (').  
  
 Una query con parametri può essere chiamata utilizzando l'istruzione precedente.
