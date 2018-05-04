---
title: Sequenza di Escape funzione scalare | Documenti Microsoft
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
- escape sequences [ODBC], scalar function
- scalar functions [ODBC], escape sequences
- ODBC escape sequences [ODBC], scalar function
ms.assetid: aaf5d516-e090-445f-8839-9e39581c69c7
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8ca98389b0279ded2aba487e2e3e0f6bbbe95e6b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="scalar-function-escape-sequence"></a>Sequenza di Escape funzione scalare
ODBC utilizza le sequenze di escape per le funzioni scalari. La sintassi di questa sequenza di escape è come segue:  
  
```  
{fn scalar-function}  
```  
  
## <a name="remarks"></a>Osservazioni  
 Nella notazione BNF, la sintassi è:  
  
 *ODBC scalar-funzione-caratteri di escape* :: =  
  
 *ODBC-esc-iniziatore* fn *funzione scalare ODBC esc-carattere di terminazione*  
  
 *funzione scalare* :: = *-nome della funzione* (*elenco di argomenti*)  
  
 (Le definizioni per i non terminal *-nome della funzione* e *-nome della funzione* (*elenco di argomenti*) sono derivati dall'elenco di funzioni scalari in [ Appendice e: funzioni scalari](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).)  
  
 *ODBC-esc-iniziatore* :: = {  
  
 *ODBC-esc-carattere di terminazione* :: =}  
  
 Per determinare se l'origine dati supporta le procedure e il driver supporta la sintassi di chiamata di procedura ODBC, un'applicazione può chiamare **SQLGetInfo**. Per ulteriori informazioni, vedere [appendice e: funzioni scalari](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).
