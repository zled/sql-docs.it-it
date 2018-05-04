---
title: Simulazione posizionato istruzioni Update e Delete | Documenti Microsoft
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
- positioned deletes [ODBC]
- data updates [ODBC], positioned update or delete
- row identifiers [ODBC]
- positioned updates [ODBC]
- updating data [ODBC], positioned update or delete
ms.assetid: b24ed59f-f25b-4646-a135-5f3596abc1a4
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4cfbd54ccd55bc4ce5ef0a4d3776cb5a119e0e1d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="simulating-positioned-update-and-delete-statements"></a>La simulazione di istruzioni Delete e aggiornamento posizionato
Se l'origine dati non supporta l'aggiornamento posizionato e istruzioni delete, il driver consente di simulare questi. Ad esempio, la libreria di cursori ODBC Simula aggiornamento posizionato e istruzioni delete. La strategia generale per la simulazione di aggiornamento posizionato e le istruzioni delete consiste nel convertire le istruzioni posizionate a quelli di ricerca. Questa operazione viene eseguita sostituendo il **WHERE CURRENT OF** clausola con una ricerca **dove** clausola che identifica la riga corrente.  
  
 Ad esempio, perché la colonna CustID identifica in modo univoco ogni riga nella tabella Customers, la posizione delete-istruzione  
  
```  
DELETE FROM Customers WHERE CURRENT OF CustCursor  
```  
  
 potrebbero essere convertiti in  
  
```  
DELETE FROM Customers WHERE (CustID = ?)  
```  
  
 Il driver può utilizzare uno dei seguenti *identificatori di riga* nel **dove** clausola:  
  
-   Colonne i cui valori verranno utilizzati per identificare in modo univoco ogni riga della tabella. Ad esempio, la chiamata **SQLSpecialColumns** con SQL_BEST_ROWID restituisce la colonna o ottimale set di colonne che hanno questo scopo.  
  
-   Pseudocolonne, forniti da alcune origini dati, allo scopo di identificare in modo univoco ogni riga. Questi possono essere recuperati chiamando **SQLSpecialColumns**.  
  
-   Un indice univoco, se disponibile.  
  
-   Tutte le colonne nel set di risultati.  
  
 Esattamente le colonne in cui è consigliabile utilizzare un driver di **dove** clausola costruisce dipende dal driver. In alcuni dati di origini, determinare un identificatore di riga possono essere costose. Tuttavia, è più veloce per eseguire e garantisce che un'istruzione simulata aggiorna o Elimina al massimo una riga. A seconda delle funzionalità del sistema DBMS sottostante, utilizzando un identificatore di riga può essere costosa da configurare. Tuttavia, è più veloce per eseguire e garantisce che un'istruzione simulata aggiornerà o eliminerà solo una riga. La possibilità di usare tutte le colonne nel set di risultati è in genere molto più semplice da configurare. Tuttavia, risulta più lento per l'esecuzione e, se le colonne non identificare in modo univoco una riga, è possibile che nelle righe aggiornati o eliminati accidentalmente, soprattutto quando imposta l'elenco di selezione per il risultato non contiene tutte le colonne presenti nella tabella sottostante.  
  
 A seconda che la strategia precedente il driver supporta, un'applicazione può scegliere la strategia è richiesto il driver da utilizzare con l'attributo di istruzione SQL_ATTR_SIMULATE_CURSOR. Anche se potrebbe sembrare strano che un'applicazione a rischiare accidentalmente l'aggiornamento o eliminazione di una riga, l'applicazione è possibile rimuovere questo rischio, verificare che le colonne nel set di risultati identificano in modo univoco ogni riga nel set di risultati. In questo modo il driver lo sforzo di dover eseguire questa operazione.  
  
 Se il driver sceglie di utilizzare un identificatore di riga, intercetta il **SELECT FOR UPDATE** istruzione che crea il set di risultati. Se le colonne nell'elenco di selezione non consentono di identificare in modo efficace una riga, il driver aggiunge le colonne necessarie alla fine dell'elenco di selezione. Alcune origini dati dispongono di una singola colonna che identifica sempre in modo univoco una riga, ad esempio la colonna ROWID Oracle; Se tale colonna è disponibile, il driver lo utilizza. In caso contrario, il driver chiama **SQLSpecialColumns** per ogni tabella di **FROM** clausola per recuperare un elenco delle colonne che identificano in modo univoco ogni riga. Una restrizione comune che deriva da questa tecnica è che la simulazione di cursore non riesce se è presente più di una tabella nel **FROM** clausola.  
  
 Indipendentemente dalla modalità di identificazione di righe il driver, e in genere rimuove il **FOR UPDATE OF** clausola disattivato il **SELECT FOR UPDATE** istruzione prima di inviarlo all'origine dati. Il **FOR UPDATE OF** clausola viene utilizzata solo con posizionato aggiornamento e istruzioni delete. Origini dati che non supportano posizionato aggiornamento e le istruzioni delete in genere non sono supportati.  
  
 Quando l'applicazione invia un'istruzione delete per l'esecuzione o un aggiornamento posizionato, il driver sostituisce il **WHERE CURRENT OF** clausola con un **dove** clausola che contiene l'identificatore di riga. I valori di queste colonne vengono recuperati da una cache gestita dal driver per ogni colonna viene utilizzata la **dove** clausola. Dopo che il driver ha sostituito il **dove** clausola, invia l'istruzione per l'origine dati per l'esecuzione.  
  
 Ad esempio, si supponga che l'applicazione invia l'istruzione seguente per creare un set di risultati:  
  
```  
SELECT Name, Address, Phone FROM Customers FOR UPDATE OF Phone, Address  
```  
  
 Se l'applicazione ha impostato SQL_ATTR_SIMULATE_CURSOR per richiedere una garanzia di univocità e se l'origine dati non fornisce una pseudo-colonna che identifica sempre in modo univoco una riga, il driver chiama **SQLSpecialColumns** per il Consente di individuare la tabella Customers, CustID è la chiave per la tabella Customers e lo aggiunge all'elenco di selezione e rimuove il **FOR UPDATE OF** clausola:  
  
```  
SELECT Name, Address, Phone, CustID FROM Customers  
```  
  
 Se l'applicazione non ha richiesto una garanzia di unicità, il driver rimuove solo il **FOR UPDATE OF** clausola:  
  
```  
SELECT Name, Address, Phone FROM Customers  
```  
  
 Si supponga che l'applicazione scorre il set di risultati e invia l'istruzione di aggiornamento posizionato seguente per l'esecuzione, in cui Cust è il nome del cursore sul set di risultati:  
  
```  
UPDATE Customers SET Address = ?, Phone = ? WHERE CURRENT OF Cust  
```  
  
 Se l'applicazione non ha richiesto una garanzia di unicità, il driver sostituisce il **dove** clausola e associa il parametro CustID alla variabile nella propria cache:  
  
```  
UPDATE Customers SET Address = ?, Phone = ? WHERE (CustID = ?)  
```  
  
 Se l'applicazione non ha richiesto una garanzia di unicità, il driver sostituisce il **dove** clausola e associa i parametri nome, indirizzo e telefono in questa clausola per le variabili nella propria cache:  
  
```  
UPDATE Customers SET Address = ?, Phone = ?  
   WHERE (Name = ?) AND (Address = ?) AND (Phone = ?)  
```
