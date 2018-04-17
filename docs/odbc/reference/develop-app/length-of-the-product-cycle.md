---
title: Lunghezza del ciclo del prodotto | Documenti Microsoft
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
- interoperability [ODBC], product cycle
- length of the product cycle [ODBC]
ms.assetid: 4d08d886-6d8b-40fd-8544-13032f4bf6c7
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7ab57383e7702b981566b67a6c1b21f3e9f767de
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="length-of-the-product-cycle"></a>Lunghezza del ciclo del prodotto
È il punto finale sull'interoperabilità. Lo sviluppo di un'applicazione interoperativa in genere richiede più tempo uno noninteroperable di sviluppo. Il motivo è che l'applicazione deve controllare funzionalità del sistema DBMS, eseguire le stesse operazioni in modo diverso per i diversi DBMS, aggirare le funzionalità supportate da alcuni DBMS, ma non altri e così via.  
  
 Oltre alla fase di sviluppo, è necessario considerare la durata del prodotto. Se l'applicazione è progettata per essere utilizzato una volta, ad esempio un'applicazione di trasferimento dei dati durante la migrazione da un DBMS a un altro, è presente alcun punto le interoperativa. L'applicazione verrà utilizzata una sola volta e rimossi.  
  
 Se l'applicazione sarà disponibile per molto tempo, potrebbe essere più facile da gestire come un'applicazione di interoperabilità. Questo vale anche per le applicazioni personalizzate che dispongono di un singolo DBMS come destinazione. Il motivo è che interoperabile codice utilizza un sottoinsieme limitato di funzionalità del database. Il driver è necessario per mantenere le funzionalità disponibili, anche in caso di modifiche al sistema DBMS sottostante. Di conseguenza, codice interoperabile può spostano il carico del supportate con le modifiche apportate al DBMS da parte dello sviluppatore dell'applicazione per gli sviluppatori di driver.
