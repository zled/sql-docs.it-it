---
title: Gateway standard | Documenti Microsoft
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
- ODBC [ODBC], database access
- SQL [ODBC], database access
- database access [ODBC]
- standardizing database access [ODBC], gateways
- standard gateways [ODBC]
- gateways [ODBC]
ms.assetid: b8341492-2141-4bab-80bd-f2752223079e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9375bc6bf5054bdfeddd4fc5e53a1494d74eb88b
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="standard-gateway"></a>Gateway standard
Oggetto *gateway* è un componente software che causa un DBMS simile a un altro. Vale a dire, il gateway accetta l'interfaccia di programmazione, la grammatica SQL e protocollo del sistema DBMS per un singolo flusso di dati e lo converte per l'interfaccia di programmazione, la sintassi SQL, flusso di dati e protocollo del sistema DBMS nascosto. Ad esempio, le applicazioni scritte per l'utilizzo di Microsoft® SQL Server™ accessibile anche dati DB2 tramite il Gateway di DB2 Decisionware Micro; Questo prodotto provoca DB2 simile a SQL Server. Quando vengono utilizzati i gateway, un diverso gateway deve essere scritto per ogni database di destinazione.  
  
 Anche se i gateway sono limitati dalle differenze di architettura tra DBMS, sono un ottimo candidato per la standardizzazione. Tuttavia, se tutti i DBMS sono di standardizzare l'interfaccia di programmazione, la grammatica SQL e dati protocollo del flusso di un singolo DBMS, il cui DBMS è deve essere scelta come standard? Certamente non commerciale fornitore del sistema DBMS è probabile che accettano di standardizzare il prodotto. E, se un'interfaccia di programmazione standard, grammatica SQL e protocollo di flusso di dati vengono sviluppati, non è necessario alcun gateway.

