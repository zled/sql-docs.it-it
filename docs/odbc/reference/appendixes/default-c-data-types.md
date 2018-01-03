---
title: Tipi di dati C predefinito | Documenti Microsoft
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
- data types [ODBC], pseudo-type identifiers
- pseudo-type identifiers [ODBC], about pseudo-type identifiers
- pseudo-type identifiers [ODBC]
ms.assetid: 229140ae-af8f-4ec8-9ccf-1e92360e0bac
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 69613e528d2b0e4e660725f204d9ffd1bf3d54af
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="default-c-data-types"></a>Tipi di dati C predefinito
Se un'applicazione specifica SQL_C_DEFAULT in **SQLBindCol**, **SQLGetData**, o **SQLBindParameter**, il driver presuppone che tipo di dati C del buffer di input o output corrisponde al tipo di dati SQL della colonna o parametro a cui è associato il buffer.  
  
> [!IMPORTANT]  
>  Non utilizzare applicazioni interoperative SQL_C_DEFAULT. Al contrario, deve sempre specificano il tipo C del buffer in uso. Ecco perché i driver non possono determinare sempre correttamente il tipo C predefinito, per i motivi seguenti:  
  
-   Se il sistema DBMS Alza di livello un tipo di dati SQL di una colonna o parametro, il driver non è possibile determinare il tipo di dati SQL originale di una colonna o parametro. Pertanto, non può determinare il tipo di dati C predefinito corrispondente.  
  
-   Se il driver non è possibile determinare se una determinata colonna o un parametro è firmato, come accade spesso quando questo è gestita dal sistema DBMS, il driver non è possibile determinare se il tipo di dati C predefinito corrispondenti deve essere firmato o non firmato.  
  
     Poiché SQL_C_DEFAULT viene fornito solo per comodità programmazione, l'applicazione non perdere eventuali funzionalità quando si specifica il tipo di dati C effettivo.  
  
 Una tabella che mostra il tipo di dati C predefinito per ogni tipo di dati SQL è incluso in [la conversione di dati da SQL a tipi di dati C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md), più avanti in questa appendice.
