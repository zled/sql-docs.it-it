---
title: Funzioni stringa | Documenti Microsoft
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
- functions [ODBC], string functions
- string functions [ODBC]
ms.assetid: 270f669e-8aab-4db0-95a4-f2b3c69538b3
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 03f783cbc287d9c315844e1a9df53187e4e2ba28
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="string-functions"></a>Funzioni per i valori stringa
La tabella seguente elenca le funzioni di modifica di stringa. Un'applicazione può determinare le funzioni di stringa supportate da un driver chiamando **SQLGetInfo** con un *tipo di informazioni* di SQL_STRING_FUNCTIONS.  
  
## <a name="remarks"></a>Osservazioni  
 Gli argomenti indicati come *string_exp* può essere il nome di una colonna, un *valore letterale stringa di caratteri*, o il risultato di un'altra funzione scalare, in cui il tipo di dati sottostante può essere rappresentato come SQL_CHAR, SQL _ VARCHAR o SQL_LONGVARCHAR.  
  
 Gli argomenti indicati come *character_exp* sono una stringa di caratteri a lunghezza variabile.  
  
 Gli argomenti indicati come *avviare*, *lunghezza*, o *conteggio* può essere un *valore letterale numerico* o il risultato di un'altra funzione scalare, in cui il tipo di dati sottostante può essere rappresentato come SQL_TINYINT, SQL_SMALLINT o SQL_INTEGER.  
  
 Le funzioni di stringa elencate di seguito sono in base 1. ovvero, il primo carattere nella stringa è 1 carattere.  
  
 Le funzioni scalari stringa BIT_LENGTH, CHAR_LENGTH, CHARACTER_LENGTH, OCTET_LENGTH e posizione sono state aggiunte in ODBC 3.0 per la compatibilità con SQL-92.  
  
