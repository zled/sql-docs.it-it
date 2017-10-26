---
title: Tipi di dati di File di testo | Documenti Microsoft
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
- text file driver [ODBC], data types
- ODBC desktop database drivers [ODBC], text file driver
- desktop database drivers [ODBC], text file driver
- text file data types [ODBC]
- Jet-based ODBC drivers [ODBC], text file driver
ms.assetid: e113112e-ae42-469e-8e4b-a365a10d9071
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: cd72cc24ff011559addeabd0bcc95b172db1a60f
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="text-file-data-types"></a>Tipi di dati di File di testo
Nella tabella seguente viene illustrato come tipi di dati di testo vengono eseguito il mapping ai tipi di dati SQL ODBC. Si noti che non tutti i tipi di dati SQL ODBC sono supportati dal driver ODBC testo.  
  
|Tipo di dati di testo|Tipo di dati ODBC|  
|--------------------|--------------------|  
|CHAR|SQL_VARCHAR|  
|DATETIME|SQL_TIMESTAMP|  
|FLOAT|SQL_DOUBLE|  
|INTEGER|SQL_INTEGER|  
|LONGCHAR|SQL_LONGVARCHAR|  
  
> [!NOTE]  
>  **SQLGetTypeInfo** restituisce i tipi di dati ODBC. Tutte le conversioni nell'appendice D il *riferimento per programmatori ODBC* sono supportati per i tipi di dati SQL elencati nella tabella precedente.  
  
 La tabella seguente illustra le limitazioni sui tipi di dati di testo.  
  
|Tipo di dati|Description|  
|---------------|-----------------|  
|CHAR|Creazione di una colonna CHAR pari a zero o lunghezza non specificata restituisce una colonna di tipo bit 255.<br /><br /> Nel file delimitati, una colonna CHAR può non avere o virgolette doppie delimitatori all'inizio e alla fine; nei file di lunghezza fissa, le virgolette doppie non vengono utilizzate come delimitatori.|  
|DATETIME|MM-DD-YY (ad esempio, 01-17-92)<br /><br /> MMM GG/AA (ad esempio Gen-17-92)<br /><br /> GG-MMM-AA (ad esempio, 17-Gen-92)<br /><br /> AAAA-MM-GG (ad esempio, 1992-01-17)<br /><br /> AAAA-MMM-GG (ad esempio, 1992-gen-17)<br /><br /> Separatori di data mista non sono consentiti all'interno di una tabella.<br /><br /> L'ISAM Text formatta un campo DATETIME nel formato europeo o Stati Uniti, in base all'impostazione internazionale nel Pannello di controllo di Windows.|  
|FLOAT|La larghezza massima include il segno e il separatore decimale. Nel file Schema.ini, la larghezza viene indicata come indicato di seguito:<br /><br /> 14.083 è FLOAT larghezza 6<br /><br /> -14.083 è FLOAT larghezza 7<br /><br /> +14.083 è FLOAT larghezza 7<br /><br /> 14083. è FLOAT larghezza 6<br /><br /> ODBC restituisce sempre 8 per le colonne FLOAT.<br /><br /> Le colonne FLOAT possono anche essere nella notazione scientifica, ad esempio:<br /><br /> -3.04E + 2 è Float larghezza 8<br /><br /> 25E4 è Float larghezza 4<br /><br /> **Nota** notazione scientifica e decimale non può essere combinata in una colonna.<br /><br /> I valori NULL sono rappresentati da una stringa vuota con zeri iniziali nei file di lunghezza fissa e in file delimitati sono state omesse.<br /><br /> Dati a virgola mobile possono essere aggiunti con spazi vuoti iniziali.|  
|INTEGER|I valori validi per le colonne di tipo INTEGER sono 32767 per -32766.<br /><br /> Nel file Schema.ini, la larghezza viene indicata come indicato di seguito:<br /><br /> 14083 è intero larghezza 5<br /><br /> 0 è 1 larghezza INTEGER<br /><br /> ODBC restituisce sempre 4 per colonne di tipo INTEGER.<br /><br /> La larghezza massima include un segno. La larghezza massima di una colonna INTEGER è 11, anche se la larghezza può essere superiore a causa di spazi vuoti che sono consentiti nelle tabelle in formato fisso.|  
|LONGCHAR|La teoria limita la larghezza di una colonna LONGCHAR in uno a lunghezza fissa oppure tabella delimitata 65500K. Il driver ISAM testo è più probabile fornire un supporto affidabile fino a circa 32 KB.|  
  
 Altre limitazioni sui tipi di dati sono reperibili [limitazioni del tipo di dati](../../odbc/microsoft/data-type-limitations.md).

