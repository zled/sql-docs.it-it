---
title: Allineamento | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- alignment issues [ODBC]
ms.assetid: 06a01e51-e7a5-495f-aa27-e304b0d005ff
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 527e8d47d4d352a0fad579d3c12c5ef3768c402b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="alignment"></a>Alignment
I problemi di allineamento in un'applicazione ODBC in genere non sono diversi rispetto a qualsiasi altra applicazione. Ovvero, la maggior parte delle applicazioni ODBC persistono poche o nessuna con allineamento. Sanzioni per l'allineamento non indirizzi variare in base all'hardware e del sistema operativo e potrebbero essere minore come una riduzione delle lieve miglioramento delle prestazioni o come principale come un errore irreversibile in fase di esecuzione. Pertanto, le applicazioni ODBC e le applicazioni ODBC portabile, in particolare, devono prestare attenzione a allineare correttamente i dati.  
  
 Un esempio di quando le applicazioni ODBC rilevano problemi di allineamento è quando allocare un blocco di memoria di grandi dimensioni e associare le colonne in un set di risultati di diverse parti di tale memoria. Si tratta probabilmente si verifica quando un'applicazione generica deve determinare la forma di un set di risultati in fase di esecuzione e allocare e associare memoria di conseguenza.  
  
 Ad esempio, si supponga che un'applicazione esegue un **selezionare** istruzione immessi dall'utente e recupera i risultati dell'istruzione. Poiché la forma di questo set di risultati non è noto quando il programma è stato scritto, l'applicazione deve determinare il tipo di ogni colonna dopo la creazione di set di risultati e associare memoria di conseguenza. Il modo più semplice per eseguire questa operazione è per allocare un blocco di memoria di grandi dimensioni e associare ogni colonna indirizzi diversi in tale blocco. Per accedere ai dati in una colonna, l'applicazione esegue il cast della memoria associata a tale colonna.  
  
 Il diagramma seguente mostra i risultati di esempio impostata e come sia associato un blocco di memoria utilizzando il tipo di dati C predefinito per ogni tipo di dati SQL. Ogni "X" rappresenta un singolo byte di memoria. (In questo esempio mostra solo i buffer di dati che sono associati alle colonne. Per semplicità, questa operazione viene eseguita. Nel codice effettivo, i buffer di lunghezza/indicatore devono inoltre essere allineati.)  
  
 ![Associazione in base al tipo di dati C predefinito al tipo di dati SQL](../../../odbc/reference/develop-app/media/pr24.gif "pr24")  
  
 Supponendo che gli indirizzi associati vengono archiviati nel *indirizzo* matrice, l'applicazione utilizza le espressioni seguenti per accedere alla memoria associata a ogni colonna:  
  
```  
(SQLCHAR *)       Address[0]  
(SQLSMALLINT *)   Address[1]  
(SQLINTEGER *)    Address[2]  
```  
  
 Si noti che gli indirizzi associati al secondo e terzo colonne avviare in byte dispari e che l'indirizzo è associato alla terza colonna non è divisibile per quattro elementi, ovvero le dimensioni di un SDWORD. In alcuni computer, non sarà un problema. in altri, causerebbe una riduzione delle lieve miglioramento delle prestazioni; nelle ancora altre causerebbe un errore irreversibile in fase di esecuzione. Una soluzione migliore, è possibile allineare ogni indirizzo associato al limite di allineamento naturale. Presupponendo che si tratta di 1 per un UCHAR, 2 per un SWORD e 4 per un SDWORD, questo il risultato sarà illustrato nella figura seguente, dove "X" rappresenta un byte di memoria utilizzata e un'operazione "O" rappresenta un byte di memoria che è inutilizzato.  
  
 ![Associazione tramite limite di allineamento naturale](../../../odbc/reference/develop-app/media/pr25.gif "pr25")  
  
 Questa soluzione non utilizza tutta la memoria dell'applicazione, non viene rilevato eventuali problemi di allineamento. Sfortunatamente, accetta una notevole quantità di codice per implementare questa soluzione, ogni colonna deve essere allineato singolarmente in base al relativo tipo. È una soluzione più semplice per allineare tutte le colonne sulle dimensioni del limite di allineamento massimo, è 4 nell'esempio illustrato nella figura seguente.  
  
 ![Associazione tramite limite di allineamento massimo](../../../odbc/reference/develop-app/media/pr26.gif "pr26")  
  
 Sebbene questa soluzione lascia fori maggiori, il codice per l'implementazione è relativamente semplice e veloce. Nella maggior parte dei casi, questo viene eseguito l'offset di penalità a pagamento in memoria inutilizzata. Per un esempio che utilizza questo metodo, vedere [SQLBindCol utilizzando](../../../odbc/reference/develop-app/using-sqlbindcol.md).
