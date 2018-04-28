---
title: Traccia di accesso ai dati con il Driver ODBC in Linux e macOS | Documenti Microsoft
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
ms.topic: article
helpviewer_keywords:
- data access tracing
- tracing
ms.assetid: 3149173a-588e-47a0-9f50-edb8e9adf5e8
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4fadd1ddbcf4004b3a6652975c2495db9007d433
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="data-access-tracing-with-the-odbc-driver-on-linux-and-macos"></a>Traccia di accesso ai dati con il Driver ODBC in Linux e macOS
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Gestione Driver unixODBC in macOS e Linux supporta la traccia delle chiamate all'API ODBC in ingresso e uscita del Driver ODBC per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].

Per tracciare il comportamento dell'applicazione ODBC, modificare il `odbcinst.ini` file `[ODBC]` sezione per impostare i valori `Trace=Yes` e `TraceFile` al percorso del file che deve contenere la traccia di output; ad esempio:

```  
Trace=Yes
TraceFile=/home/myappuser/odbctrace.log
```  

(È anche possibile usare `/dev/stdout` o qualsiasi altro nome di dispositivo per inviare l'output sono invece di un file permanente di traccia.) Con le impostazioni sopra riportate, ogni volta che un'applicazione carica gestione Driver unixODBC registrerà tutte le chiamate API ODBC che eseguita nel file di output.

Dopo aver completato l'analisi dell'applicazione, rimuovere `Trace=Yes` dal `odbcinst.ini` per evitare la riduzione delle prestazioni di analisi di file e verificare i file di traccia non necessari vengono rimossi.
  
La traccia si applica a tutte le applicazioni che utilizzano il driver in `odbcinst.ini`. Per non tracciare tutte le applicazioni (ad esempio, per evitare di diffondere informazioni utente riservate), è possibile tracciare una singola istanza dell'applicazione specificando il percorso di una privata `odbcinst.ini`, usando il `ODBCSYSINI` variabile di ambiente. Esempio:  
  
```  
$ ODBCSYSINI=/home/myappuser myapp
```  
  
In questo caso, è possibile aggiungere `Trace=Yes` per il `[ODBC Driver 13 for SQL Server]` sezione `/home/myappuser/odbcinst.ini`.

## <a name="determining-which-odbcini-file-the-driver-is-using"></a>Determinare quali File odbc.ini utilizza il Driver

Il driver ODBC di Linux e macOS non conosce quale `odbc.ini` è in uso o il percorso di `odbc.ini` file. Tuttavia, informazioni su quali `odbc.ini` file è in uso è disponibile in strumenti unixODBC `odbc_config` e `odbcinst`e dalla documentazione di gestione Driver unixODBC.  
  
Ad esempio, il comando seguente stampa (tra le altre informazioni) il percorso di sistema e utente `odbc.ini` file che contengono, rispettivamente, i DSN di sistema e utente:

```
$ odbcinst -j
unixODBC 2.3.1
DRIVERS............: /etc/odbcinst.ini
SYSTEM DATA SOURCES: /etc/odbc.ini
FILE DATA SOURCES..: /etc/ODBCDataSources
USER DATA SOURCES..: /home/odbcuser/.odbc.ini`
SQLULEN Size.......: 8
SQLLEN Size........: 8
SQLSETPOSIROW Size.: 8
```

Il [documentazione unixODBC](http://www.unixodbc.org/doc/UserManual/) vengono illustrate le differenze tra utente e di DSN di sistema. Riepilogo:  

- I DSN utente---si tratta di DSN in cui sono disponibili solo per un utente specifico. Gli utenti possono connettersi utilizzando, aggiungere, modificare e rimuovere i propri DSN utente. DSN utente vengono archiviati in un file nella directory principale dell'utente o una sottodirectory della stessa.
  
- DSN di sistema---questi DSN sono disponibili per ogni utente del sistema per la connessione con essi, ma possono solo essere aggiunto, modificato e rimosso da un amministratore di sistema. Se un utente dispone di un DSN utente con lo stesso nome di DSN di sistema, il DSN utente da utilizzare durante le connessioni per tale utente.

## <a name="see-also"></a>Vedere anche
[Linee guida per la programmazione](../../../connect/odbc/linux-mac/programming-guidelines.md)
