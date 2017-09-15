---
title: Accesso al Database di rete | Documenti Microsoft
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
- ODBC [ODBC], database access
- SQL [ODBC], database access
- database access [ODBC]
- network database access [ODBC]
- standardizing database access [ODBC], network
ms.assetid: f31dd938-e992-436b-b613-145c23973064
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5220da346aea15e2dc56224001b0d803c90e0047
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="network-database-access"></a>Accesso alla rete del Database
Accesso a un database in una rete richiede un numero di componenti, ognuno dei quali è indipendente e si trova di sotto, l'interfaccia di programmazione. Questi componenti sono illustrati nella figura seguente.  
  
 ![Componenti di accedere a un database in una rete](../../odbc/reference/media/pr04.gif "pr04")  
  
 Una descrizione più dettagliata di ogni componente di seguito:  
  
-   **Interfaccia di programmazione** come descritto in precedenza in questa sezione, l'interfaccia di programmazione contiene le chiamate effettuate dall'applicazione. Queste interfacce (embedded SQL, SQL, moduli e interfacce a livello di chiamata) sono in genere specifici per ogni sistema DBMS, anche se sono in genere basate su uno standard ANSI o ISO.  
  
-   **Protocollo di flusso di dati** il protocollo di flusso di dati descrive il flusso di dati trasferiti tra il sistema DBMS e il relativo client. Ad esempio, il protocollo potrebbe richiedere il primo byte per descrivere il resto del flusso di contenuto: un'istruzione SQL da eseguire, un valore di errore restituito, o ha restituito dati. Il formato del resto dei dati nel flusso dipenderanno quindi questo flag. Ad esempio, un flusso di errore potrebbe contenere un messaggio di errore, un codice di errore di integer a 2 byte, una lunghezza del messaggio di errore di integer a 2 byte e il flag.  
  
     Il protocollo di flusso di dati è un protocollo logico ed è indipendente dei protocolli utilizzati dalla rete sottostante. Di conseguenza, un protocollo di flusso di dati single in genere consente un numero di reti diverse. I protocolli di flusso di dati sono in genere proprietari e sono stati ottimizzati per l'utilizzo di un determinato DBMS.  
  
-   **Meccanismo di comunicazione interprocesso** il meccanismo di comunicazione interprocesso (IPC) è il processo mediante il quale un processo comunica con un altro. Esempi includono DECnet socket, socket TCP/IP e named pipe. La scelta del meccanismo IPC è vincolata dal sistema operativo e la rete in uso.  
  
-   **Protocollo di rete** viene utilizzato il protocollo di rete per il trasporto del flusso di dati in una rete. Può essere considerato l'infrastruttura che supporta i meccanismi IPC utilizzati per implementare i dati di flusso di protocollo, nonché il supporto di operazioni di rete di base, ad esempio i trasferimenti di file e stampanti. Protocolli di rete includono NetBEUI, TCP/IP, DECnet e SPX/IPX e sono specifici per ogni rete.
