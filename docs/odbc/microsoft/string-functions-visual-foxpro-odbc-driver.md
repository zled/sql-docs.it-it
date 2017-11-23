---
title: Funzioni (Driver ODBC di Visual FoxPro) stringa | Documenti Microsoft
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
helpviewer_keywords:
- ODBC string functions [ODBC]
- string functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], string functions
- FoxPro ODBC driver [ODBC], string functions
ms.assetid: 1974fd26-ef0d-45d5-860b-298917c8e9c3
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2c62e64602162e71916624d3185426fbf73cf0bc
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="string-functions-visual-foxpro-odbc-driver"></a>Funzioni stringa (Visual FoxPro ODBC Driver)
La tabella seguente elenca le funzioni di modifica stringa ODBC supportate dal Driver ODBC di Visual FoxPro; Quando la grammatica di Visual FoxPro per la stessa funzione differisce dalla sintassi ODBC, viene elencata l'equivalente di Visual FoxPro.  
  
|Grammatica ODBC|Grammatica di Visual FoxPro|  
|------------------|---------------------------|  
|ASCII *(string_exp)*|ASC *(string_exp)*|  
|CHAR *(codice)*|CHR *(string_exp)*|  
|CONCAT *(string_exp1, string_exp2 e)*|*string_exp1 + string_exp2 e*|  
|DIFFERENZA *(string_exp1, string_exp2 e)*||  
|Inserisci *(string_exp1, start, lunghezza, string_exp2 e)*|STUFF *(string_exp1, start, lunghezza, string_exp2 e)*|  
|LCASE *(string_exp)*|INFERIORE *(string_exp)*|  
|SINISTRA *(string_exp, conteggio)*||  
|LUNGHEZZA *(string_exp)*|LEN *(string_exp)*|  
|LTRIM *(string_exp)*||  
|Ripetere *(string_exp, conteggio)*|REPLICARE *(string_exp, conteggio)*|  
|Sostituire *(string_exp1, string_exp2 e, string_exp3)*|STRTRAN *(string_exp1, string_exp2 e, string_exp3)*|  
|DESTRA *(string_exp, conteggio)*||  
|RTRIM *(string_exp)*||  
|SOUNDEX *(string_exp)*||  
|SPAZIO *(conteggio)*||  
|SOTTOSTRINGA *(string_exp, start, lunghezza)*|SUBSTR *(string_exp, start, lunghezza)*|  
|Funzione UCASE *(string_exp)*|SUPERIORE *(string_exp)*|
