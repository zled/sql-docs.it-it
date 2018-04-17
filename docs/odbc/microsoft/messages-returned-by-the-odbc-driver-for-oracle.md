---
title: I messaggi restituiti dal Driver ODBC per Oracle | Documenti Microsoft
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
- error messages [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], error messages
ms.assetid: 150bde1d-adb6-4e77-90e9-4dc93499a746
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 067300b35282b39c63504f6f8e3a16fd3e1a8c00
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="messages-returned-by-the-odbc-driver-for-oracle"></a>Messaggi restituiti dal Driver ODBC per Oracle
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. In alternativa, utilizzare il driver ODBC fornito da Oracle.  
  
 Se un messaggio di errore Oracle è disponibile, verrà restituito preceduto da [Microsoft] [Driver ODBC per Oracle,] e [Oracle]; in caso contrario, viene restituito il messaggio senza tag [Oracle] come negli esempi seguenti:  
  
## <a name="oracle-error-message"></a>Messaggio di errore Oracle:  
  
```  
[Microsoft][ODBC driver for Oracle][Oracle]ORA-nnnnn message-text  
```  
  
## <a name="odbc-driver-for-oracle-error-message"></a>Driver ODBC per il messaggio di errore Oracle:  
  
```  
[Microsoft][ODBC driver for Oracle]  
```
