---
title: I moduli SQL | Documenti Microsoft
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
- SQL modules [ODBC]
- sending SQL statements to DBMS [ODBC]
- SQL [ODBC], modules
- modules [ODBC]
- SQL statements [ODBC], modules
ms.assetid: 07551472-87ee-4765-951f-1364ed32f0c0
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b6e600d9b759f884e8c0ce7393380b8c4f7da5cc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sql-modules"></a>Moduli SQL
La seconda tecnica per l'invio di istruzioni SQL per il sistema DBMS è tramite moduli. In breve, un modulo è costituito da un gruppo di procedure che vengono chiamati dall'host del linguaggio di programmazione. Ogni routine contiene una sola istruzione SQL e i dati vengono passati tramite parametri da e verso la procedura.  
  
 Un modulo può essere considerato come una libreria di oggetti che è collegata al codice dell'applicazione. Tuttavia, esattamente come le procedure e il resto dell'applicazione sono collegate è dipendente dall'implementazione. Ad esempio, le procedure compilate in codice oggetto e collegate direttamente al codice dell'applicazione, può essere compilati e archiviati nel sistema DBMS e chiamate a identificatori piano inseriti nel codice dell'applicazione di accedere o potrebbe essere interpretate in fase di esecuzione.  
  
 Il vantaggio principale dei moduli è che consentono di separare correttamente le istruzioni SQL dal linguaggio di programmazione. In teoria, deve essere possibile modificare uno senza modificare l'altro e ricollegate semplicemente.
