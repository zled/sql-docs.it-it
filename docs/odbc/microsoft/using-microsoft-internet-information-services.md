---
title: Utilizzando Microsoft Internet Information Services | Documenti Microsoft
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
- ODBC driver for Oracle [ODBC], IIS
- internet information services [ODBC]
- IIS [ODBC]
ms.assetid: 3328f2f1-b34a-472f-82cf-ad49768ff061
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d3975d0a51282e9fda7a649b6eeff63dd83a045e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="using-microsoft-internet-information-services"></a>Utilizzando Microsoft Internet Information Services
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. In alternativa, utilizzare il driver ODBC fornito da Oracle.  
  
 Nel caso di problemi di connessione all'interno di uno script IIS (in particolare se si riceve un errore ORA 12641), aggiungere il file Sqlnet.ora la riga seguente:  
  
```  
SQLNET.AUTHENTICATION_SERVICES = (none)  
```  
  
 Servizi di rete sicura verrà disabilitato per la connessione utilizzando l'autenticazione anonima.
