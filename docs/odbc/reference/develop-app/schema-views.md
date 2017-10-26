---
title: Viste degli schemi | Documenti Microsoft
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
- schema views [ODBC]
- functions [ODBC], catalog functions
- catalog functions [ODBC], schema views
ms.assetid: f1dfb3e8-a7bd-46c3-92b6-c19531e8409d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 06b9546950d5ae84b6ac5811ae4413fa1841c065
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="schema-views"></a>Viste degli schemi
Un'applicazione può recuperare informazioni sui metadati da DBMS chiamando le funzioni di catalogo ODBC o le viste INFORMATION_SCHEMA. Le viste sono definite dallo standard ANSI SQL-92.  
  
 Se supportata da DBMS e il driver, le viste INFORMATION_SCHEMA forniscono un mezzo più potente e completo il recupero dei metadati che forniscono le funzioni di catalogo ODBC. Un'applicazione può eseguire personalizzati **selezionare** istruzione su una di queste visualizzazioni, è possibile unire viste, o eseguire un'unione di viste. Offrendo una vasta gamma di metadati e di maggiore utilità, viste INFORMATION_SCHEMA non sono spesso supportate dal sistema DBMS. Questo potrebbe cambiare come più DBMS e driver conseguire la conformità con SQL-92.  
  
 Per determinare quali visualizzazioni sono supportate, un'applicazione chiama **SQLGetInfo** con l'opzione SQL_INFO_SCHEMA_VIEWS. Per recuperare metadati da una vista supportata, l'applicazione esegue un **selezionare** istruzione che specifica le informazioni sullo schema richieste.

