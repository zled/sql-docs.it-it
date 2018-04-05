---
title: SQLPrimaryKeys (Driver ODBC di Visual FoxPro) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLPrimaryKeys function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 8dbe2903-efdc-45e0-a079-9e357c5fd81b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e89d07b2cb622c42ed6f18c10d3498c9df52323f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sqlprimarykeys-visual-foxpro-odbc-driver"></a>SQLPrimaryKeys (Driver ODBC di Visual FoxPro)
> [!NOTE]  
>  In questo argomento contiene informazioni specifiche del Driver ODBC Visual FoxPro. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Supporto: completo  
  
 Conformità di API ODBC: Livello 2  
  
 Restituisce i nomi delle colonne che costituiscono la chiave primaria per una tabella. L'implementazione di Visual FoxPro il Driver ODBC di **SQLPrimaryKeys** si comporta come segue:  
  
-   Ignora il *szTableOwner* e *cbTableOwner* argomenti.  
  
-   Funziona solo per le origini dati che sono [database](../../odbc/microsoft/visual-foxpro-terminology.md). Il driver restituisce l'errore "Driver non supporta questa funzione" se l'origine dati è una directory di [libero tabelle](../../odbc/microsoft/visual-foxpro-terminology.md).  
  
 Per ulteriori informazioni, vedere [SQLPrimaryKeys](../../odbc/reference/syntax/sqlprimarykeys-function.md) nel *riferimento per programmatori ODBC*.
