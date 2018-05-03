---
title: SQLColAttributes (Driver di File di testo) | Documenti Microsoft
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
- text file driver [ODBC], SQLColAttributes
- SQLColAttribute function [ODBC], Text File Driver
ms.assetid: 132fd1c0-1921-4a7d-910e-aedf1bff5453
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e23519c557cddc3353924c6cb285b8421a6bcc32
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlcolattributes-text-file-driver"></a>SQLColAttributes (Driver di File di testo)
> [!NOTE]  
>  In questo argomento fornisce informazioni specifiche del Driver File di testo. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Attribute|Commenti|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|Per i dati, LONGVARBINARY SQL_COLUMN_DISPLAY_SIZE è la lunghezza massima della colonna, non la lunghezza massima della colonna per 2.|  
|SQL_OWNER_NAME|Una stringa vuota ("") in questa colonna viene restituito perché il nome del proprietario non è supportato.|  
|SQL_QUALIFIER_NAME|Viene restituito il percorso di una directory.|  
|SQL_COLUMN_SEARCHABLE|Colonne LONGVARBINARY e LONGVARCHAR vengono segnalate come SQL_UNSEARCHABLE.<br /><br /> Tipi di dati di carattere e binari a lunghezza fissa e a lunghezza variabile sono ricercabili, anche se non sono LONGVARBINARY e LONGVARCHAR.|
