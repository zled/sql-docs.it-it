---
title: SQLProcedureColumns (Driver di accesso) | Documenti Microsoft
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
- Access driver [ODBC], SQLProcedureColumns
- SQLProcedureColumns function [ODBC], Access Driver
ms.assetid: 34fee995-5848-4ecb-bda0-fc362a77b2d9
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9faec06a2337e7b3a2e93769486f40e006d9d7c8
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlprocedurecolumns-access-driver"></a>SQLProcedureColumns (Driver di accesso)
> [!NOTE]  
>  In questo argomento fornisce informazioni di accesso specifici del Driver. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Gli sviluppatori di applicazioni devono cercare di colonne definite dal driver di avvio alla fine del set di risultati e procedere a ritroso.  
  
|Colonna|Commenti|  
|------------|--------------|  
|COLUMN_TYPE|SQL_PARAM_INPUT o SQL_RESULT_COL|  
|NUMERO ORDINALE|Si tratta di una colonna specifici del driver che viene restituita alla fine del set di risultati. Il tipo SQL della colonna è un numero intero.|

