---
title: Sequenza di Escape delle funzioni scalari | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], scalar function
- scalar functions [ODBC], escape sequences
- ODBC escape sequences [ODBC], scalar function
ms.assetid: aaf5d516-e090-445f-8839-9e39581c69c7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0913458d683d7641145b262552e147033dbfc054
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47660789"
---
# <a name="scalar-function-escape-sequence"></a>Sequenza di escape per funzioni scalari
ODBC Usa sequenze di escape per le funzioni scalari. La sintassi di questa sequenza di escape è come segue:  
  
```  
{fn scalar-function}  
```  
  
## <a name="remarks"></a>Note  
 Nella notazione BNF, la sintassi è come segue:  
  
 *Valore scalare ODBC-funzione-escape* :: =  
  
 *ODBC-esc-iniziatore* fn *funzione scalare ODBC esc-carattere di terminazione*  
  
 *funzione scalare* :: = *-nome della funzione* (*elenco di argomenti*)  
  
 (Le definizioni per i non terminal *-nome della funzione* e *-nome della funzione* (*dall'elenco di argomenti*) sono derivati dall'elenco di funzioni scalari in [ Appendice e: funzioni scalari](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).)  
  
 *ODBC-esc-iniziatore* :: = {  
  
 *ODBC-esc-carattere di terminazione* :: =}  
  
 Per determinare se l'origine dati supporta le procedure e il driver supporta la sintassi di chiamata di procedura ODBC, un'applicazione può chiamare **SQLGetInfo**. Per altre informazioni, vedere [appendice e: funzioni scalari](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).
