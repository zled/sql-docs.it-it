---
title: Limitazioni di istruzione ALTER tabella | Documenti Microsoft
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
- ODBC SQL grammar, ALTER TABLE statement limitations
- ALTER TABLE statement limitations [ODBC]
ms.assetid: f3e88f85-edf4-47cd-a822-292b106ddb34
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b3969d9c8985cadba3d8e8e4ec72986660931109
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="alter-table-statement-limitations"></a>Limitazioni di istruzione ALTER nella tabella
Quando il file dBASE o il driver Paradox viene utilizzato, dopo che un indice è stato creato e aggiunto un nuovo record, la struttura della tabella può essere modificata tramite l'istruzione ALTER TABLE solo l'indice viene eliminato e il contenuto della tabella viene eliminato.  
  
 Le istruzioni ALTER TABLE non sono supportate per i driver Microsoft Excel o testo.  
  
> [!NOTE]  
>  Quando si utilizza il driver Paradox senza implementare Borland Database Engine, le istruzioni ALTER TABLE non sono supportate. solo leggere e aggiungere le istruzioni sono consentite.
