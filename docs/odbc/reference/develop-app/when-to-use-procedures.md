---
title: Quando utilizzare le procedure | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], procedures
- procedures [ODBC], about procedures
ms.assetid: 7dc9e327-dd54-4b10-9f66-9ef5c074f122
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c8af54a32480f7ae2cd382de53a586f801e7d189
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="when-to-use-procedures"></a>Quando utilizzare le procedure
Esistono diversi vantaggi rispetto all'utilizzo delle procedure, tutte basata sul fatto che tramite le procedure Sposta istruzioni SQL dall'applicazione per l'origine dati. Ciò che resta nell'applicazione è una chiamata di procedura interoperativa. Tali vantaggi includono:  
  
-   **Prestazioni** procedure vengono in genere il modo più rapido per eseguire istruzioni SQL. Ad esempio preparata esecuzione, l'istruzione viene compilato ed eseguito in due fasi distinte. A differenza di esecuzione preparata, procedure vengono eseguite solo in fase di esecuzione. Vengono compilati in un altro momento.  
  
-   **Le regole business** A *regola business* è una regola sul modo in cui una società di business. Ad esempio, solo un utente con il titolo del venditore potrebbe essere consentito per aggiungere nuovi ordini di vendita. Immissione di queste regole nelle procedure consente alle aziende di singoli personalizzare le applicazioni verticali riscrivendo le procedure per l'applicazione chiamate senza dover modificare il codice dell'applicazione. Ad esempio, un'applicazione di immissione ordini potrebbe chiamare la routine **InsertOrder** con un numero fisso di parametri; esattamente come **InsertOrder** viene implementato può variare da una società a.  
  
-   **Replaceability** strettamente correlate per il posizionamento delle regole di business nelle procedure è il fatto che le procedure possono essere sostituite senza ricompilare l'applicazione. Se una regola business viene modificata dopo che una società ha acquistato e installata un'applicazione, la società può sostituire la routine contenente tale regola. Dal punto di vista dell'applicazione, non è stata modificata; comunque, chiama una particolare procedura per completare un'attività particolare.  
  
-   **SQL DBMS specifici** procedure forniscono un modo per le applicazioni di sfruttare SQL DBMS specifici e sono tuttora disponibili interoperativa. Ad esempio, una procedura in un sistema DBMS che supporta le istruzioni di controllo di flusso in SQL potrebbe intercettare e correggere gli errori, mentre una procedura in un sistema DBMS che non supportano le istruzioni di controllo di flusso può semplicemente restituire un errore.  
  
-   **Procedure di restare attiva quando le transazioni** in alcune origini dati, i piani di accesso per le istruzioni preparate tutti su una connessione vengono eliminati quando una transazione viene eseguito il commit o rollback. Inserire le istruzioni SQL in procedure, che sono archiviate in modo permanente nell'origine dati, le istruzioni di superare la transazione. Se le procedure sopravvivono un preparata parzialmente preparata, o non preparato lo stato è specifico del DBMS.  
  
-   **Separare sviluppo** procedure possono essere sviluppate separatamente dal resto dell'applicazione. In grandi aziende, questo potrebbe fornire un modo per sfruttare ulteriormente le competenze di programmatori altamente specializzate. In altre parole, i programmatori di applicazioni è possono scrivere codice dell'interfaccia utente e ai programmatori di database è possono scrivere routine.  
  
 Procedure vengono utilizzate in genere da applicazioni personalizzate e verticale. Queste applicazioni tendono a eseguire attività fissa, ed è possibile per le chiamate di procedura a livello di codice in essi contenuti. Ad esempio, un'applicazione di immissione dell'ordine può chiamare le procedure **InsertOrder**, **DeleteOrder**, **UpdateOrder**, e **GetOrders** .  
  
 È necessario chiamare procedure dalle applicazioni generiche. Le procedure sono scritte in genere per eseguire un'attività nel contesto di una determinata applicazione e quindi non avere alcuna utilità per applicazioni generiche. Ad esempio, un foglio di calcolo non è alcun motivo per chiamare il **InsertOrder** procedure in precedenza. Inoltre, le applicazioni generiche non devono costruire procedure in fase di esecuzione casuali fornendo i tempi di esecuzione istruzione; non solo è questo potrebbe essere più lenta rispetto all'esecuzione diretta o preparata, richiede anche le istruzioni SQL DBMS specifici.  
  
 Un'eccezione il caso gli ambienti di sviluppo di applicazioni, che offrono spesso un modo per i programmatori possono generare istruzioni SQL che può eseguono le procedure e possono costituire un modo per i programmatori di verificare le procedure. Chiamata di questo tipo ambienti **SQLProcedures** alle procedure disponibili elenco e **SQLProcedureColumns** per visualizzare un elenco di parametri di input, input/output e output, la procedura di valore restituito e le colonne di qualsiasi set di risultati creati dalla stored procedure. Tuttavia, tali procedure devono essere sviluppate in anticipo su ogni origine dati. Questa operazione richiede le istruzioni SQL DBMS specifici.  
  
 Esistono tre principali svantaggi all'utilizzo delle procedure. Il primo è che procedure devono essere scritte e compilate per ogni sistema DBMS con cui l'applicazione deve essere eseguita. Sebbene non sia un problema per le applicazioni personalizzate, aumenta notevolmente lo sviluppo e l'ora di manutenzione per le applicazioni verticali progettato per l'esecuzione con un numero di DBMS.  
  
 Il secondo svantaggio è che molti DBMS non supportano le procedure. Anche questo è più probabile che un problema per le applicazioni verticali progettato per l'esecuzione con un numero di DBMS. Per determinare se le procedure sono supportate, un'applicazione chiama **SQLGetInfo** con l'opzione SQL_PROCEDURES.  
  
 Lo svantaggio di terzo, che è applicabile in particolare in ambienti di sviluppo di applicazioni, è che ODBC non viene definita una grammatica standard per la creazione di procedure. Ovvero, sebbene le applicazioni possono chiamare procedure interoperably, non possono creare li interoperably.
