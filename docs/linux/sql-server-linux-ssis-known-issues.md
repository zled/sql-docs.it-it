---
title: Limitazioni e problemi noti per SSIS in Linux | Documenti Microsoft
description: In questo articolo vengono descritti problemi noti e limitazioni per SQL Server Integration Services (SSIS) nei computer Linux
author: leolimsft
ms.author: lle
ms.reviewer: douglasl
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.workload: Inactive
ms.openlocfilehash: c366afc1b8755a22b13fa6224ec117db045c8dd3
ms.sourcegitcommit: 9d0467265e052b925547aafaca51e5a5e93b7e38
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2018
---
# <a name="limitations-and-known-issues-for-ssis-on-linux"></a>Limitazioni e problemi noti per SSIS in Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Questo articolo descrive problemi noti e limitazioni correnti per SQL Server Integration Services (SSIS) in Linux.

## <a name="general-limitations-and-known-issues"></a>Problemi noti e limitazioni generali

Le funzionalità seguenti non sono supportate in questa versione di SSIS in Linux:
  - Database del catalogo SSIS
  - Esecuzione del pacchetto pianificato dall'agente SQL
  - Autenticazione di Windows
  - Componenti di terze parti
  - Change Data Capture (CDC)
  - Scalabilità orizzontale SSIS
  - Azure Feature Pack per SSIS
  - Supporto di Hadoop e HDFS
  - Microsoft Connector for SAP BW

Per altre limitazioni e problemi noti con SSIS in Linux, vedere il [note sulla versione](sql-server-linux-release-notes.md#ssis).

## <a name="components"></a> Componenti supportati e non supportati

I seguenti componenti di Integration Services predefiniti sono supportati in Linux. Alcuni di essi hanno limitazioni sulla piattaforma Linux, come descritto nelle tabelle seguenti.

Componenti predefiniti ai quali non sono elencati di seguito non sono supportati in Linux.

### <a name="supported-control-flow-tasks"></a>Attività flusso di controllo è supportato
- Inserimento bulk - attività
- Attività Flusso di dati
- Attività Profiling dati
- Attività Esegui SQL
- Attività Esegui istruzione T-SQL
- Attività Espressione
- Attività FTP
- Attività Servizio Web
- XML Task

### <a name="control-flow-tasks-supported-with-limitations"></a>Attività flusso di controllo è supportata con limitazioni

| Attività | Limitazioni |
|------------|---|
| Execute Process Task | Supporta solo modalità in-process. |
| Attività File system | Il *spostamento directory* e *impostare attributi di file* azioni non sono supportate. |
| attività Script | Supporta solo l'API di .NET Framework standard. |
| Invia messaggi - attività | Supporta solo modalità utente anonimo. |
| Attività Trasferisci Database | I percorsi UNC non sono supportati. |
| | |

### <a name="supported-control-flow-containers"></a>Contenitori del flusso di controllo è supportato
- Sequenza - contenitore
- Contenitore Ciclo For
- Contenitore Ciclo Foreach

### <a name="supported-data-flow-sources-and-destinations"></a>Flusso di dati supportati origini e destinazioni
- Origine File non elaborato e destinazione
- Origine XML

### <a name="data-flow-sources-and-destinations-supported-with-limitations"></a>Origini flusso di dati e destinazioni supportate con limitazioni

| Componente | Limitazioni |
|------------|---|
| Destinazione e l'origine ADO.NET | Supporta solo il provider di dati SQLClient. |
| Origine File flat e destinazione | Supporta solo i percorsi dei file di stile di Windows, a cui viene applicata la regola di mapping del percorso predefinito. Ad esempio `D:\home\ssis\travel.csv` diventa `/home/ssis/travel.csv`. |
| Origine OData | Supporta solo l'autenticazione di base. |
| Origine e destinazione ODBC | Supporta i driver ODBC Unicode a 64 bit in Linux. Dipende da Gestione driver UnixODBC in Linux. |
| Origine OLE DB e destinazione | Supporta solo SQL Server Native Client 11.0 e il Provider Microsoft OLE DB per SQL Server. |
| | |

### <a name="supported-data-flow-transformations"></a>Trasformazioni del flusso di dati supportati
- Aggregate
- Controllare il funzionamento di
- Server di distribuzione di dati bilanciati
- Mappa caratteri
- Suddivisione condizionale
- Copia colonna
- Conversione dati
- Colonna derivata
- Esportazione colonna
- Raggruppamento fuzzy
- Ricerca fuzzy
- Importa colonna
- Ricerca
- Merge
- Merge Join
- Multicast
- Pivot
- Conteggio righe
- Dimensione a modifica lenta
- Ordina
- Ricerca termini
- Union All
- UnPivot

### <a name="data-flow-transformations-supported-with-limitations"></a>Trasformazioni di flusso di dati supportate con restrizioni

| Componente | Limitazioni |
|------------|---|
| Comando OLE DB - trasformazione | Stesse limitazioni di origine OLE DB e di destinazione. |
| componente script | Supporta solo l'API di .NET Framework standard. |
| | |

### <a name="supported-and-unsupported-log-providers"></a>Provider di log supportati e non supportati
Tutti i provider di log SSIS predefiniti sono supportati in Linux tranne il provider del registro eventi di Windows.

Il provider di log di SQL Server supporta solo l'autenticazione di SQL. non supporta l'autenticazione di Windows.

I provider di log SSIS per file di testo, per i file XML e per SQL Server Profiler scrivono l'output in un file specificato. Le considerazioni seguenti si applicano al percorso del file:
-   Se non si fornisce un percorso, il provider di log scritto nella directory corrente dell'host. Se l'utente corrente non dispone dell'autorizzazione di scrittura nella directory corrente dell'host, il provider di log genera un errore.
-   È possibile utilizzare una variabile di ambiente in un percorso di file. Se si specifica una variabile di ambiente, viene visualizzato il testo specificato nel percorso del file. Ad esempio, se si specifica `%TMP%/log.txt`, il provider di log aggiunge il testo letterale `/%TMP%/log.txt` nella directory host corrente.

## <a name="related-content-about-ssis-on-linux"></a>Contenuto correlato su SSIS in Linux
-   [Estrarre, trasformare e caricare i dati in Linux con SSIS](sql-server-linux-migrate-ssis.md)
-   [Installare SQL Server Integration Services (SSIS) in Linux](sql-server-linux-setup-ssis.md)
-   [Configurare SQL Server Integration Services in Linux con ssis-conf](sql-server-linux-configure-ssis.md)
-   [Esecuzione in Linux con cron del pacchetto di pianificazione di SQL Server Integration Services](sql-server-linux-schedule-ssis-packages.md)
