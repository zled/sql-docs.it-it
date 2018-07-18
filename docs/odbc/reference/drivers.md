---
title: Driver | Documenti Microsoft
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
- ODBC architecture [ODBC], drivers
- drivers [ODBC]
- drivers [ODBC], about drivers
ms.assetid: d6795d92-877e-44e1-b7d5-2ff2fd3989bd
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1906e61847537d3c89a5f2c3529172a9634713c0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32915196"
---
# <a name="drivers"></a>Driver
*I driver* sono librerie che implementano le funzioni dell'API ODBC. Ognuno è specifico per un determinato DBMS; ad esempio, un driver per Oracle non può accedere direttamente i dati in un DBMS Informix. I driver di espongono le funzionalità del DBMS sottostante; che non sono necessari per implementare funzionalità non supportate dal sistema DBMS. Ad esempio, se il sistema DBMS sottostante non supporta gli operatori outer join, quindi non deve essere il driver. L'eccezione principale è che i driver per DBMS che non dispongono di motori di database autonomo, ad esempio Xbase, devono implementare un motore di database che supporta almeno una quantità minima di SQL.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Attività dei driver](../../odbc/reference/driver-tasks.md)  
  
-   [Architettura dei driver](../../odbc/reference/driver-architecture.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Driver ODBC forniti da Microsoft](../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)
