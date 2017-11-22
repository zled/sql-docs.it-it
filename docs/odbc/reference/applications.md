---
title: Applicazioni | Documenti Microsoft
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
- off-the-shelf applications [ODBC]
- ODBC architecture [ODBC], applications
- shrink-wrapped applications [ODBC]
- application development [ODBC], types
- custom applications [ODBC]
- virtual applications [ODBC]
- generic applications [ODBC]
ms.assetid: 39d6461f-0d24-4b7d-a723-843ade15ad73
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 07ea2d2f08fb0d31ed141281b195742462350a5b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="applications"></a>Applicazioni
Un *applicazione* è un programma che chiama l'API ODBC per accedere ai dati. Anche se sono possibili diversi tipi di applicazioni, la maggior parte rientrano in tre categorie, che vengono utilizzate come esempi in questa Guida.  
  
-   **Applicazioni generiche** questi sono anche denominati per le applicazioni con wrapping di riduzione o preconfigurati. Applicazioni generiche sono progettate per funzionare con un'ampia gamma di diversi DBMS. Ad esempio un foglio di calcolo o pacchetto di statistiche che utilizza ODBC per importare i dati per un'ulteriore analisi e un elaboratore di testo che utilizza ODBC per ottenere un elenco di indirizzi da un database.  
  
     Un'importante sottocategoria di applicazioni generiche è ambienti di sviluppo di applicazioni, ad esempio PowerBuilder o Microsoft® Visual Basic®. Sebbene le applicazioni costruite con questi ambienti probabilmente funzionerà solo con un singolo DBMS, ambiente stesso deve essere utilizzato con più DBMS.  
  
     Cosa generiche tutte le applicazioni hanno in comune è che sono estremamente interoperativi tra DBMS e devono utilizzare ODBC in modo relativamente generico. Per ulteriori informazioni sull'interoperabilità, vedere [scelta di un livello di interoperabilità](../../odbc/reference/develop-app/choosing-a-level-of-interoperability.md).  
  
-   **Le applicazioni verticali** applicazioni verticali eseguire un singolo tipo di attività, ad esempio ordini o dati di produzione, di rilevamento e di lavoro con uno schema di database che viene controllato dallo sviluppatore dell'applicazione. Per un determinato cliente, l'applicazione funziona con un singolo DBMS. Ad esempio, una piccola azienda potrebbe utilizzare l'applicazione con dBase, mentre un'azienda di grandi dimensioni potrebbe essere utilizzato con Oracle.  
  
     L'applicazione utilizza ODBC in modo che l'applicazione non è correlato a un qualsiasi DBMS, anche se potrebbero essere associato a un numero limitato di DBMS che offrono funzionalità simili. Di conseguenza, lo sviluppatore di applicazioni è possibile vendere l'applicazione indipendentemente da DBMS. Le applicazioni verticali sono interoperativi quando vengono sviluppati, ma in alcuni casi sono state modificate per includere codice noninteroperable dopo che il cliente avrà scelto un DBMS.  
  
-   **Applicazioni personalizzate** applicazioni personalizzate vengono utilizzate per eseguire un'attività specifica in un'unica società. Ad esempio, un'applicazione di una società di grandi dimensioni potrebbe raccogliere dati di vendita da diverse divisioni (ognuno dei quali utilizza diversi DBMS) e creare un singolo report. ODBC viene utilizzato perché è un'interfaccia comune e Salva i programmatori di dover imparare più interfacce. Tali applicazioni sono in genere interoperativi e vengono scritti i driver e DBMS specifici.  
  
 Un numero di attività è comune a tutte le applicazioni, indipendentemente dalla modalità di uso ODBC. Nel loro insieme, in gran parte definiscono il flusso di qualsiasi applicazione ODBC. Le attività sono:  
  
-   Selezionare un'origine dati e di una connessione.  
  
-   Invio di un'istruzione SQL per l'esecuzione.  
  
-   Il recupero dei risultati (se presente).  
  
-   Errori di elaborazione.  
  
-   Eseguire il commit o il rollback della transazione che racchiude l'istruzione SQL.  
  
-   Disconnessione dall'origine dati.  
  
 Poiché la maggior parte delle operazioni di accesso di dati viene eseguita con SQL, l'attività principale per cui le applicazioni utilizzano ODBC è per inviare istruzioni SQL e recuperare i risultati generati da tali istruzioni (se presente). Altre attività per cui le applicazioni utilizzano ODBC includono stabilire e modifica alle funzionalità del driver e il catalogo del database di esplorazione.
