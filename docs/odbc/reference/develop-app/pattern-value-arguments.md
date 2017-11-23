---
title: Argomenti di valore di schema | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- catalog functions [ODBC], arguments
- arguments in catalog functions [ODBC], pattern value
- pattern value arguments [ODBC]
ms.assetid: 1d3f0ea6-87af-4836-807f-955e7df2b5df
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 28caa361e4363aa2224d6cfa63a8830675aeece8
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="pattern-value-arguments"></a>Argomenti di valore modello
Alcuni argomenti nel catalogo di funzioni, ad esempio il *TableName* argomento **SQLTables**, accettare i criteri di ricerca. Questi argomenti accettano i criteri di ricerca se l'attributo di istruzione SQL_ATTR_METADATA_ID è impostato su SQL_FALSE; sono gli argomenti di identificatore che non accettano un criterio di ricerca se questo attributo è impostato su SQL_TRUE.  
  
 I caratteri di criterio di ricerca sono:  
  
-   Un carattere di sottolineatura (_), che rappresenta qualsiasi carattere singolo.  
  
-   Un segno di percentuale (%), che rappresenta qualsiasi sequenza di zero o più caratteri.  
  
-   Un carattere di escape, che è specifico del driver e viene utilizzato per includere i caratteri di sottolineatura, segni di percentuale, e il carattere di escape come valori letterali. Se il carattere di escape precede un carattere non speciali, il carattere di escape non hanno alcun significato speciale. Se il carattere di escape precede un carattere speciale, viene eseguito l'escape del carattere speciale. Ad esempio, "\a" verrebbe considerato come due caratteri, "\\" e "a", ma "\\%" verrebbe considerato come il carattere singolo non speciali "%".  
  
 Il carattere di escape verrà recuperato con l'opzione SQL_SEARCH_PATTERN_ESCAPE in **SQLGetInfo**. In un argomento che accetta i criteri di ricerca per includere tale carattere come valore letterale deve precedere qualsiasi carattere di sottolineatura, un segno di percentuale o un carattere di escape. Nella tabella seguente sono illustrati esempi.  
  
|Criterio di ricerca|Description|  
|--------------------|-----------------|  
|% %A|Tutti gli identificatori che contiene la lettera A|  
|ABC|Tutti gli identificatori di quattro caratteri a partire da ABC|  
|ABC\\_|L'identificatore ABC, presupponendo che il carattere di escape è una barra rovesciata (\\)|  
|\\\\%|Tutti gli identificatori a partire da una barra rovesciata (\\), presupponendo che il carattere di escape è una barra rovesciata|  
  
 Particolare attenzione per eseguire l'escape di caratteri del modello di ricerca negli argomenti che accettano i criteri di ricerca. Ciò è particolarmente vero per il carattere di sottolineatura, in genere utilizzato negli identificatori. Un errore comune nelle applicazioni consiste nel recuperare un valore di una funzione di catalogo e passare il valore a un argomento di modello di ricerca in un'altra funzione di catalogo. Ad esempio, si supponga che un'applicazione recupera il nome della tabella MY_TABLE dal risultato impostato per **SQLTables** e passa la **SQLColumns** per recuperare un elenco di colonne in MY_TABLE. Anziché le colonne per MY_TABLE, l'applicazione riceverà le colonne per tutte le tabelle che corrispondono al criterio di ricerca MY_TABLE, ad esempio MY_TABLE, MY1TABLE, MY2TABLE e così via.  
  
> [!NOTE]  
>  ODBC 2. *x* driver non supporta i criteri di ricerca nel *CatalogName* argomento **SQLTables**. ODBC 3*x* driver accettano i modelli di ricerca in questo argomento se l'attributo di ambiente sql_attr ODBC_VERSION è impostato su SQL_OV_ODBC3; non accetta i criteri di ricerca in questo argomento se è impostato su SQL_OV_ODBC2.  
  
 Passando un puntatore null a un argomento di modello di ricerca non vincola la ricerca per tale argomento. ovvero, un puntatore null e la percentuale di criterio di ricerca (caratteri) sono equivalenti. Tuttavia, di lunghezza zero ricerca modello, ovvero, ovvero un puntatore valido a una stringa di lunghezza zero, ovvero corrisponde solo una stringa vuota ("").
