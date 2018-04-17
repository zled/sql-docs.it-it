---
title: Limitazioni di istruzione ALTER tabella | Documenti Microsoft
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
ms.topic: article
helpviewer_keywords:
- ODBC SQL grammar, ALTER TABLE statement limitations
- ALTER TABLE statement limitations [ODBC]
ms.assetid: f3e88f85-edf4-47cd-a822-292b106ddb34
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 06af545611da90d51ad0fc82136a4cb1ecc3984c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="alter-table-statement-limitations"></a>Limitazioni di istruzione ALTER nella tabella
Quando il file dBASE o il driver Paradox viene utilizzato, dopo che un indice è stato creato e aggiunto un nuovo record, la struttura della tabella può essere modificata tramite l'istruzione ALTER TABLE solo l'indice viene eliminato e il contenuto della tabella viene eliminato.  
  
 Le istruzioni ALTER TABLE non sono supportate per i driver Microsoft Excel o testo.  
  
> [!NOTE]  
>  Quando si utilizza il driver Paradox senza implementare Borland Database Engine, le istruzioni ALTER TABLE non sono supportate. solo leggere e aggiungere le istruzioni sono consentite.
