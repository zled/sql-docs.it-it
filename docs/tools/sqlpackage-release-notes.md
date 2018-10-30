---
title: Note sulla versione di Microsoft DacFx e sqlpackage | Microsoft Docs
description: Note sulla versione di sqlpackage Microsoft
ms.custom: tools|sos
ms.date: 06/20/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: conceptual
author: pensivebrian
ms.author: broneill
manager: kenvh
ms.openlocfilehash: c146426a9c325eec721e3289d711d0a00a632e2c
ms.sourcegitcommit: 182d77997133a6e4ee71e7a64b4eed6609da0fba
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50050853"
---
# <a name="sqlpackage-release-notes"></a>note sulla versione di Sqlpackage

**[Scaricare la versione più recente](sqlpackage-download.md)**

## <a name="sqlpackage-180"></a>sqlpackage 18.0

Data di rilascio: 24 ottobre 2018  
Build: 15.0.4200.1 

La versione include le seguenti funzionalità e correzioni:

- Aggiunta del supporto per il livello di compatibilità database 150.
- Aggiunta del supporto per le istanze gestite.
- Aggiunta MaxParallelism del parametro della riga di comando per specificare il grado di parallelismo per le operazioni di database.
- Aggiungere AccessToken parametro della riga di comando per specificare un token di autenticazione quando ci si connette a SQL Server.
- Aggiunta del supporto per i tipi di dati BLOB/CLOB di flusso per le importazioni.
- Aggiunta del supporto per UDF scalari opzione 'INLINE'.
- Aggiunta del supporto per la sintassi 'MERGE' nella tabella di grafico.
- Pseudo-colonna non risolto fissa per tabelle grafi.
- Correzione di creazione di un database con file con ottimizzazione per la memoria vengono usati gruppi di tabelle ottimizzate per la memoria.
- Risolto tra cui le proprietà estese per le tabelle esterne.

## <a name="sqlpackage-178"></a>sqlpackage 17.8

Data di rilascio: 22 giugno 2018  
Build: 14.0.4079.2  

La versione include le correzioni seguenti:

- Messaggi di errore per gli errori di connessione, tra cui il messaggio di eccezione SqlClient migliorati.
- Supporta la compressione dell'indice negli indici partizione singola per importazione/esportazione.
- Risolto un problema reverse engineering per set di colonne XML con SQL 2017 e versioni successive.
- Risolto un problema in cui il livello di compatibilità 140 di script è stato ignorato per il Database SQL di Azure.

## <a name="sqlpackage-1741"></a>sqlpackage 17.4.1

Data di rilascio: 25 gennaio 2018  
Build: 14.0.3917.1

La versione include le correzioni seguenti:

- Quando si importa un bacpac del Database SQL di Azure in un'istanza on-premise, correzione di errori a causa di 'chiavi master di Database senza password non sono supportate in questa versione di SQL Server'.
- Supporto delle regole di confronto del catalogo di database.
- Correzione di un errore di colonna pseudo non risolti per tabelle grafi.
- Aggiunta ThreadMaxStackSize del parametro della riga di comando per analizzare TSQL con un numero elevato di istruzioni annidate.
- Risolto tramite il SchemaCompareDataModel con autenticazione di SQL Server per confrontare gli schemi.

## <a name="sqlpackage-1740"></a>sqlpackage 17.4.0

Data di rilascio: 12 dicembre 2017  
Build: 14.0.3881.1

La versione include le correzioni seguenti:

- Non vengono bloccati quando incontra un livello di compatibilità del database non riconosciuto. Al contrario, verrà considerata il Database SQL di Azure più recente o la piattaforma a livello locale.
- Aggiunta del supporto per 'criteri di conservazione temporale' SQL2017 + e Database SQL di Azure.
- Aggiunto /DiagnosticsFile:"C:\Temp\sqlpackage.log" parametro della riga di comando per specificare un percorso di file per salvare le informazioni di diagnostica.
- Parametro della riga di comando /Diagnostics aggiunto per registrare le informazioni di diagnostica nella console.

## <a name="sqlpackage-on-macos-and-linux-001-preview"></a>Sqlpackage in macOS e Linux 0.0.1 (anteprima)

Data di rilascio: 9 maggio 2018  
Build: 15.0.4057.1

Questa versione contiene la build di anteprima lo sviluppo multipiattaforma di sqlpackage destinata a .NET Core 2.0 e può eseguire in macOS e Linux. 

Questa versione è un'anteprima anticipata con problemi noti seguenti:

- Il parametro /p:CommandTimeout è hardcoded su 120.
- Non sono supportati i collaboratori di compilazione e distribuzione.
  - Verranno risolti dopo il passaggio a .NET Core 2.1 dove System.ComponentModel.Composition.dll è supportata.
  - Necessità di gestire i percorsi tra maiuscole e minuscole.
- Non sono supportati i tipi UDT CLR SQL, inclusi i tipi UDT CLR di SQL Server: SqlHierarchyId, SqlGeometry e SqlGeography.
- File con estensione dacpac e bacpac meno recenti che usano la serializzazione dei dati json non sono supportati.
- Riferimento .dacpacs (ad esempio master.dacpac) non possono essere risolti a causa di problemi con i sistemi di file tra maiuscole e minuscole.
  - Soluzione alternativa consiste nel convertire in maiuscolo il nome del file di riferimento (ad esempio MASTER. FILE BACPAC).
