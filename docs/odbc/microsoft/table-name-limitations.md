---
title: Limitazioni per i nomi di tabella | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC SQL grammar, table name limitations
- table name limitations [ODBC]
- Excel driver [ODBC], table name limitations
ms.assetid: d9843e4b-1d05-4d5a-9dc3-ee9ec59edb97
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b001db50394ea1e9cf7c52d9519294fb66dbcdfc
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="table-name-limitations"></a>Limitazioni di nomi di tabella
I nomi di tabella possono contenere qualsiasi carattere validi (ad esempio, spazi). Se i nomi delle tabelle contengono caratteri tranne lettere, numeri e caratteri di sottolineatura, il nome deve essere delimitato racchiudendolo tra virgolette indietro (').  
  
 Quando viene utilizzato il driver Microsoft Excel e un nome di tabella non è qualificato tramite un riferimento al database, il database predefinito è implicito. Se un nome in Microsoft Excel include il "!" carattere, verrà automaticamente tradotto per il carattere "$" invece.  
  
 Il nome della tabella di Microsoft Excel che fa riferimento a \<filename > è supportato per Microsoft Excel 3.0 e 4.0 file. Il nome della tabella di Microsoft Excel che fa riferimento a \<nome di cartella di lavoro > è supportato per i file di Microsoft Excel 97 5.0 o 7.0.  
  
 Quando viene utilizzato il driver dBASE, caratteri con un valore ASCII maggiore di 127 vengono convertiti in caratteri di sottolineatura.  
  
 Quando viene utilizzato il driver Microsoft Access, il nome della tabella è limitato a 64 caratteri.  
  
 Quando viene utilizzato il driver di Microsoft Excel versione 3.0 o 4.0, Paradox o testo, dBASE, parole chiave MS-DOS speciali CON, AUX, LPT1 e LPT2 non utilizzare come nomi di tabella.