|Funzione|Description|  
|--------------|-----------------|  
|**ASCII (** *string_exp* **)** (ODBC 1.0)|Restituisce il codice ASCII del carattere più a sinistra di *string_exp* come numero intero.|  
|**BIT_LENGTH (** *string_exp* **)** (ODBC 3.0)|Restituisce la lunghezza in bit dell'espressione stringa.<br /><br /> Funziona solo per i tipi di dati stringa, pertanto verrà non in modo implicito convert *string_exp* in una stringa ma restituisce le dimensioni (interna) di qualsiasi tipo di dati è specificato.|  
|**CHAR (** *codice* **)** (ODBC 1.0)|Restituisce il carattere ASCII con codice specificato dal valore *codice*. Il valore di *codice* deve essere compreso tra 0 e 255; in caso contrario, il valore restituito dipende dall'origine dati.|  
|**CHAR_LENGTH (** *string_exp* **)** (ODBC 3.0)|Restituisce la lunghezza in caratteri dell'espressione stringa, se l'espressione stringa di un tipo di dati character; in caso contrario, restituisce la lunghezza in byte dell'espressione stringa (intero più piccolo non minore del numero di bit diviso per 8). (Questa funzione è lo stesso della funzione CHARACTER_LENGTH).|  
|**CHARACTER_LENGTH (** *string_exp* **)** (ODBC 3.0)|Restituisce la lunghezza in caratteri dell'espressione stringa, se l'espressione stringa di un tipo di dati character; in caso contrario, restituisce la lunghezza in byte dell'espressione stringa (intero più piccolo non minore del numero di bit diviso per 8). (Questa funzione è lo stesso della funzione CHAR_LENGTH).|  
|**CONCAT (** *string_exp1*,*string_exp2 e * * *)** (ODBC 1.0)|Restituisce una stringa di caratteri che rappresenta il risultato della concatenazione *string_exp2 e* a *string_exp1*. La stringa risultante dipende da DBMS. Ad esempio, se la colonna rappresentata da *string_exp1* contiene un valore NULL, DB2, verrà restituito NULL, ma SQL Server restituisce la stringa non NULL.|  
|**DIFFERENZA (** *string_exp1*,*string_exp2 e * * *)** (ODBC 2.0)|Restituisce un valore intero che indica la differenza tra i valori restituiti dalla funzione SOUNDEX per *string_exp1* e *string_exp2 e*.|  
|**INSERT (** *string_exp1*, *start*, *lunghezza*, *string_exp2 e * * *)** (ODBC 1.0)|Restituisce un carattere stringa dove *lunghezza* caratteri sono stati eliminati dal *string_exp1*, a partire da *avviare*e in cui *string_exp2 e* è stato inserito in *string_exp,* a partire da *avviare*.|  
|**LCASE (** *string_exp* **)** (ODBC 1.0)|Restituisce una stringa uguale a quello in *string_exp*, con tutti i caratteri maiuscoli caratteri convertiti in caratteri minuscoli.|  
|**A sinistra (** *string_exp*, *conteggio * * *)** (ODBC 1.0)|Restituisce il più a sinistra *conteggio* caratteri di *string_exp*.|  
|**LUNGHEZZA (** *string_exp* **)** (ODBC 1.0)|Restituisce il numero di caratteri in *string_exp,* esclusi gli spazi vuoti finali.<br /><br /> **LUNGHEZZA** accetta solo stringhe. Di conseguenza in modo implicito convertirà *string_exp* in una stringa e restituire la lunghezza di questa stringa (non la dimensione del tipo di dati interna).|  
|**INDIVIDUARE (** *string_exp1*, *string_exp2 e*[, *avviare*]**)** (ODBC 1.0)|Restituisce la posizione iniziale della prima occorrenza di *string_exp1* all'interno di *string_exp2 e*. La ricerca per la prima occorrenza di *string_exp1* inizia con la posizione del primo carattere in *string_exp2 e* , a meno che l'argomento facoltativo, *avviare*, viene specificato. Se *avviare* è specificato, la ricerca inizia con la posizione del carattere indicata dal valore di *avviare*. La prima posizione in *string_exp2 e* è indicato dal valore 1. Se *string_exp1* non viene trovato all'interno di *string_exp2 e*, viene restituito il valore 0.<br /><br /> Se un'applicazione può chiamare la funzione scalare di individuare con il *string_exp1*, *string_exp2 e*, e *avviare* argomenti, il driver restituisce SQL_FN_STR_LOCATE quando  **SQLGetInfo** viene chiamato con un *opzione* di SQL_STRING_FUNCTIONS. Se l'applicazione può chiamare la funzione scalare di individuare solo con il *string_exp1* e *string_exp2 e* argomenti, il driver restituisce SQL_FN_STR_LOCATE_2 quando **SQLGetInfo**viene chiamato con un *opzione* di SQL_STRING_FUNCTIONS. Driver che supportano chiamando la funzione di individuare con due o tre argomenti restituire SQL_FN_STR_LOCATE e SQL_FN_STR_LOCATE_2.|  
|**LTRIM (** *string_exp* **)** (ODBC 1.0)|Restituisce i caratteri di *string_exp*, rimuovere gli spazi vuoti iniziali.|  
|**Funzione OCTET_LENGTH (** *string_exp* **)** (ODBC 3.0)|Restituisce la lunghezza in byte dell'espressione stringa. Il risultato è il più piccolo numero integer non inferiore al numero di bit diviso per 8.<br /><br /> Funziona solo per i tipi di dati stringa, pertanto verrà non in modo implicito convert *string_exp* in una stringa ma restituisce le dimensioni (interna) di qualsiasi tipo di dati è specificato.|  
|**POSIZIONE (** *character_exp* **IN** *character_exp * * *)** (ODBC 3.0)|Restituisce la posizione della prima espressione di caratteri nella seconda espressione di caratteri. Il risultato è un numerico esatto con scala 0 e un valore di precisione definito dall'implementazione.|  
|**Ripetere (** *string_exp,* *conteggio * * *)** (ODBC 1.0)|Restituisce una stringa di caratteri costituita *string_exp* ripetuto *conteggio* volte.|  
|**Sostituisci (** *string_exp1*, *string_exp2 e*, *string_exp3 * * *)** (ODBC 1.0)|Ricerca *string_exp1* foroccurrences di *string_exp2 e*e sostituire con *string_exp3*.|  
|**RIGHT (** *string_exp*, *conteggio * * *)** (ODBC 1.0)|Restituisce il più a destra *conteggio* caratteri di *string_exp*.|  
|**RTRIM (** *string_exp* **)** (ODBC 1.0)|Restituisce i caratteri di *string_exp* rimossi gli spazi vuoti finali.|  
|**SOUNDEX (** *string_exp* **)** (ODBC 2.0)|Restituisce una stringa di caratteri dipende dall'origine dati che rappresenta il suono delle parole nella *string_exp*. Ad esempio, SQL Server restituisce un codice SOUNDEX di 4 cifre; Oracle restituisce una rappresentazione fonetica di ogni parola.|  
|**Lo spazio (** *conteggio* **)** (ODBC 2.0)|Restituisce una stringa di caratteri costituito *conteggio* spazi.|  
|**SUBSTRING (** *string_exp*, *start*, lunghezza **)** (ODBC 1.0)|Restituisce una stringa di caratteri che è derivata da *string_exp*, a partire dalla posizione del carattere specificata da *avviare* per *lunghezza* caratteri.|  
|**UCASE (** *string_exp* **)** (ODBC 1.0)|Restituisce una stringa uguale a quello in *string_exp*, con tutti minuscoli convertiti in caratteri maiuscoli.|
