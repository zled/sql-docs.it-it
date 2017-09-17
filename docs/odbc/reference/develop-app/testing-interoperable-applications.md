---
title: Test delle applicazioni interoperabili | Documenti Microsoft
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
- interoperability [ODBC], testing interoperable applications
- testing interoperable applications [ODBC]
ms.assetid: 489083cb-8430-40be-9ef2-d75b9a2eea88
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d36c443cb6bc4a189006a3d63e90deead3f11e66
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="testing-interoperable-applications"></a>Test delle applicazioni interoperabili
Test delle applicazioni interoperabili è nella migliore delle ipotesi una lunga nel peggiore dei casi è possibile poiché i nuovi driver continuamente vengono visualizzati sul mercato e dell'azienda. Tuttavia, un livello ragionevole di test è possibile. Solo le applicazioni con bassa o limitato interoperabilità necessitano testate con i driver che sono garantisce il supporto. Tuttavia, essi devono essere completamente testati rispetto a tali driver.  
  
 Applicazioni altamente interoperabile non possono essere testate praticamente tutti i driver. Il miglior che è possono eseguire la maggior parte degli sviluppatori di applicazioni è per testarle completamente da un numero ridotto di driver e cursorily da diverse altre. Driver certificati devono includere i driver più comuni per il DBMS più comuni nel mercato dell'applicazione; Se sul mercato copre tutti i DBMS, è necessario testare i driver per i desktop e server DBMS.  
  
 Uno dei problemi nel test le applicazioni ODBC è il numero di componenti coinvolti: l'applicazione stessa, gestione Driver, il driver, il DBMS e di software di rete probabilmente o gateway. Le applicazioni possono rendere più semplice tenere traccia degli errori inviando i messaggi di errore restituiti dalle funzioni ODBC tramite **SQLGetDiagField** e **SQLGetDiagRec**. Questi messaggi identificano il produttore e il componente in cui si verificano errori. Per ulteriori informazioni, vedere [diagnostica](../../../odbc/reference/develop-app/diagnostics.md).
