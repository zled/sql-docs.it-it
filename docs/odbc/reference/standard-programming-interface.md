---
title: Interfaccia di programmazione standard | Documenti Microsoft
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
- ODBC [ODBC], database access
- SQL [ODBC], database access
- database access [ODBC]
- standardizing database access [ODBC], programming interface
- programming interface standardization [ODBC]
ms.assetid: a2fa727e-51f2-4123-ae25-0ee28e611231
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 235d61849f28b29af7ec0b9ba67fe86b38bf8239
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="standard-programming-interface"></a>Interfaccia di programmazione standard
L'interfaccia di programmazione è ad esempio più evidente candidato per la standardizzazione. Infatti, quando viene sviluppato ODBC, ANSI e ISO già fornito standard per incorporati e SQL moduli. Anche se non esiste standard per un database CLI, il gruppo di accesso di SQL, ovvero un consorzio di settore di fornitori di database: stato si prende in considerazione per crearne uno; parti di ODBC in un secondo momento è diventata la base per il proprio lavoro.  
  
 Uno dei requisiti per ODBC è che una singola applicazione binaria era necessario usare più DBMS. È per questo motivo che ODBC non utilizza incorporate lingue SQL o un modulo. Sebbene il linguaggio nei linguaggi SQL e modulo incorporati standardizzato, ognuno è correlato alla precompilers specifici del DBMS. Pertanto, è necessario ricompilare le applicazioni per ogni sistema DBMS e i file binari risultanti funzionano solo con un singolo DBMS. Sebbene sia accettabile per le applicazioni di scarso trovate nel mondo minicomputer e mainframe, non è accettabile nel mondo personal computer. Innanzitutto, si tratta di un notevole problema logistico per offrire più versioni di volumi elevati, il software ai clienti; in secondo luogo, applicazioni per personal computer spesso necessario accedere contemporaneamente a più DBMS.  
  
 D'altra parte, è possibile implementare un'interfaccia a livello di chiamata tramite librerie o driver di database, che si trovano su ciascun computer locale. un driver diverso è necessario per ogni sistema DBMS. Poiché i sistemi operativi moderni possono caricare tali librerie (ad esempio librerie a collegamento dinamico nel sistema operativo Microsoft® Windows®) in fase di esecuzione, una singola applicazione può accedere ai dati dai diversi DBMS senza ricompilazione e può anche accedere ai dati da più database contemporaneamente. Quando sono disponibili i nuovi driver di database, gli utenti possono solo installare questi nei propri computer senza dover modificare, compilare o ricollegare le applicazioni di database. Inoltre, un'interfaccia a livello di chiamata non è un buon candidato per ODBC perché Windows, la piattaforma per cui è stato originariamente sviluppato ODBC: estensivo di tali librerie è necessario crearle.
