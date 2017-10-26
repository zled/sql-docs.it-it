---
title: Posizione catalogo | Documenti Microsoft
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
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], catalog position
- catalog position [ODBC]
ms.assetid: 5bc5f64b-c75a-43d2-8745-102ec7a49000
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: dd67618a952e189a1ce7b3596f68dddd16977ae3
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="catalog-position"></a>Posizione del catalogo
La posizione di un nome di catalogo in un identificatore e la modalità è separata dal resto dell'identificatore varia da origine dati all'origine dati. Ad esempio, in un'origine dati Xbase, il nome del catalogo è una directory e, in Microsoft® Windows® è separato dal nome della tabella (che è un nome di file) da una barra rovesciata (\\). Nella figura seguente viene illustrata questa condizione.  
  
 ![Posizione catalogo: Xbase](../../../odbc/reference/develop-app/media/ch0801.gif "ch0801")  
  
 In un'origine dati di SQL Server, il catalogo è un database e separato dai nomi di tabella e dello schema da un punto (.).  
  
 ![Posizione catalogo: SQL Server](../../../odbc/reference/develop-app/media/ch0802.gif "ch0802")  
  
 In un'origine dati Oracle, il catalogo è anche il database ma segue il nome della tabella ed è separato dai nomi di tabella e dello schema da un simbolo di chiocciola (@).  
  
 ![Posizione catalogo: Oracle](../../../odbc/reference/develop-app/media/ch0803.gif "ch0803")  
  
 Per determinare il separatore di catalogo e il percorso del nome di catalogo, un'applicazione chiama **SQLGetInfo** con le opzioni SQL_CATALOG_NAME_SEPARATOR e SQL_CATALOG_LOCATION. Applicazioni interoperative devono costruire identificatori in base a questi valori.  
  
 Racchiudere tra virgolette gli identificatori che contengono più di una parte, le applicazioni necessario utilizzare le virgolette separatamente ogni parte e non utilizzare le virgolette con il carattere che separa gli identificatori. Ad esempio, l'istruzione seguente per selezionare tutte le righe e colonne di una tabella Xbase offerte del catalogo (\XBASE\SALES\CORP) e i nomi di tabella (Parts.dbf), ma non il separatore di catalogo (\\):  
  
```  
SELECT * FROM "\XBASE\SALES\CORP"\"PARTS.DBF"  
```  
  
 L'istruzione seguente per selezionare tutte le righe e colonne di una tabella Oracle offerte del catalogo (Sales), dello schema (aziendali) e i nomi di tabella (parti), ma non il catalogo (@) o separatori di schema (.):  
  
```  
SELECT * FROM "Corporate"."Parts"@"Sales"  
```  
  
 Per informazioni sull'uso di virgolette gli identificatori, vedere la sezione successiva, [identificatori tra virgolette](../../../odbc/reference/develop-app/quoted-identifiers.md).

