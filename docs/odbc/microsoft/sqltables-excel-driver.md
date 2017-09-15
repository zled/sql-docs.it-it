---
title: SQLTables (Driver per Excel) | Documenti Microsoft
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
- Excel driver [ODBC], SQLTables
- SQLTables function [ODBC], Excel Driver
ms.assetid: 9410b686-4b5b-4b51-b5ef-f9d2e7a48faa
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9aad9b74b9813c0526df87437999b66f27e95414
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqltables-excel-driver"></a>SQLTables (Driver per Excel)
> [!NOTE]  
>  In questo argomento fornisce informazioni specifiche del Driver Excel. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Argomento|Commenti|  
|--------------|--------------|  
|*szTableOwner*|L'argomento valido solo per *szTableOwner* è NULL perché nessuno dei driver supporta i nomi dei proprietari. Con *szTableOwner* impostato su NULL, vengono restituite tutte le tabelle. Nella colonna TABLE_OWNER viene restituito NULL.|  
|*szTableQualifier*|Quando Microsoft Excel 3.0 o 4.0 driver viene usato, se si chiama **SQLTables** con un valore per *szTableQualifier* che non è il nome di una tabella esistente, il driver creerà una tabella con lo stesso nome.<br /><br /> Nella colonna TABLE_QUALIFIER **SQLTables** restituirà il percorso in una directory.|  
|*SzTableType*|Per Microsoft Excel 3.0 o 4.0, "TABLE" è l'unico tipo di tabella è supportato.<br /><br /> Per le versioni successive dei file di Microsoft Excel, viene restituita "Tabella di sistema" per i nomi dei fogli (le tabelle con "$" alla fine) e viene restituito "TABLE" per le tabelle all'interno di fogli di lavoro.|
