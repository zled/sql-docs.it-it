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
ms.openlocfilehash: 55df71c62fddfe6d21abb27235b287963b946709
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47754334"
---
# <a name="sqlpackage-release-notes"></a>note sulla versione di Sqlpackage

**[Scaricare la versione più recente](sqlpackage-download.md)**

## <a name="sqlpackage-178"></a>sqlpackage 17.8

Data di rilascio: 22 giugno 2018  
Build: 14.0.4079.2  

La versione include le correzioni seguenti:

- Messaggi di errore per gli errori di connessione, tra cui il messaggio di eccezione SqlClient migliorati.
- Aggiunta MaxParallelism del parametro della riga di comando per specificare il grado di parallelismo per le operazioni di database.
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
