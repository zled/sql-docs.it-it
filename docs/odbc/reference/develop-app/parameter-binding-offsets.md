---
title: Offset di associazione di parametro | Documenti Microsoft
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
- offsets of parameters [ODBC]
- binding offsets of parameters [ODBC]
ms.assetid: 309339e9-9ccd-4a58-8aa4-b6dc88f4eb7c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5b3fea1397710c5a65a03b3f829972f04cc63f5a
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="parameter-binding-offsets"></a>Offset di associazione di parametri
Un'applicazione può specificare che un offset viene aggiunto per associare gli indirizzi di buffer di parametro e l'indicatore di lunghezza corrispondente buffer indirizzi quando **SQLExecDirect** o **SQLExecute** viene chiamato. Il risultato di queste aggiunte determina gli indirizzi usati in queste operazioni.  
  
 Offset di associazione consentono a un'applicazione modificare le associazioni senza chiamare **SQLBindParameter** per i parametri associati in precedenza. Una chiamata a **SQLBindParameter** per riassociare un parametro viene modificato l'indirizzo del buffer e il puntatore di lunghezza/indicatore. Riassociazione con un offset, d'altra parte, semplicemente aggiunge un offset all'indirizzo del buffer di parametri associati esistente e indirizzo del buffer di lunghezza/indicatore. Quando vengono utilizzati gli offset, le associazioni sono "modello" di disposizione i buffer dell'applicazione e l'applicazione può passare "modello" a diverse aree di memoria modificando l'offset. Un nuovo offset può essere specificato in qualsiasi momento e viene sempre aggiunta per i valori associati originariamente.  
  
 Per specificare un offset di associazione, l'applicazione imposta l'attributo di istruzione SQL_ATTR_PARAM_BIND_OFFSET_PTR all'indirizzo di un buffer SQLINTEGER. Prima che l'applicazione chiama una funzione che utilizza le associazioni, viene inserito un offset in byte di questo buffer, fino a quando l'indirizzo del buffer parametro né l'indirizzo del buffer di lunghezza/indicatore è 0 e il parametro associato è presente l'istruzione SQL. La somma dell'indirizzo e l'offset deve essere un indirizzo valido. (Ciò significa che uno o entrambi l'offset e l'indirizzo a cui viene aggiunta l'offset può essere validi, come la somma è un indirizzo valido).  
  
> [!NOTE]  
>  Offset di associazione non sono supportate da ODBC 2. *x* driver.
