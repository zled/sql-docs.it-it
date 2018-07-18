---
title: SQLColAttributes (Driver Paradox) | Documenti Microsoft
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
- SQLColAttribute function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLColAttributes
ms.assetid: bbeef024-d470-4d28-b61b-26997ef41007
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dc1714a37de4b9629098dda32beb758e5bfaa986
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32903046"
---
# <a name="sqlcolattributes-paradox-driver"></a>SQLColAttributes (Paradox Driver)
> [!NOTE]  
>  In questo argomento fornisce informazioni specifiche del Driver Paradox. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Attribute|Commenti|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|Per i dati, LONGVARBINARY SQL_COLUMN_DISPLAY_SIZE è la lunghezza massima della colonna, non la lunghezza massima della colonna per 2.|  
|SQL_OWNER_NAME|Una stringa vuota ("") in questa colonna viene restituito perché il nome del proprietario non è supportato.|  
|SQL_QUALIFIER_NAME|Viene restituito il percorso di una directory.|  
|SQL_COLUMN_SEARCHABLE|Colonne LONGVARBINARY e LONGVARCHAR vengono segnalate come SQL_UNSEARCHABLE.<br /><br /> Tipi di dati di carattere e binari a lunghezza fissa e a lunghezza variabile sono ricercabili, anche se non sono LONGVARBINARY e LONGVARCHAR.|  
  
> [!NOTE]  
>  Il precedente non è un elenco completo degli attributi restituiti da **SQLColAttributes**.
