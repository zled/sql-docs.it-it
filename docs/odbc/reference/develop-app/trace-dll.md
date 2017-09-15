---
title: DLL di traccia | Documenti Microsoft
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
- trace DLLs [ODBC]
- tracing options [ODBC], trace DLLs
ms.assetid: 5ab99bd3-cdc3-4e2c-8827-932d1fcb6e00
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 22bbb28f42f7bd3c1ec32e01c3451944315861a0
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="trace-dll"></a>DLL di traccia
La DLL che esegue la traccia è uno dei componenti principali di ODBC. La traccia è attualmente fornito come una DLL di esempio nel componente ODBC di Windows SDK, DLL ed è stata precedentemente incluso Microsoft Data Access Components (MDAC) SDK. Pertanto, la voce del Registro di sistema, l'interfaccia e il codice di esempio per la DLL di traccia sono disponibili. Questa DLL può essere sostituita da una traccia DLL generati da un utente ODBC o un fornitore di terze parti. Una DLL di traccia personalizzato è necessario assegnare un nome diverso dalla traccia di esempio originale DLL. DLL di traccia deve essere installata nella directory di sistema o non riuscirà a caricare. Le stringhe di connessione non verrà passate alla DLL di traccia da Gestione Driver.  
  
 La traccia DLL tiene traccia degli argomenti di input, gli argomenti di output, argomenti posticipati, codici restituiti e SQLState. Quando la traccia è abilitata, gestione Driver chiama la DLL di traccia in due punti: una volta immesse funzioni (prima della convalida di argomento) e nuovamente appena prima che la funzione restituisce.  
  
 Quando un'applicazione chiama una funzione, gestione Driver chiama una funzione di traccia nella traccia DLL prima di chiamare la funzione nel driver o l'elaborazione della chiamata a se stesso. Ogni funzione ODBC è una funzione di traccia corrispondente (con prefisso *traccia*) che è identica alla funzione ODBC, fatta eccezione per il nome. Quando viene chiamata la funzione di traccia, traccia DLL acquisisce gli argomenti di input e restituisce un codice restituito. Poiché la DLL di traccia viene chiamata prima di gestione Driver convalida di argomenti, vengono tracciate le chiamate di funzione non valido, in modo vengono registrati errori di transizione di stato e di argomenti non validi.  
  
 Dopo avere chiamato la funzione di traccia nella traccia DLL, gestione Driver chiama la funzione nel driver ODBC. Chiama quindi **TraceReturn** nella DLL di traccia. Questa funzione accetta due argomenti: il valore restituito dalla DLL di traccia per la funzione di traccia e il codice restituito restituita dal driver a gestione Driver per la funzione ODBC (o il valore restituito da Gestione Driver stesso, se la funzione elaborata). La funzione utilizza il valore restituito per la funzione di traccia per modificare i valori di argomento di input acquisita. Scrive il codice restituito per la funzione ODBC per il file di log (o viene visualizzata in modo dinamico, se abilitato). Consente di dereferenziare i puntatori dell'argomento di output e registra i valori degli argomenti di output.
