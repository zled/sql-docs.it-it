---
title: Sequenza di Escape di chiamata di routine | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], procedure call
- procedure call escape sequence [ODBC]
- ODBC escape sequences [ODBC], procedure call
ms.assetid: 269fbab0-e5f2-4a98-86c0-2d7b647acaae
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 914bd4759552680a57c345dc3a7c3bc1bcc103a6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47806559"
---
# <a name="procedure-call-escape-sequence"></a>Sequenza di escape per chiamata di procedura
ODBC Usa sequenze di escape per le chiamate di procedura. La sintassi di questa sequenza di escape è come segue:  
  
 **{**[? =]**chiamare** *-nome della routine*[**(**[*parametro*] [, [*parametro*]]... **)**]**}**  
  
 Nella notazione BNF, la sintassi è come segue:  
  
 *ODBC-procedure-escape* :: =  
  
 &#124;*ODBC-esc-iniziatore* [? =] chiamare *procedure ODBC-esc-carattere di terminazione*  
  
 *routine* :: = *-nome della routine* &#124; *procedure-name* (*procedure-parameter-list*)  
  
 *procedure-identifier* :: = *nome definito dall'utente*  
  
 *nome della routine* :: = *procedure-identifier*  
  
 &#124;*-nome del proprietario*. *Identificatore di procedure*  
  
 &#124;*separatore di catalogo-nome del catalogo* *procedure-identifier*  
  
 &#124;*separatore di catalogo-nome del catalogo* [*-nome del proprietario*]. *Identificatore di procedure*  
  
 (La terza sintassi è valida solo se l'origine dati non supporta i proprietari).  
  
 *nome del proprietario* :: = *nome definito dall'utente*  
  
 *Nome-catalogo* :: = *nome definito dall'utente*  
  
 *separatore di catalogo* :: = {*definito dall'implementazione*}  
  
 (Il separatore di catalogo viene restituito tramite **SQLGetInfo** con l'opzione di informazioni SQL_CATALOG_NAME_SEPARATOR.)  
  
 *elenco di parametri di routine* :: = *procedure-parametro*  
  
 &#124;*parametro di routine*, *procedure-parameter-list*  
  
 *parametro di routine* :: = *il parametro dinamico* &#124; *letterale* &#124; *stringa vuota*  
  
 *stringa vuota* :: =  
  
 *ODBC-esc-iniziatore* :: = {  
  
 *ODBC-esc-carattere di terminazione* :: =}  
  
 (Se un parametro di routine è una stringa vuota, la procedura Usa il valore predefinito per tale parametro.)  
  
 Per determinare se l'origine dati supporta le procedure e il driver supporta la sintassi di chiamata di procedura ODBC, un'applicazione può chiamare **SQLGetInfo** con il tipo di informazioni SQL_PROCEDURES.
