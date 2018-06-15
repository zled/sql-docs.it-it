---
title: SQLStatistics (Driver di accesso) | Documenti Microsoft
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
- Access driver [ODBC], SQLStatistics
- SQLStatistics function [ODBC], Access Driver
ms.assetid: 6117ac77-1020-4f0c-8eed-e671c34c1f21
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f7c58b66333936a6cd8c44dba9f7e6ca7f2667a5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32902856"
---
# <a name="sqlstatistics-access-driver"></a>SQLStatistics (Driver di accesso)
> [!NOTE]  
>  In questo argomento fornisce informazioni di accesso specifici del Driver. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Colonna|Commenti|  
|------------|--------------|  
|TABLE_QUALIFIER|Viene restituito il percorso di un file di database per Microsoft Access.<br /><br /> Criteri di ricerca non sono supportato nel *szTableQualifier* argomento.|  
|TABLE_OWNER|In questa colonna, viene restituito NULL perché il nome del proprietario non è supportato.|  
|TABLE_NAME|Nome della tabella non delimitato.<br /><br /> Criteri di ricerca non sono supportato nel *szTableName* argomento.|  
|INDEX_QUALIFIER|Viene sempre restituito NULL.|  
|INDEX_NAME|Indice dipendente.|  
|TYPE|Verrà restituito solo SQL_TABLE_STAT o SQL_INDEX_OTHER per tipo.|  
|SEQ_IN_INDEX|Indice dipendente.|  
|COLUMN_NAME|Indice dipendente.|  
|COLLATION|Indice dipendente.|  
|CARDINALITY|Restituito solo per Microsoft Access.|  
|PAGES|Viene sempre restituito NULL.|  
  
 Il filtro si basa sull'univocità (la *fUnique* argomento). Il *fAccuracy* parametro viene ignorato.
