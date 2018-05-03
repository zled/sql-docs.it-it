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
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], IIS
- internet information services [ODBC]
- IIS [ODBC]
ms.assetid: 3328f2f1-b34a-472f-82cf-ad49768ff061
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6c1f0e1e4c21fc6e04bbaae7ec39d4b8d6ef1dd8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="using-microsoft-internet-information-services"></a>Utilizzando Microsoft Internet Information Services
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. In alternativa, utilizzare il driver ODBC fornito da Oracle.  
  
 Nel caso di problemi di connessione all'interno di uno script IIS (in particolare se si riceve un errore ORA 12641), aggiungere il file Sqlnet.ora la riga seguente:  
  
```  
SQLNET.AUTHENTICATION_SERVICES = (none)  
```  
  
 Servizi di rete sicura verrà disabilitato per la connessione utilizzando l'autenticazione anonima.
