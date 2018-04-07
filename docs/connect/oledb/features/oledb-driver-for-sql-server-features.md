---
title: Driver OLE DB per la funzionalità di SQL Server | Documenti Microsoft
description: Driver OLE DB per le funzionalità di SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- MDAC [SQL Server]
- MSOLEDBSQL, about OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], features
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 6c56a145ecfbb986c7ec0124202ff61e89036657
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="ole-db-driver-for-sql-server-features"></a>Driver OLE DB per la funzionalità di SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Oltre a esporre le funzionalità di Windows (in precedenza Microsoft) Data Access Components (WDAC), il Driver OLE DB per SQL Server implementa anche molte altre funzionalità per esporre [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] funzionalità.  
  
## <a name="in-this-section"></a>Contenuto della sezione    
 [Uso del mirroring del database](../../oledb/features/using-database-mirroring.md)  
 Viene illustrato come il Driver OLE DB per SQL Server supporta l'utilizzo di database con mirroring, ovvero la possibilità di mantenere una copia, o mirror, di un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database in un server di standby.  
  
 [Esecuzione di operazioni asincrone](../../oledb/features/performing-asynchronous-operations.md)  
 Viene descritto come il Driver OLE DB per SQL Server supporta le operazioni asincrone, ovvero la possibilità di restituzione immediata senza blocchi sul thread chiamante.  
  
 [Uso di MARS &#40;Multiple Active Result Set&#41;](../../oledb/features/using-multiple-active-result-sets-mars.md)  
 Viene descritto come il Driver OLE DB per SQL Server supporta multiple active result set (MARS). che consente di eseguire e ricevere più set di risultati utilizzando una sola connessione al database.  
  
 [Uso di tipi di dati XML](../../oledb/features/using-xml-data-types.md)  
 Viene descritto come il Driver OLE DB per SQL Server supporta il tipo di dati XML, ovvero un tipo di dati basato su XML che può essere usato come tipo di colonna, tipo di variabile, tipo di parametro o tipo restituito della funzione.  
  
 [Utilizzo di tipi definiti dall'utente](../../oledb/features/using-user-defined-types.md)  
 Viene illustrato come il Driver OLE DB per SQL Server supporta User-Defined tipi (UDT), che estende il sistema di tipi SQL consentendo di archiviare oggetti e strutture di dati personalizzate in un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.  
  
 [Utilizzo di tipi di valori di grandi dimensioni](../../oledb/features/using-large-value-types.md)  
 Viene descritto come il Driver OLE DB per SQL Server supporta i tipi di dati valori di grandi dimensioni, ovvero sono tipi di dati large object (LOB).  
  
 [Modifica delle password a livello di codice](../../oledb/features/changing-passwords-programmatically.md)  
 Viene descritto come il Driver OLE DB per SQL Server supporta la gestione delle password scadute in modo che le password possono ora essere modificate sul client senza il coinvolgimento dell'amministratore.  
  
 [Utilizzo dell'isolamento dello Snapshot](../../oledb/features/working-with-snapshot-isolation.md)  
 Viene descritto come il Driver OLE DB per SQL Server supporta la funzionalità avanzata al controllo delle versioni di riga che consente di migliorare le prestazioni del database, evitando scenari di blocco di lettura / scrittura.  
  
 [Uso delle notifiche delle query](../../oledb/features/working-with-query-notifications.md)  
 Viene descritto come il Driver OLE DB per SQL Server supporta la notifica di tipo consumer in Modifica set di righe.  
  
 [Esecuzione di operazioni di copia bulk](../../oledb/features/performing-bulk-copy-operations.md)  
 Viene illustrato come il Driver OLE DB per SQL Server supporta operazioni di copia bulk che consentono di trasferire grandi quantità di dati in o da un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tabella o vista.  
  
 [Uso della crittografia senza convalida](../../oledb/features/using-encryption-without-validation.md)  
 Viene illustrato come utilizzare il Driver OLE DB per SQL Server per crittografare i dati inviati al server senza convalidare il certificato.  
  
 [Table-Valued Parameters &#40;OLE DB Driver per SQL Server&#41;](../../oledb/features/table-valued-parameters-oledb-driver-for-sql-server.md)  
 Vengono descritti il Driver OLE DB per il supporto di SQL Server per i parametri con valori di tabella.  
  
 [Tipi CLR definiti dall'utente di grandi dimensioni](../../oledb/features/large-clr-user-defined-types.md)  
 Si illustra il supporto dei tipi CRL definiti dall'utente di grandi dimensioni.  
  
 [Supporto FILESTREAM](../../oledb/features/filestream-support.md)  
 Vengono descritti i Driver OLE DB per il supporto di SQL Server per la caratteristica FILESTREAM avanzata.  
  
 [Nome dell'entità servizio &#40;SPN&#41; supporto nelle connessioni Client](../../oledb/features/service-principal-name-spn-support-in-client-connections.md)  
 Si illustra in che modo il supporto per i nomi SPN (nome dell'entità servizio) è stato esteso per consentire l'autenticazione reciproca in tutti i protocolli.  
  
 [Supporto per colonne di tipo sparse nel driver OLE DB per SQL Server](../../oledb/features/sparse-columns-support-in-oledb-driver-for-sql-server.md)  
 Vengono descritti il Driver OLE DB per il supporto di SQL Server per colonne di tipo sparse.  
  
 [Miglioramenti relativi a data e ora](../../oledb/features/date-and-time-improvements.md)  
 Viene descritto il supporto aggiunto per il Driver OLE DB per SQL Server per i tipi di dati data e ora.  
  
 [Individuazione dei metadati](../../oledb/features/metadata-discovery.md)  
 Si illustrano i miglioramenti apportati all'individuazione dei metadati in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].  
  
 [Supporto UTF-16 nel driver OLE DB per SQL Server](../../oledb/features/utf-16-support-in-oledb-driver-for-sql-server.md)  
 Si illustra una modifica nel comportamento introdotta in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Se si fornisce un buffer a lunghezza fissa quando si associa un parametro di risultato o di output di colonna e il **wchar** carattere scritto nel buffer prima che il carattere di terminazione è un punto di codice surrogato alto di una coppia di surrogati e quella successiva **wchar** carattere è un punto di codice surrogato basso, il Driver OLE DB per SQL Server non aggiungerà il punto di codice surrogato alto nel buffer.  
  
 [Driver OLE DB per il supporto di SQL Server per il ripristino di emergenza a disponibilità elevata](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)  
 Viene descritta la modalità di configurazione l'applicazione per sfruttare il ripristino di emergenza a disponibilità elevata, le funzionalità aggiunte in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].  
  
 [Accesso alle informazioni di diagnostica nel log degli eventi estesi](../../oledb/features/accessing-diagnostic-information-in-the-extended-events-log.md)  
 Illustra i miglioramenti al Driver OLE DB per SQL Server e l'analisi di dati che consente di accedere a informazioni di diagnostica nel buffer circolare e registro XEvents.  
  
 [Driver OLE DB per il supporto SQL Server per LocalDB](../../oledb/features/oledb-driver-for-sql-server-support-for-localdb.md)  
 Viene descritto il Driver OLE DB per il supporto di SQL Server per la funzionalità del database locale.  
  
## <a name="see-also"></a>Vedere anche  
 [Driver OLE DB per la programmazione di SQL Server](../../oledb/oledb-driver-for-sql-server-programming.md)      
 [Argomenti relativi alle procedure di OLE DB](../../oledb/ole-db-how-to/ole-db-how-to-topics.md)   
 [Installazione del driver OLE DB per SQL Server](../../oledb/applications/installing-oledb-driver-for-sql-server.md)  
  
  
