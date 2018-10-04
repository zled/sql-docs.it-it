---
title: SQLGetInfo (Driver File di testo) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetInfo function [ODBC], Text File Driver
- text file driver [ODBC], SQLGetInfo
ms.assetid: 6b7a630e-47f8-4ee1-b2a7-476bc1d0b0d4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 37d8d67300ec29a2b346f5f6b958c1955d08db0a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47792169"
---
# <a name="sqlgetinfo-text-file-driver"></a>SQLGetInfo (driver file di testo)
> [!NOTE]  
>  In questo argomento fornisce informazioni specifiche del Driver File di testo. Per informazioni generali su questa funzione, vedere l'argomento appropriato nel [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLGetInfo** supporta il tipo di informazioni SQL_FILE_USAGE. Il valore restituito è un numero intero a 16 bit che indica il modo in cui il driver considera direttamente i file in un'origine dati:  
  
-   SQL_FILE_NOT_SUPPORTED, Il driver non è un driver a un solo livello.  
  
-   SQL_FILE_TABLE, ovvero Un driver a un solo livello di gestione dei file in un'origine dati come tabelle.  
  
-   SQL_FILE_QUALIFIER, ovvero Un driver a un solo livello considera i file in un'origine dati come un qualificatore.  
  
 Il driver ODBC restituisce SQL_FILE_TABLE per Textdriver, poiché ogni file è una tabella.  
  
## <a name="sqldbmsver"></a>SQL_DBMS_VER  
  
|ISAM|Versione|Formato dei numeri di versione|  
|----------|-------------|-------------------------------|  
|Testo|1,0|01.00.0000|  
  
## <a name="sqlcatalogusage"></a>SQL_CATALOG_USAGE  
 SQL_QU_DML_STATEMENTS &AMP;#124; SQL_QU_TABLE_DEFINITION  
  
## <a name="sqltimedatefunctions"></a>SQL_TIMEDATE_FUNCTIONS  
 SQL_FN_TD_CURDATE &AMP;#124; SQL_FN_TD_CURTIME &AMP;#124; SQL_FN_TD_DAYOFMONTH &AMP;#124; SQL_FN_TD_DAYOFWEEK &AMP;#124; SQL_FN_TD_DAYOFYEAR &AMP;#124; SQL_FN_TD_HOUR &AMP;#124; SQL_FN_TD_MINUTE &AMP;#124; SQL_FN_TD_MONTH &AMP;#124; SQL_FN_TD_NOW &AMP;#124; SQL_FN_TD_SECOND &AMP;#124; SQL_FN_TD_WEEK &AMP;#124; SQL_FN_TD_YEAR
