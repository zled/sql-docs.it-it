---
title: SQL Server Profiler - Strumenti-Opzioni (pagina Opzioni generale) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.replay.tools.generaloptions.f1
helpviewer_keywords:
- General Options dialog box
ms.assetid: a888246d-ccfe-415f-bbdc-d6adafac250a
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e0dbabfc0564d1338fb4eec8b9688acd99538576
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48113061"
---
# <a name="sql-server-profiler---tools-options-general-options-page"></a>SQL Server Profiler - Strumenti-Opzioni (pagina Opzioni generali)
  Usare la finestra di dialogo **Opzioni generali** per visualizzare o specificare le opzioni seguenti.  
  
## <a name="options"></a>Opzioni  
  
### <a name="display-options"></a>Opzioni di visualizzazione  
 **Nome carattere**  
 Visualizza il nome del carattere utilizzato nella griglia dei risultati della traccia durante l'esecuzione delle tracce.  
  
 **Dimensioni carattere**  
 Visualizza le dimensioni del carattere utilizzato nella griglia dei risultati della traccia durante l'esecuzione delle tracce.  
  
 **Scegli carattere**  
 Consente di aprire una finestra di dialogo per la modifica delle impostazioni del carattere.  
  
 **Visualizza valori di data e ora in base alle impostazioni internazionali**  
 Visualizza i valori di data e ora in base alle impostazioni internazionali configurate nel computer in uso. Se questa opzione non viene selezionata, i valori di data e ora vengono visualizzati in base al formato predefinito utilizzato da Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]in cui sono inclusi i millisecondi.  
  
> [!NOTE]  
>  L'abilitazione o disabilitazione di questa casella di controllo consente di modificare il formato di visualizzazione delle colonne relative all'ora, ad esempio **StartTime** ed **EndTime**. Tuttavia, non vengono modificati i parametri del valore **DateTime** negli eventi del linguaggio o nelle RPC (Remote Procedure Call).  
  
 **Mostra i valori nella colonna Durata in microsecondi**  
 Visualizza i valori in microsecondi nella colonna di dati **Durata** delle tracce. Per impostazione predefinita, i valori nella colonna **Durata** vengono visualizzati in millisecondi.  
  
### <a name="tracing-options"></a>Opzioni di traccia  
 **Avvia traccia non appena viene stabilita una connessione**  
 La traccia viene avviata utilizzando il modello predefinito non appena viene stabilita una connessione.  
  
 **Aggiorna la definizione di traccia in caso di modifica della versione del provider**  
 Consente di applicare a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] la definizione di traccia più recente quando il provider viene aggiornato. Questo elemento non è selezionato per impostazione predefinita. [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] viene forzato a recuperare la definizione di traccia dal server e a ricreare il file su disco, se un file esiste.  
  
### <a name="file-rollover-options"></a>Opzioni rollover file  
 **Carica tutti i file di rollover in sequenza senza chiedere conferma**  
 I file di rollover vengono caricati automaticamente all'apertura del file di traccia. Se durante la creazione della traccia sono stati creati più file, la selezione di questa opzione determina il caricamento automatico di tutti i file di rollover.  
  
 **Chiedi conferma prima di caricare file di rollover**  
 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] chiede conferma prima di aggiungere un file di rollover quando è aperto un file di traccia.  
  
 **Non caricare mai file di rollover successivi**  
 Il caricamento di file di rollover consecutivi da parte di [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] non viene mai eseguito quando è aperto un file di traccia.  
  
### <a name="replay-options"></a>Opzioni di riproduzione  
 **Numero predefinito di thread di riproduzione**  
 Consente di specificare il numero di thread di riproduzione da utilizzare simultaneamente. Un numero elevato determina un maggior consumo di risorse durante la riproduzione, ma migliora la simultaneità della riproduzione.  
  
 **Intervallo di attesa predefinito Health Monitor (sec)**  
 Consente di specificare l'intervallo di attesa in secondi per la riproduzione. Il valore predefinito è 3600 secondi (1 ora). Questa impostazione influisce sulla quantità di tempo durante la quale è consentita l'esecuzione di un thread prima che questo venga terminato da Health Monitor.  
  
 **Intervallo di polling predefinito Health Monitor (sec)**  
 Consente di specificare l'intervallo di polling in secondi di Health Monitor durante la riproduzione. Il valore predefinito è 60 secondi. Questo valore consente di configurare la frequenza con cui Health Monitor esegue il polling di candidati per la terminazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Avviare una traccia automaticamente dopo la connessione a un Server &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md)   
 [Impostare i valori predefiniti di visualizzazione traccia &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md)   
 [Riprodurre una tabella di traccia &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md)   
 [Riprodurre un file di traccia &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md)   
 [Riprodurre le tracce](../tools/sql-server-profiler/replay-traces.md)   
 [Impostare le opzioni di traccia globali &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/set-global-trace-options-sql-server-profiler.md)   
 [Modelli e autorizzazioni di SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
