---
title: Multithreading | Documenti Microsoft
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
- ODBC drivers [ODBC], thread-safe
- thread-safe drivers [ODBC]
- multithreaded applications [ODBC]
ms.assetid: cdfebdf5-12ff-4e28-8055-41f49b77f664
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 822dcc213a28211a15a07e1bb4586c8a14f7cdd0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="multithreading"></a>Il multithreading
Nei sistemi operativi multithread, i driver devono essere thread-safe. Ovvero, deve essere possibile per le applicazioni di utilizzare lo stesso handle su più di un thread. Come si ottiene questo risultato è specifico del driver, ed è probabile che i driver serializzerà qualsiasi tentativo di utilizzare contemporaneamente sullo stesso handle su due thread diversi.  
  
 Le applicazioni in genere utilizzano più thread anziché l'elaborazione asincrona. L'applicazione crea un thread separato, chiama una funzione ODBC su di esso e quindi continua l'elaborazione del thread principale. Anziché dover continuamente il polling di funzione asincrona, come accade quando viene utilizzato l'attributo di istruzione SQL_ATTR_ASYNC_ENABLE, l'applicazione può lasciare il thread appena creato fine.  
  
 Funzioni che accettano un handle di istruzione e sono in esecuzione su un thread possono essere annullate chiamando **SQLCancel** con la stessa istruzione handle da un altro thread. Anche se i driver non devono serializzare l'utilizzo di **SQLCancel** in questo modo, non c'è garanzia che la chiamata **SQLCancel** effettivamente annullerà la funzione in esecuzione in altri thread.
