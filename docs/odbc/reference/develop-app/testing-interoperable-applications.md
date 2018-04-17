---
title: Test delle applicazioni interoperabili | Documenti Microsoft
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
- interoperability [ODBC], testing interoperable applications
- testing interoperable applications [ODBC]
ms.assetid: 489083cb-8430-40be-9ef2-d75b9a2eea88
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4cd98e6311d7d08b6faed0cb4759523642e70a5d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="testing-interoperable-applications"></a>Test delle applicazioni interoperabili
Test delle applicazioni interoperabili è nella migliore delle ipotesi una lunga nel peggiore dei casi è possibile poiché i nuovi driver continuamente vengono visualizzati sul mercato e dell'azienda. Tuttavia, un livello ragionevole di test è possibile. Solo le applicazioni con bassa o limitato interoperabilità necessitano testate con i driver che sono garantisce il supporto. Tuttavia, essi devono essere completamente testati rispetto a tali driver.  
  
 Applicazioni altamente interoperabile non possono essere testate praticamente tutti i driver. Il miglior che è possono eseguire la maggior parte degli sviluppatori di applicazioni è per testarle completamente da un numero ridotto di driver e cursorily da diverse altre. Driver certificati devono includere i driver più comuni per il DBMS più comuni nel mercato dell'applicazione; Se sul mercato copre tutti i DBMS, è necessario testare i driver per i desktop e server DBMS.  
  
 Uno dei problemi nel test le applicazioni ODBC è il numero di componenti coinvolti: l'applicazione stessa, gestione Driver, il driver, il DBMS e di software di rete probabilmente o gateway. Le applicazioni possono rendere più semplice tenere traccia degli errori inviando i messaggi di errore restituiti dalle funzioni ODBC tramite **SQLGetDiagField** e **SQLGetDiagRec**. Questi messaggi identificano il produttore e il componente in cui si verificano errori. Per ulteriori informazioni, vedere [diagnostica](../../../odbc/reference/develop-app/diagnostics.md).
