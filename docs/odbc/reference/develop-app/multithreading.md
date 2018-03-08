---
title: Multithreading | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC drivers [ODBC], thread-safe
- thread-safe drivers [ODBC]
- multithreaded applications [ODBC]
ms.assetid: cdfebdf5-12ff-4e28-8055-41f49b77f664
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 72cc8fd918c8ba69a0eb52f9739abeb3728c425d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="multithreading"></a>Il multithreading
Nei sistemi operativi multithread, i driver devono essere thread-safe. Ovvero, deve essere possibile per le applicazioni di utilizzare lo stesso handle su più di un thread. Come si ottiene questo risultato è specifico del driver, ed è probabile che i driver serializzerà qualsiasi tentativo di utilizzare contemporaneamente sullo stesso handle su due thread diversi.  
  
 Le applicazioni in genere utilizzano più thread anziché l'elaborazione asincrona. L'applicazione crea un thread separato, chiama una funzione ODBC su di esso e quindi continua l'elaborazione del thread principale. Anziché dover continuamente il polling di funzione asincrona, come accade quando viene utilizzato l'attributo di istruzione SQL_ATTR_ASYNC_ENABLE, l'applicazione può lasciare il thread appena creato fine.  
  
 Funzioni che accettano un handle di istruzione e sono in esecuzione su un thread possono essere annullate chiamando **SQLCancel** con la stessa istruzione handle da un altro thread. Anche se i driver non devono serializzare l'utilizzo di **SQLCancel** in questo modo, non c'è garanzia che la chiamata **SQLCancel** effettivamente annullerà la funzione in esecuzione in altri thread.
