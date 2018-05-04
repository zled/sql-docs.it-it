---
title: Chiamata a livello di interfacce | Documenti Microsoft
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
- SQL statements [ODBC], CLI
- CLI [ODBC], using CLI
- sending SQL statements to DBMS [ODBC]
- SQL [ODBC], CLI
- call-level interface [ODBC], using call-level interface
ms.assetid: 42257bb6-0bf1-4533-a4ef-4a6dd2aecb18
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5df7ff90e8b290f6fb55f1c62b59eee10d83cd8e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="call-level-interfaces"></a>Interfacce a livello di chiamata
La tecnica finale per l'invio di istruzioni SQL per il sistema DBMS è tramite un'interfaccia a livello di chiamata (CLI). Un'interfaccia a livello di chiamata fornisce una libreria di funzioni di sistema DBMS che può essere chiamato dall'applicazione. Pertanto, anziché tentare di blend SQL con un altro linguaggio di programmazione, un'interfaccia a livello di chiamata è simile alle routine librerie che la maggior parte dei programmatori sono abituati a usare, ad esempio la stringa, i/o o librerie matematiche in C. Notare che DBMS che supportano SQL incorporato dispone già di un'interfaccia a livello di chiamata, le chiamate a cui vengono generate dallo strumento di precompilazione. Tuttavia, queste chiamate sono non documentato e soggetto a modifiche senza preavviso.  
  
 Interfacce a livello di chiamata vengono comunemente utilizzate nelle architetture client/server, in cui si trova il programma di applicazione (client) in un computer e il sistema DBMS (server) risiede in un computer diverso. L'applicazione chiama le funzioni CLI nel sistema locale, e tali chiamate vengono inviate attraverso la rete per il sistema DBMS per l'elaborazione.  
  
 Un'interfaccia a livello di chiamata è simile a codice SQL dinamico, in istruzioni SQL vengono passate al DBMS per l'elaborazione in fase di esecuzione, ma differisce da embedded SQL nel suo complesso che non sono presenti istruzioni SQL incorporate e non precompilatore è obbligatorio.  
  
 Utilizzo di un'interfaccia a livello di chiamata in genere prevede i passaggi seguenti:  
  
1.  L'applicazione chiama una funzione CLI a cui connettersi nel sistema DBMS.  
  
2.  L'applicazione genera un'istruzione SQL e lo inserisce in un buffer. Chiama quindi uno o più funzioni CLI per inviare l'istruzione del sistema DBMS per la preparazione e l'esecuzione.  
  
3.  Se l'istruzione è un'istruzione SELECT, l'applicazione chiama una funzione CLI per restituire i risultati nel buffer dell'applicazione. In genere, questa funzione restituisce una riga o una colonna di dati alla volta.  
  
4.  L'applicazione chiama una funzione CLI per disconnettersi dal sistema DBMS.
