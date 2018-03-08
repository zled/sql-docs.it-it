---
title: Conteggio record | Documenti Microsoft
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
- record count [ODBC]
- descriptors [ODBC], record count
ms.assetid: 46eec3cc-0ecc-4980-9020-fb74a9af5730
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 13834f75836157ac5aead267db63adacb6d533c0
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="record-count"></a>Conteggio record
Il campo dell'intestazione di un descrittore di SQL_DESC_COUNT è l'indice in base 1 del record numero più alto che contiene dati. Questo campo non è un conteggio di tutte le colonne o parametri associati. Quando viene allocato un descrittore, il valore iniziale di SQL_DESC_COUNT è 0.  
  
 Il driver accetta qualsiasi azione necessario per allocare e mantenere la risorsa di archiviazione necessario per contenere informazioni sul descrittore. L'applicazione in modo non esplicito specificare le dimensioni di un descrittore né allocare nuovi record. Quando l'applicazione fornisce informazioni per un record del descrittore il cui numero è maggiore del valore di SQL_DESC_COUNT, il driver aumenta automaticamente SQL_DESC_COUNT. Quando l'applicazione viene disassociato il record del descrittore numero più alto, il driver riduce automaticamente SQL_DESC_COUNT a contenere il numero del record associato rimanenti più alto.
