---
title: Tipi di dati Microsoft Access | Documenti Microsoft
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
- ODBC desktop database drivers [ODBC], Access driver
- Jet-based ODBC drivers [ODBC], Access driver
- desktop database drivers [ODBC], Access driver
- Access driver [ODBC], data types
- access data types [ODBC]
- data types [ODBC], Access driver
ms.assetid: b537348a-bea0-4bd6-84a4-52a75292957f
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d158cd0646f276d278b66427e3f44b661493e695
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="microsoft-access-data-types"></a>Tipi di dati Microsoft Access
La tabella seguente illustra i tipi di dati Microsoft Access, tipi di dati utilizzati per creare tabelle e tipi di dati SQL ODBC.  
  
|Tipo di dati Microsoft Access|Tipo di dati (CREATETABLE)|Tipo di dati SQL ODBC|  
|--------------------------------|-------------------------------|------------------------|  
|BIGBINARY [1]|LONGBINARY|SQL_LONGVARBINARY|  
|BINARY|BINARY|SQL_BINARY|  
|BIT|BIT|SQL_BIT|  
|CONTATORE|CONTATORE|SQL_INTEGER|  
|CURRENCY|CURRENCY|SQL_NUMERIC|  
|DATA E ORA|DATETIME|SQL_TIMESTAMP|  
|GUID|GUID|SQL_GUID|  
|BINARIO LUNGO|LONGBINARY|SQL_LONGVARBINARY|  
|TESTO LUNGO|LONGTEXT|SQL_WLONGVARCHAR SQL_LONGVARCHAR [2] [3]|  
|MEMO|LONGTEXT|SQL_WLONGVARCHAR SQL_LONGVARCHAR [2] [3]|  
|NUMERO (Dimensione campo = celibe/NUBILE)|SINGOLO|SQL_REAL|  
|NUMERO (Dimensione campo = doppia)|DOUBLE|SQL_DOUBLE|  
|NUMERO (Dimensione campo = BYTE)|BYTE SENZA SEGNO|SQL_TINYINT|  
|NUMERO (Dimensione campo = valore INTEGER)|BREVE|SQL_SMALLINT|  
|NUMERO (Dimensione campo = valore LONG INTEGER)|LONG|SQL_INTEGER|  
|NUMERIC|NUMERIC|SQL_NUMERIC|  
|OLE|LONGBINARY|SQL_LONGVARBINARY|  
|TEXT|VARCHAR|SQL_WVARCHAR SQL_VARCHAR [1] [2]|  
ARBINARY|VARBINARY|SQL_VARBINARY|  
  
 [1] di accedere solo alle 4.0 applicazioni. Lunghezza massima di 4000 byte. Comportamento simile a LONGBINARY.  
  
 [2] solo le applicazioni ANSI.  
  
 [3] Unicode e 4.0 di accesso solo applicazioni.  
  
> [!NOTE]  
>  **SQLGetTypeInfo** restituisce i tipi di dati ODBC. Tutti i tipi di dati di Microsoft Access non verrà restituito se viene eseguito il mapping di più di un tipo di Microsoft Access nello stesso tipo di dati SQL ODBC. Tutte le conversioni nell'appendice D il *riferimento per programmatori ODBC* sono supportati per i tipi di dati SQL elencati nella tabella precedente.  
  
 La tabella seguente illustra le limitazioni sui tipi di dati Microsoft Access.  
  
|Tipo di dati|Description|  
|---------------|-----------------|  
|BINARY, VARBINARY e VARCHAR|Creazione di una colonna BINARY, VARBINARY o VARCHAR pari a zero o lunghezza non specificata restituisce una colonna di 510 byte.|  
|BYTE|Anche se un campo del numero di accesso di Microsoft con una dimensione pari a BYTE senza segno, un numero negativo può essere inserito nel campo quando si utilizza il driver Microsoft Access.|  
|VARCHAR, LONGVARCHAR e CHAR|Un valore letterale di stringa di caratteri può contenere qualsiasi carattere ANSI (decimale 1-255). Utilizzare due virgolette singole consecutive (") per rappresentare una virgoletta singola (').<br /><br /> Procedure devono essere utilizzate per passare i dati di tipo carattere quando si utilizzano caratteri speciali in una colonna di tipo carattere.|  
|DATE|I valori di data devono essere delimitati in base al formato di data canonica ODBC o delimitati dal delimitatore di datetime ("#"). In caso contrario, Microsoft Access tratterà il valore come un'espressione aritmetica e non genererà un avviso o errore.<br /><br /> Ad esempio, la data "5 marzo 1996" deve essere rappresentato come {d ' 1996-03-05'} o # #03/05/1996; in caso contrario, se solo invio 05/03/1993, Microsoft Access valuterà questo come 3 diviso 5 diviso 1996. Questo valore arrotondamento per eccesso all'intero 0 e dal momento che il giorno zero associato a 1899-12-31, si tratta della data utilizzata.<br /><br /> Un carattere barra verticale (&#124;) non è utilizzato in un valore di data, anche se i backup racchiusi tra virgolette.|  
|GUID|Tipo di dati limitato alla versione 4.0 di Microsoft Access.|  
|NUMERIC|Tipo di dati limitato alla versione 4.0 di Microsoft Access.|  
  
 Altre limitazioni sui tipi di dati sono reperibili [limitazioni del tipo di dati](../../odbc/microsoft/data-type-limitations.md).

