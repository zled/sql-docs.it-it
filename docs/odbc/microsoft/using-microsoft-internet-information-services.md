---
title: Utilizzando Microsoft Internet Information Services | Documenti Microsoft
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
- ODBC driver for Oracle [ODBC], IIS
- internet information services [ODBC]
- IIS [ODBC]
ms.assetid: 3328f2f1-b34a-472f-82cf-ad49768ff061
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 75659769b4d0318fa21494a3f2ca3262836c69eb
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="using-microsoft-internet-information-services"></a>Utilizzando Microsoft Internet Information Services
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. In alternativa, utilizzare il driver ODBC fornito da Oracle.  
  
 Nel caso di problemi di connessione all'interno di uno script IIS (in particolare se si riceve un errore ORA 12641), aggiungere il file Sqlnet.ora la riga seguente:  
  
```  
SQLNET.AUTHENTICATION_SERVICES = (none)  
```  
  
 Servizi di rete sicura verrà disabilitato per la connessione utilizzando l'autenticazione anonima.

