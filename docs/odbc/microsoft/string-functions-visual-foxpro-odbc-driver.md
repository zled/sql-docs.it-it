---
title: Funzioni (Driver ODBC Visual FoxPro) stringa | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC string functions [ODBC]
- string functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], string functions
- FoxPro ODBC driver [ODBC], string functions
ms.assetid: 1974fd26-ef0d-45d5-860b-298917c8e9c3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1a9e1c94eec150cc24522cd6e4c57eb35b4a2126
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47854829"
---
# <a name="string-functions-visual-foxpro-odbc-driver"></a>Funzioni per i valori stringa (driver ODBC Visual FoxPro)
La tabella seguente elenca le funzioni di modifica stringa ODBC supportate per il Driver ODBC Visual FoxPro; Quando la grammatica di Visual FoxPro per la stessa funzione differisce dalla sintassi ODBC, viene elencato l'equivalente di Visual FoxPro.  
  
|Grammatica ODBC|Grammatica di Visual FoxPro|  
|------------------|---------------------------|  
|ASCII *(string_exp)*|Centro sicurezza di AZURE *(string_exp)*|  
|CHAR *(codice)*|Tra due CHR *(string_exp)*|  
|CONCAT *(string_exp1, string_exp2 e)*|*string_exp1 + string_exp2 e*|  
|DIFFERENZA *(string_exp1, string_exp2 e)*||  
|Inserisci *(string_exp1, start, length, string_exp2 e)*|STUFF *(string_exp1, start, length, string_exp2 e)*|  
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
|SOTTOSTRINGA *(string_exp, start, length)*|SUBSTR *(string_exp, start, length)*|  
|UCASE *(string_exp)*|ALTO *(string_exp)*|
