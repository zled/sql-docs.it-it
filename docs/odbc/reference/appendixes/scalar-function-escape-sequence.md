---
title: Sequenza di Escape funzione scalare | Documenti Microsoft
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
helpviewer_keywords:
- escape sequences [ODBC], scalar function
- scalar functions [ODBC], escape sequences
- ODBC escape sequences [ODBC], scalar function
ms.assetid: aaf5d516-e090-445f-8839-9e39581c69c7
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6792312d9b82b54460a35dd6f614c206c7bdfe3d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="scalar-function-escape-sequence"></a>Sequenza di Escape funzione scalare
ODBC utilizza le sequenze di escape per le funzioni scalari. La sintassi di questa sequenza di escape è come segue:  
  
```  
{fn scalar-function}  
```  
  
## <a name="remarks"></a>Osservazioni  
 Nella notazione BNF, la sintassi è:  
  
 *Scalare ODBC-escape funzione* :: =  
  
 *ODBC-esc-iniziatore* fn *funzione scalare ODBC esc-carattere di terminazione*  
  
 *funzione scalare* :: = *-nome della funzione* (*elenco di argomenti*)  
  
 (Le definizioni per i non terminal *-nome della funzione* e *-nome della funzione* (*elenco di argomenti*) sono derivati dall'elenco di funzioni scalari in [ Appendice e: funzioni scalari](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).)  
  
 *ODBC-esc-iniziatore* :: = {  
  
 *Terminatore di esc ODBC* :: =}  
  
 Per determinare se l'origine dati supporta le procedure e il driver supporta la sintassi di chiamata di procedura ODBC, un'applicazione può chiamare **SQLGetInfo**. Per ulteriori informazioni, vedere [appendice e: funzioni scalari](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).
