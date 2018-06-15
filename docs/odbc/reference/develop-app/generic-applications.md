---
title: Applicazioni generiche | Documenti Microsoft
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
- interoperability [ODBC], generic applications
- interoperability [ODBC], levels
- generic applications [ODBC]
ms.assetid: dda2a3c4-76ef-40a6-b3a1-9e95bed61618
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ae9643de106e11865505483d84f2253fb9511227
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32909526"
---
# <a name="generic-applications"></a>Applicazioni generiche
Applicazioni generiche, talvolta, eseguire un'attività a livello di codice, ad esempio un foglio di calcolo il recupero dei dati da un database. Potrebbe inoltre eseguono una serie di attività definite dall'utente, ad esempio un'applicazione di query generico consentendo all'utente di immettere ed eseguire un'istruzione SQL. Le applicazioni generiche hanno in comune è che questi devono funzionare con un'ampia gamma di diversi DBMS e che lo sviluppatore non conosce in anticipo questi DBMS.  
  
 Pertanto, applicazioni generiche devono essere estremamente interoperativi. Lo sviluppatore deve effettuare numerose opzioni, raggiungendo un compromesso interoperabilità per le funzionalità tra e necessario scrivere codice che prevede che i driver per supportare un'ampia gamma di funzionalità. Mentre le applicazioni generiche potrebbero essere ottimizzate per l'utilizzo di DBMS comuni, raramente contengono codice specifico del driver o specifici del DBMS.
