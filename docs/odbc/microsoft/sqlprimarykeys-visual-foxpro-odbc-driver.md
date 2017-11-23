---
title: SQLPrimaryKeys (Driver ODBC di Visual FoxPro) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQLPrimaryKeys function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 8dbe2903-efdc-45e0-a079-9e357c5fd81b
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e0d7c874fe97f70f5e8d8096a4b03a2f064f2cb1
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
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
