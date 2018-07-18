---
title: I vincoli del calendario gregoriano | Documenti Microsoft
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
- data types [ODBC], Gregorian calendar
- Gregorian calendar [ODBC]
ms.assetid: 70667410-c582-4369-8e06-9d98e21cd2bf
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1cea1f4b4dd5b56feee64623bd6ff2355ce4332c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32905436"
---
# <a name="constraints-of-the-gregorian-calendar"></a>Vincoli del calendario gregoriano
Tipi di dati date e datetime e i campi dei tipi di dati di intervallo finali devono essere conforme ai vincoli del calendario gregoriano. Questi vincoli sono i seguenti:  
  
-   Il valore del campo mese deve essere compreso tra 1 e 12 inclusi.  
  
-   Il valore del campo giorno deve essere compreso nell'intervallo compreso tra 1 e il numero di giorni del mese. Il numero di giorni del mese è determinato dai valori dei campi anni e mesi e può essere 28, 29, 30 o 31. (Il numero di giorni del mese può inoltre dipendere si tratti di un anno bisestile.)  
  
-   Il valore del campo ora deve essere compreso tra 0 e 23, inclusi.  
  
-   Il valore del campo relativo ai minuti deve essere compreso tra 0 e 59.  
  
-   Per il campo secondi finali dei tipi di dati di intervallo, il valore del campo secondi deve essere compreso tra 0 e 59,9 (*n*), inclusi, dove *n* è il numero di cifre di precisione frazionaria dei secondi.  
  
-   Per il campo secondi finali dei tipi di dati Data/ora, il valore del campo secondi deve essere compreso tra 0 e 61.9 (*n*), inclusi, dove *n* specifica il numero di cifre "9" e il valore di *n*  è la precisione dei secondi frazionari. (L'intervallo di secondi consente un massimo di due secondi di compensazione gestire la sincronizzazione dell'ora siderale).
