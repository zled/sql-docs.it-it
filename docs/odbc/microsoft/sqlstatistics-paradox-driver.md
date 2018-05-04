---
title: SQLStatistics (Driver Paradox) | Documenti Microsoft
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
- Paradox driver [ODBC], SQLStatistics
- SQLStatistics function [ODBC], Paradox Driver
ms.assetid: 886cab83-d599-4fbc-9c88-e8cb833aac4b
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 18e323ff059fdeb70fcadd256728de8050eea56a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlstatistics-paradox-driver"></a>SQLStatistics (Paradox Driver)
> [!NOTE]  
>  In questo argomento fornisce informazioni specifiche del Driver Paradox. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
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
