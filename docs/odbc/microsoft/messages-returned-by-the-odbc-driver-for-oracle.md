---
title: I messaggi restituiti dal Driver ODBC per Oracle | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- error messages [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], error messages
ms.assetid: 150bde1d-adb6-4e77-90e9-4dc93499a746
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4425c814fb8814ec1ef7822d4642ccf6fcc0dd70
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47719669"
---
# <a name="messages-returned-by-the-odbc-driver-for-oracle"></a>Messaggi restituiti dal driver ODBC per Oracle
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. In alternativa, usare il driver ODBC fornito da Oracle.  
  
 Se un messaggio di errore Oracle è disponibile, verrà restituito preceduti da [Microsoft] [Driver ODBC per Oracle], [Oracle] tag; e in caso contrario, viene restituito il messaggio senza tag [Oracle] come negli esempi seguenti:  
  
## <a name="oracle-error-message"></a>Messaggio di errore Oracle:  
  
```  
[Microsoft][ODBC driver for Oracle][Oracle]ORA-nnnnn message-text  
```  
  
## <a name="odbc-driver-for-oracle-error-message"></a>Driver ODBC per il messaggio di errore Oracle:  
  
```  
[Microsoft][ODBC driver for Oracle]  
```
