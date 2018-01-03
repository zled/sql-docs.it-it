---
title: SQLGetTypeInfo (Driver ODBC di Visual FoxPro) | Documenti Microsoft
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
helpviewer_keywords: SQLGetTypeInfo function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5f25e20b-a4ef-42da-aeb6-00e0510fb1cc
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2e552a73289da6d78223b6416b7be7fe125e23e7
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sqlgettypeinfo-visual-foxpro-odbc-driver"></a>SQLGetTypeInfo (Driver ODBC di Visual FoxPro)
> [!NOTE]  
>  In questo argomento contiene informazioni specifiche del Driver ODBC Visual FoxPro. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Supporto: completo  
  
 Conformità di API ODBC: Livello 1  
  
 Restituisce informazioni sui tipi di dati supportati da un'origine dati. Il driver restituisce le informazioni in un set di risultati SQL. Nella tabella seguente sono elencati i tipi di dati ODBC e il tipo di dati Visual FoxPro corrispondente.  
  
|Tipo ODBC|Tipo di Visual FoxPro|  
|---------------|------------------------|  
|SQL_BIGINT|Non supportato. Tipo non è a 64 bit di Visual FoxPro.|  
|SQL_BIT|Logico|  
|SQL_CHAR|Carattere|  
|SQL_DATE|date|  
|SQL_DECIMAL|Numeric|  
|SQL_DOUBLE|Double|  
|SQL_FLOAT|Double|  
|SQL_INTEGER|Valore intero|  
|SQL_LONGVARBINARY|Memo (binario)|  
|SQL_LONGVARCHAR|Memo|  
|SQL_NUMERIC|Numerico *, valuta, Float|  
|SQL_REAL|Double|  
|SQL_SMALLINT|Valore intero|  
|SQL_TIME|Non supportato. Non vi è alcun Visual FoxPro *ora* tipo.|  
|SQL_TIMESTAMP|DateTime|  
|SQL_TINYINT|Valore intero|  
|SQL_VARBINARY|Memo (binario) *, generale|  
|SQL_VARCHAR|Carattere|  
  
 * Tipo predefinito  
  
 Per ulteriori informazioni sui tipi di dati Visual FoxPro, vedere [CREATE TABLE](../../odbc/microsoft/create-table-sql-command.md). Per ulteriori informazioni su questa funzione, vedere [SQLGetTypeInfo](../../odbc/reference/syntax/sqlgettypeinfo-function.md) nel *riferimento per programmatori ODBC*.
