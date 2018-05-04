---
title: Il recupero dei risultati (avanzati) | Documenti Microsoft
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
- offsets [ODBC]
- result sets [ODBC], about result sets
- bind offsets [ODBC]
ms.assetid: bc00c379-71a7-407a-975c-898243f39bb6
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b8f8683d8ec1b467b17e5434803c5deb1ee3a554
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="retrieving-results-advanced"></a>Il recupero dei risultati (avanzati)
Un'applicazione può specificare che un offset viene aggiunto per associare gli indirizzi di buffer di dati e l'indicatore di lunghezza corrispondente buffer indirizzi quando **SQLBulkOperations**, **SQLFetch**,  **SQLFetchScroll**, o **SQLSetPos** viene chiamato. I risultati di queste aggiunte determinano gli indirizzi usati in queste operazioni.  
  
 Offset di associazione consentono a un'applicazione modificare le associazioni senza chiamare **SQLBindCol** per le colonne associate in precedenza. Una chiamata a **SQLBindCol** per riassociare i dati viene modificato l'indirizzo del buffer e il puntatore di lunghezza/indicatore. Riassociazione con un offset, d'altra parte, semplicemente aggiunge un offset all'indirizzo del buffer di dati associati esistente e indirizzo del buffer di lunghezza/indicatore. Quando vengono utilizzati gli offset, le associazioni sono "modello" di disposizione i buffer dell'applicazione e l'applicazione può passare "modello" a diverse aree di memoria modificando l'offset. Un nuovo offset può essere specificato in qualsiasi momento e viene sempre aggiunta per i valori associati originariamente.  
  
 Per specificare un offset di associazione, l'applicazione imposta l'attributo di istruzione SQL_ATTR_ROW_BIND_OFFSET_PTR all'indirizzo di un buffer SQLINTEGER. Prima che l'applicazione chiama una funzione che utilizza le associazioni, ad esempio **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**, o **SQLSetPos**, viene inserito un offset in byte di questo buffer, fino a quando l'indirizzo del buffer dei dati né l'indirizzo del buffer di lunghezza/indicatore è 0 e fino a quando la colonna associata viene nel set di risultati. La somma dell'indirizzo e l'offset deve essere un indirizzo valido. (Ciò significa che uno o entrambi l'offset e l'indirizzo a cui viene aggiunta l'offset può essere validi, come la somma è un indirizzo valido). L'attributo di istruzione SQL_ATTR_ROW_BIND_OFFSET_PTR è un puntatore in modo che il valore di offset può essere applicato a più di un set di associazione di dati, ognuno dei quali può essere modificato da un valore di offset di modifica. Un'applicazione deve garantire che il puntatore rimane valido fino a quando il cursore è chiuso.  
  
> [!NOTE]  
>  Offset di associazione non sono supportate da ODBC 2. *x* driver.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Cursori rettangolari](../../../odbc/reference/develop-app/block-cursors.md)  
  
-   [Cursori scorrevoli](../../../odbc/reference/develop-app/scrollable-cursors.md)  
  
-   [Libreria di cursori ODBC](../../../odbc/reference/develop-app/the-odbc-cursor-library.md)  
  
-   [Risultati multipli](../../../odbc/reference/develop-app/multiple-results.md)
