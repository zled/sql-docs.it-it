---
title: Cifre decimali | Documenti Microsoft
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
- size of data types [ODBC]
- decimal digits of data types [ODBC]
- data types [ODBC], decimal digits
- SQL data types [ODBC], column characteristics
ms.assetid: 07f3d1fc-b4ee-4693-b342-330b2231b6d0
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1bb5222837dab705701e4a137c00f3b10867ae2a
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="decimal-digits"></a>Cifre decimali
Il *cifre decimali* di dati decimal e numeric tipi viene definito come il numero massimo di cifre a destra del separatore decimale, o la scala dei dati. Per le colonne di numeri a virgola mobile approssimati o i parametri, la scala è definita, poiché il numero di cifre a destra del separatore decimale non è fisso. Per datetime o intervallo di dati che contiene un componente di secondi, le cifre decimali viene definito come il numero di cifre a destra del separatore decimale nel componente di secondi di dati.  
  
 Per i tipi di dati SQL_DECIMAL e SQL_NUMERIC, la scala massima corrisponde in genere la precisione massima. Tuttavia, alcune origini dati impongono un limite separato per la scala massima. Per determinare le scale minime e massime consentite per un tipo di dati, un'applicazione chiama **SQLGetTypeInfo**.  
  
 Le cifre decimali definite per ogni tipo di dati SQL conciso è illustrato nella tabella seguente.  
  
|Tipo SQL|cifre decimali|  
|--------------|--------------------|  
|Tutti i tipi carattere e binario [a]|n/d|  
|SQL_DECIMAL<br />SQL_NUMERIC|Il numero definito di cifre a destra del separatore decimale. Ad esempio, la scala di una colonna definita come NUMERIC(10,3) è 3. Può trattarsi di un numero negativo per il supporto di archiviazione di numeri molto grandi senza utilizzare la notazione esponenziale. ad esempio, "12000" possono essere archiviate come "12" con una scala pari a -3.|  
|Tutti i tipi numerici esatti diversi da SQL_DECIMAL e SQL_NUMERIC [a]|0|  
|Tutti i tipi di dati approssimati [a]|n/d|  
|Tipo SQL_TYPE_DATE e tutti i tipi di intervallo con nessun componente di secondi [a]|n/d|  
|Tutti i tipi datetime ad eccezione di tipo SQL_TYPE_DATE e tutti i tipi di intervallo con un componente di secondi|Il numero di cifre a destra del separatore decimale nella parte relativa ai secondi del valore (secondi frazionari). Questo numero può essere negativo.|  
|SQL_GUID|n/d|  
  
 [a] il *DecimalDigits* argomento di **SQLBindParameter** viene ignorata per questo tipo di dati.  
  
 I valori restituiti per le cifre decimali non corrispondono ai valori nel campo del descrittore. I valori possono provenire dal SQL_DESC_SCALE o il campo SQL_DESC_PRECISION, a seconda del tipo di dati, come illustrato nella tabella seguente.  
  
|Tipo SQL|Campo di descrizione corrispondente<br /><br /> cifre decimali|  
|--------------|----------------------------------------------------------|  
|Tutti i tipi carattere e binario|n/d|  
|Tutti i tipi numerici esatti|SCALE|  
|SQL_BIT|n/d|  
|Tutti i tipi numerici approssimati|n/d|  
|Tutti i tipi di data/ora|PRECISION|  
|Tutti i tipi di intervallo con un componente di secondi|PRECISION|  
|Tutti i tipi di intervallo con nessun componente di secondi|n/d|
