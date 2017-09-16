---
title: Handle di connessione | Documenti Microsoft
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
- connection handles [ODBC]
- handles [ODBC], connection
ms.assetid: 12222653-f04d-46d6-bdee-61348f5d550f
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ba20d3fcb6d943f4669774013dcb62c8ad896d8d
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="connection-handles"></a>Handle di connessione
Oggetto *connessione* è costituito da un driver e un'origine dati. Un handle di connessione identifica ogni connessione. Consente di definire l'handle di connessione non solo driver da utilizzare, ma l'origine dati da utilizzare con il driver. All'interno di un segmento di codice che implementa ODBC (Driver Manager o un driver), l'handle di connessione identifica una struttura contenente informazioni di connessione, ad esempio le operazioni seguenti:  
  
-   Lo stato della connessione  
  
-   La diagnostica a livello di connessione corrente  
  
-   Gli handle di istruzioni e descrittori allocati per la connessione  
  
-   Le impostazioni correnti di ogni attributo di connessione  
  
 ODBC non impedisce più connessioni simultanee, se il driver supportarle. Pertanto, in un particolare ambiente ODBC, più handle di connessione potrebbero fare riferimento a un'ampia gamma di driver e origini dati per lo stesso driver e una varietà di origini dati o anche a più connessioni allo stesso driver e origine dati. Alcuni driver limitare il numero di connessioni attive che supportano; opzione di SQL_MAX_DRIVER_CONNECTIONS **SQLGetInfo** specifica il numero di connessioni attivo supporta un driver specifico.  
  
 Handle di connessione vengono utilizzati principalmente per la connessione all'origine dati (**SQLConnect**, **SQLDriverConnect**, o **SQLBrowseConnect**), disconnessione dai dati origine (**SQLDisconnect**), recupero di informazioni sull'origine dati e i driver (**SQLGetInfo**), il recupero di diagnostica (**SQLGetDiagField** e **SQLGetDiagRec**) e l'esecuzione di transazioni (**SQLEndTran**). Vengono inoltre utilizzati durante l'impostazione e recupero degli attributi di connessione (**SQLSetConnectAttr** e **SQLGetConnectAttr**) e quando si ottiene il formato nativo di un'istruzione SQL (**SQLNativeSql **).  
  
 Handle di connessione vengono allocati con **SQLAllocHandle** e liberata con **SQLFreeHandle**.
