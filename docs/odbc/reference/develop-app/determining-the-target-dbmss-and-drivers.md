---
title: Determinare il DBMS di destinazione e i driver | Documenti Microsoft
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
- target DBMSs and drivers in interoperability [ODBC]
- interoperability [ODBC], target dbmss and drivers
ms.assetid: 23bee0f6-e12a-4598-b34e-df11a8086829
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f275e344b49f62f1ecc55430c603c0f31f333aa6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="determining-the-target-dbmss-and-drivers"></a>Determinare il DBMS di destinazione e i driver
Domanda successiva da considerare è, quali sono il DBMS di destinazione per l'applicazione e i driver sono disponibili che supportano tali DBMS? Poiché le applicazioni generiche tendono a essere estremamente interoperativi, la domanda di DBMS di destinazione è più applicabile alle applicazioni personalizzate e verticale. Tuttavia, la domanda di driver di destinazione si applica a tutte le applicazioni, poiché i driver variano notevolmente in velocità, la qualità, supporto delle funzionalità e disponibilità. Inoltre, se i driver devono essere ridistribuito con l'applicazione, il costo e la disponibilità di piani di contratti multilicenza necessario essere considerato.  
  
 Per molte applicazioni personalizzate il DBMS di destinazione sono evidenti: essi sono esistenti DBMS che l'applicazione è progettata per accedere. Deve essere considerato DBMS a cui è pianificata la migrazione futura. Tuttavia, la domanda principale per queste applicazioni è che i driver da utilizzare con essi. Per le altre applicazioni personalizzate, ovvero quelli che non sono progettati per accedere a un DBMS esistente, ovvero il DBMS di destinazione può essere scelto in base al supporto delle funzionalità, supporto simultaneo degli utenti, la disponibilità di driver e convenienza.  
  
 Per le applicazioni verticali, la destinazione del che DBMS in genere vengono scelti basato sul supporto delle funzionalità, la disponibilità di driver e sul mercato. Ad esempio, un'applicazione verticale progettata per le piccole imprese deve avere come destinazione DBMS che sono accessibili a tali aziende; un'applicazione verticale progettata come un componente aggiuntivo esistente DBMS di destinazione deve essere ampiamente utilizzato DBMS.  
  
 Quando si sceglie di DBMS di destinazione, è necessario considerare le differenze tra i database desktop e server. I database desktop, ad esempio dBASE, Paradox e Btrieve sono meno potenti rispetto ai database del server. Poiché in genere avviene tramite motori di SQL meno potenti trovati nel driver basati su più file, spesso non includono il supporto delle transazioni pieno, supportano un numero di utenti simultaneo e non dispongono di SQL. Tuttavia, sono economiche e disporre di una base installata di grandi dimensioni.  
  
 Server database, ad esempio Oracle, DB2 e SQL Server forniscono il supporto delle transazioni pieno, supportano molti utenti simultanei e avere SQL completo. Sono molto più costosi e disporre di una base installata più piccoli. D'altra parte, i prezzi di software tendono a essere superiore, in qualche modo offset di un mercato potenziale più piccolo.  
  
 Di conseguenza, destinazione DBMS a volte può essere scelto in base le funzionalità necessarie per l'applicazione e di mercato di destinazione dell'applicazione. Ad esempio, un sistema di immissione dell'ordine per le aziende di grandi dimensioni potrebbe non essere destinati database desktop perché questi non dispongono di supporto delle transazioni sufficiente. Un simile sistema progettato per le piccole imprese potrebbe escludere la maggior parte dei database del server in base al costo. Ma gli sviluppatori di applicazioni generiche potrebbe essere destinate a evitare di utilizzare le funzionalità avanzate disponibili nel database del server.
