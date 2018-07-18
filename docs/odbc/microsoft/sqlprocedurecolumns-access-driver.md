---
title: SQLProcedureColumns (Driver di accesso) | Documenti Microsoft
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
- Access driver [ODBC], SQLProcedureColumns
- SQLProcedureColumns function [ODBC], Access Driver
ms.assetid: 34fee995-5848-4ecb-bda0-fc362a77b2d9
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c8a2f1fc2a37dcdce65a145eec966d3b118bf734
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32902146"
---
# <a name="sqlprocedurecolumns-access-driver"></a>SQLProcedureColumns (Driver di accesso)
> [!NOTE]  
>  In questo argomento fornisce informazioni di accesso specifici del Driver. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Gli sviluppatori di applicazioni devono cercare di colonne definite dal driver di avvio alla fine del set di risultati e procedere a ritroso.  
  
|Colonna|Commenti|  
|------------|--------------|  
|COLUMN_TYPE|SQL_PARAM_INPUT o SQL_RESULT_COL|  
|NUMERO ORDINALE|Si tratta di una colonna specifici del driver che viene restituita alla fine del set di risultati. Il tipo SQL della colonna è un numero intero.|
