---
title: Funzioni (Driver ODBC di Visual FoxPro) stringa | Documenti Microsoft
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
- ODBC string functions [ODBC]
- string functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], string functions
- FoxPro ODBC driver [ODBC], string functions
ms.assetid: 1974fd26-ef0d-45d5-860b-298917c8e9c3
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a5f201eee732fa316873919deaabc4d07610a015
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="string-functions-visual-foxpro-odbc-driver"></a>Funzioni stringa (Visual FoxPro ODBC Driver)
La tabella seguente elenca le funzioni di modifica stringa ODBC supportate dal Driver ODBC di Visual FoxPro; Quando la grammatica di Visual FoxPro per la stessa funzione differisce dalla sintassi ODBC, viene elencata l'equivalente di Visual FoxPro.  
  
|Grammatica ODBC|Grammatica di Visual FoxPro|  
|------------------|---------------------------|  
|ASCII *(string_exp)*|ASC *(string_exp)*|  
|CHAR *(codice)*|CHR *(string_exp)*|  
|CONCAT *(string_exp1, string_exp2 e)*|*string_exp1 + string_exp2 e*|  
|DIFFERENZA *(string_exp1, string_exp2 e)*||  
|INSERIRE *(string_exp1, start, lunghezza, string_exp2 e)*|STUFF *(string_exp1, start, lunghezza, string_exp2 e)*|  
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
|UCASE *(string_exp)*|SUPERIORE *(string_exp)*|
