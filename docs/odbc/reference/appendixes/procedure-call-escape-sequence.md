---
title: Sequenza di Escape di chiamata di procedura | Documenti Microsoft
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
- escape sequences [ODBC], procedure call
- procedure call escape sequence [ODBC]
- ODBC escape sequences [ODBC], procedure call
ms.assetid: 269fbab0-e5f2-4a98-86c0-2d7b647acaae
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0ba89ae47d223ea17f02cb07976510d78ff3660e
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="procedure-call-escape-sequence"></a>Sequenza di Escape di chiamata di routine
ODBC utilizza le sequenze di escape per le chiamate di procedura. La sintassi di questa sequenza di escape è come segue:  
  
 **{**[? =]**chiamare** *nome procedura*[**(**[*parametro*] [, [*parametro*]] ... **)**]**}**  
  
 Nella notazione BNF, la sintassi è:  
  
 *ODBC-procedura-escape* :: =  
  
 &#124; *ODBC-esc-iniziatore* [? =] chiamare *procedure ODBC-esc-carattere di terminazione*  
  
 *procedura* :: = *nome procedura* &#124; *nome procedura* (*elenco di parametri di procedura*)  
  
 *Identificatore di procedure* :: = *nome definito dall'utente*  
  
 *nome della routine* :: = *identificatore di procedure*  
  
 &#124; *-nome del proprietario*. *Identificatore di procedure*  
  
 &#124; *separatore di catalogo nome-catalogo* *identificatore di procedure*  
  
 &#124; *separatore di catalogo nome-catalogo* [*-nome del proprietario*]. *Identificatore di procedure*  
  
 (La terza sintassi è valida solo se l'origine dati non supporta i proprietari).  
  
 *nome del proprietario* :: = *nome definito dall'utente*  
  
 *nome del catalogo* :: = *nome definito dall'utente*  
  
 *separatore di catalogo* :: = {*definito dall'implementazione*}  
  
 (Il separatore di catalogo viene restituito tramite **SQLGetInfo** con l'opzione di informazioni SQL_CATALOG_NAME_SEPARATOR.)  
  
 *elenco di parametri di procedura* :: = *parametro di routine*  
  
 &#124; *parametro di routine*, *elenco di parametri di routine*  
  
 *parametro di routine* :: = *parametro dinamico* &#124; *letterale* &#124; *stringa vuota*  
  
 *stringa vuota* :: =  
  
 *ODBC-esc-iniziatore* :: = {  
  
 *Terminatore di esc ODBC* :: =}  
  
 (Se un parametro di routine è una stringa vuota, la procedura Usa il valore predefinito per tale parametro).  
  
 Per determinare se l'origine dati supporta le procedure e il driver supporta la sintassi di chiamata di procedura ODBC, un'applicazione può chiamare **SQLGetInfo** con il tipo di informazioni SQL_PROCEDURES.

