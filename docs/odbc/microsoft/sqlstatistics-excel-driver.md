---
title: SQLStatistics (Driver per Excel) | Documenti Microsoft
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
- Excel driver [ODBC], SQLStatistics
- SQLStatistics function [ODBC], Excel Driver
ms.assetid: 02506664-8dcc-4bd0-a8bb-d49fcbdd5722
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3e0ca371de4c7d81847be076761e8ce4d0beafd2
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlstatistics-excel-driver"></a>SQLStatistics (Driver per Excel)
> [!NOTE]  
>  In questo argomento fornisce informazioni specifiche del Driver Excel. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Colonna|Commenti|  
|------------|--------------|  
|TABLE_QUALIFIER|Il percorso di una directory.<br /><br /> Criteri di ricerca non sono supportato nel *szTableQualifier* argomento.|  
|TABLE_OWNER|In questa colonna viene restituito NULL perché il nome del proprietario non è supportato.|  
|TABLE_NAME|Nome della tabella non delimitato.<br /><br /> Criteri di ricerca non sono supportato nel *szTableName* argomento.|  
|INDEX_QUALIFIER|Viene sempre restituito NULL.|  
|INDEX_NAME|Indice dipendente.|  
|TYPE|Verrà restituito solo SQL_TABLE_STAT o SQL_INDEX_OTHER per tipo.|  
|SEQ_IN_INDEX|Indice dipendente.|  
|COLUMN_NAME|Indice dipendente.|  
|COLLATION|Indice dipendente.|  
|PAGES|Viene sempre restituito NULL.|  
  
 Il filtro si basa sull'univocità (la *fUnique* argomento). Il *fAccuracy* parametro viene ignorato.

