---
title: I record di diagnostica | Documenti Microsoft
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
- diagnostic information [ODBC], diagnostic records
- handles [ODBC], diagnostic records
- header records [ODBC]
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 92c73f9b-3ed7-410d-9cec-2771004aae60
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d6395d87e5691dc33b5a08267ef83c459f94c0d1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32909316"
---
# <a name="diagnostic-records"></a>Record di diagnostica
Associato a ogni ambiente, connessione, l'istruzione e handle di descrittore sono *i record di diagnostica*. Questi record contengono informazioni di diagnostica relative l'ultima funzione chiamata che è usato un handle specifico. I record vengono sostituiti solo quando viene chiamata un'altra funzione utilizzando l'handle. Non sussiste alcun limite al numero di record di diagnostica che possono essere archiviati in qualsiasi momento.  
  
 Esistono due tipi di record di diagnostica: un *record di intestazione* e zero o più *record di stato*. Il record di intestazione è 0; i record di stato sono record 1 e versioni successive. I record di diagnostica sono costituiti da un numero di campi distinti, che sono diverse per il record di intestazione e il record di stato. Inoltre, i componenti ODBC è possono definire i propri campi di record di diagnostica.  
  
 Sebbene i record di diagnostica possono essere considerati come strutture, non vi è alcun requisito per poter essere effettivamente strutture. come un driver archivia le informazioni di diagnostica è specifico del driver.  
  
 I campi dei record di diagnostica vengono recuperati con **SQLGetDiagField**. I campi di messaggio di diagnostica di record di stato, numero di errore nativo e SQLSTATE possono essere recuperati in una singola chiamata con **SQLGetDiagRec**.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Record di intestazione](../../../odbc/reference/develop-app/header-record.md)  
  
-   [Record di stato](../../../odbc/reference/develop-app/status-records.md)
