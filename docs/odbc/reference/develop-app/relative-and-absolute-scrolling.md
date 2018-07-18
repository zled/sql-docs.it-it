---
title: Lo scorrimento relative e assolute | Documenti Microsoft
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
- absolute scrolling [ODBC]
- relative scrolling [ODBC]
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
ms.assetid: 3d0ff48d-fef5-4c01-bb1d-a583e6269b66
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 93f92b1cd5369ade8102b2505ef37f1da29dde4f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="relative-and-absolute-scrolling"></a>Relative e assolute lo scorrimento
La maggior parte delle opzioni di scorrimento in **SQLFetchScroll** posizionare il cursore rispetto alla posizione corrente o a una posizione assoluta. **SQLFetchScroll** supporta il recupero successivo, precedente, primo e ultimo set di righe, come anche come relativo recupero di massa (recuperare il set di righe *n* righe dall'inizio del set di righe corrente) e il recupero assoluto (recupero di inizio del set di righe alla riga *n*). Se *n* è negativo in un recupero assoluto, le righe vengono conteggiate dalla fine del set di risultati. Di conseguenza, un recupero assoluto della riga -1 indica il recupero di set di righe che inizia con l'ultima riga nel set di risultati.  
  
 I cursori dinamici rilevano righe inserito ed eliminate dal set di risultati, pertanto non sarà più semplice per i cursori dinamici recuperare la riga in corrispondenza di un numero specifico diverso da lettura dall'inizio del set di risultati, è probabile che sia lento. Inoltre, recupero assoluto non è molto utile per i cursori dinamici perché i numeri di riga è stata modificata le righe vengono inserite e soppresso. Pertanto, recupero successivamente lo stesso numero di riga consentono di ottenere righe diverse.  
  
 Le applicazioni che utilizzano **SQLFetchScroll** solo per il relativo blocco di funzionalità del cursore, ad esempio report, è probabile che passano attraverso il set di risultati una sola volta, utilizzando solo l'opzione per recuperare il successivo set di righe. Applicazioni basate su schermo, d'altra parte, possono sfruttare tutte le funzionalità di **SQLFetchScroll**. Se l'applicazione imposta le dimensioni del set di righe per il numero di righe visualizzate sullo schermo e associa i buffer dello schermo al set di risultati, può convertire operazioni della barra di scorrimento direttamente in chiamate a **SQLFetchScroll**.  
  
|Operazione della barra di scorrimento|Opzione di scorrimento SQLFetchScroll|  
|--------------------------|-------------------------------------|  
|Su di una pagina|SQL_FETCH_PRIOR|  
|Giù di una pagina|SQL_FETCH_NEXT|  
|Su di una riga|SQL_FETCH_RELATIVE con *FetchOffset* uguale a -1|  
|Giù di una riga|SQL_FETCH_RELATIVE con *FetchOffset* uguale a 1|  
|Casella di scorrimento in alto|SQL_FETCH_FIRST|  
|Casella di scorrimento nella parte inferiore|SQL_FETCH_LAST|  
|Posizione casuale della casella di scorrimento|SQL_FETCH_ABSOLUTE|  
  
 Tali applicazioni è necessario anche posizionare la casella di scorrimento dopo un'operazione di scorrimento, che richiede il numero di riga corrente e il numero di righe. Per il numero di riga corrente, le applicazioni di tenere traccia del numero di riga corrente o chiamare **SQLGetStmtAttr** con l'attributo SQL_ATTR_ROW_NUMBER per recuperarlo.  
  
 Il numero di righe del cursore, ovvero le dimensioni del risultato è impostato, è disponibile come il campo SQL_DIAG_CURSOR_ROW_COUNT dell'intestazione di diagnostica. Il valore in questo campo è definito solo dopo che **SQLExecute**, **SQLExecDirect**, o **SQLMoreResult** è stato chiamato. Questo conteggio può essere un numero approssimativo di o un conteggio esatto, a seconda delle funzionalità del driver. Supporto del driver può essere determinato chiamando **SQLGetInfo** con i tipi di informazioni di attributi del cursore e verifica se il bit SQL_CA2_CRC_APPROXIMATE o SQL_CA2_CRC_EXACT viene restituito il tipo di cursore.  
  
 Un numero di riga esatta non è mai supportato per un cursore dinamico. Per altri tipi di cursori, il driver può supportare il conteggio delle righe esatta o approssimativa, ma non entrambi. Se il driver supporta esatta né approssimativo conteggio delle righe per un tipo di cursore specifico, il campo SQL_DIAG_CURSOR_ROW_COUNT contiene il numero di righe che sono stati recuperati finora. Indipendentemente dal quale il driver supporta, **SQLFetchScroll** con un *operazione* di SQL_FETCH_LAST causerà il campo SQL_DIAG_CURSOR_ROW_COUNT contenere il numero di riga esatta.
