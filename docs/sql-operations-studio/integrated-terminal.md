---
title: Terminale integrato in SQL Operations Studio (anteprima) | Microsoft Docs
description: Scopri il terminale integrato in SQL Operations Studio (anteprima).
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: 
ms.topic: article
author: yualan
ms.author: alayu
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b55e86314dd075b61dac5751b29fc541fdf1e2c4
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="integrated-terminal"></a>Terminale integrato

In [!INCLUDE[name-sos](../includes/name-sos-short.md)] è possibile aprire un terminale integrato, inizialmente partendo dalla cartella principale dell'area di lavoro. Ciò risulta utile in quanto non è necessario passare windows o modificare lo stato di un terminale esistente per eseguire un'attività rapida da riga di comando.

Per aprire il terminale:

* Premere **Ctrl+`** con il carattere apice inverso.
* Selezionare il comando **Terminale integrato** dal menu **Visualizza**.
* Dal **riquadro comandi** (**Ctrl+MAIUSC+P**), selezionare il comando **Visualizza: Attiva/disattiva il terminale integrato**.

![Terminale](media/integrated-terminal/terminal-screen.png)

> [!NOTE]
> È comunque possibile aprire una shell esterna del terminale usando il comando **Apri con il prompt dei comandi** su Windows Explorer (**Apri terminale** su Mac o Linux) se si preferisce lavorare fuori da [!INCLUDE[name-sos](../includes/name-sos-short.md)].

## <a name="managing-multiple-terminals"></a>Gestione di più terminali

È possibile creare più terminali aperti in diverse posizioni e spostarsi facilmente tra di essi. È possibile infatti aggiungere più istanze del terminale facendo clic sull'icona "+" (più) in alto a destra del pannello **TERMINALE** o premendo **Ctrl+Maiusc+`**. Ogni istanza creata aggiunge un'altra voce nell'elenco a discesa in alto a destra, il quale può essere usato per selezionare i vari terminali.

![Più Terminali](media/integrated-terminal/terminal-multiple-instances.png)

Per rimuovere le istanze create premere l'icona del cestino.

> [!TIP]
> Se si utilizzano i terminali più ampiamente, è possibile aggiungere tasti di scelta rapida per i comandi `focusNext`, `focusPrevious` e `kill`, descritti nella [sezione delle associazioni dei tasti](#key-bindings) per consentire lo spostamento tra le istanze utilizzando solo la tastiera.

## <a name="configuration"></a>Configurazione

La shell utilizza l'impostazione predefinita per `$SHELL` su Linux e macOS, PowerShell in Windows 10 e cmd.exe nelle versioni precedenti di Windows. Questo può essere ridefinito manualmente impostando `terminal.integrated.shell.*` nelle [impostazioni](settings.md). Gli argomenti possono essere passati alla shell per Linux e macOS utilizzando l'impostazione `terminal.integrated.shellArgs.*`.

### <a name="windows"></a>Windows

Configurare correttamente la shell in Windows corrisponde ad individuare il file eseguibile corretto e aggiornare l'impostazione. Di seguito un elenco di file eseguibili di shell comuni e i percorsi predefiniti:

```json
// 64-bit cmd if available, otherwise 32-bit
"terminal.integrated.shell.windows": "C:\\Windows\\sysnative\\cmd.exe"
// 64-bit PowerShell if available, otherwise 32-bit
"terminal.integrated.shell.windows": "C:\\Windows\\sysnative\\WindowsPowerShell\\v1.0\\powershell.exe"
// Git Bash
"terminal.integrated.shell.windows": "C:\\Program Files\\Git\\bin\\bash.exe"
// Bash on Ubuntu (on Windows)
"terminal.integrated.shell.windows": "C:\\Windows\\sysnative\\bash.exe"
```

> [!NOTE]
> Per essere utilizzato come un terminale integrato, il file eseguibile della shell deve essere un'applicazione console in modo che `stdin/stdout/stderr` possano essere reindirizzati.

> [!TIP]
> La shell integrata del terminale è in esecuzione con le autorizzazioni di [!INCLUDE[name-sos](../includes/name-sos-short.md)]. Se è necessario eseguire un comando con privilegi elevati (amministratore) o autorizzazioni diverse, è possibile utilizzare le utilità della piattaforma, ad esempio `runas.exe` all'interno di un terminale.

### <a name="shell-arguments"></a>Argomenti della shell

Quando viene avviata, è possibile passare argomenti alla shell.

Ad esempio, per eseguire bash come una shell di account di accesso (viene eseguito `.bash_profile`), passare l'argomento `-l` (tra virgolette doppie):

```json
// Linux
"terminal.integrated.shellArgs.linux": ["-l"]
```

## <a name="terminal-display-settings"></a>Impostazioni di visualizzazione del terminale

È possibile personalizzare il carattere e l'altezza della riga nel terminale integrato con le seguenti impostazioni:

* `terminal.integrated.fontFamily`
* `terminal.integrated.fontSize`
* `terminal.integrated.lineHeight`

## <a id="key-bindings"></a>Tasti di scelta rapida del terminale

Il comando **Visualizza: Attiva/disattiva il terminale integrato** è associato a **Ctrl+`** e mostra/nasconde rapidamente il pannello del terminale integrato.

Di seguito sono elencati i tasti di scelta rapida per spostarsi rapidamente nel terminale integrato:

Key|Comando
---|---
**CTRL+`**|Mostra terminale integrato
**CTRL+MAIUSC+`**|Crea un nuovo terminale
**CTRL+freccia su**|Scorre verso l'alto
**CTRL+freccia giù**|Scorre verso il basso
**CTRL+PGSU**|Scorre di una pagina verso l'alto
**CTRL+PGGIÙ**|Scorre di una pagina verso il basso
**CTRL+Home**|Scorre fino all'inizio
**CTRL+fine**|Scorre fino alla fine
**CTRL+K**|Pulisce il contenuto del terminale

Sono disponibili altri comandi e possono essere associati ai tasti di scelta rapida che preferite.

Sono:

* `workbench.action.terminal.focus`: Lo stato attivo del terminale. Simile ad un Attiva/Disattiva, ma pone il focus sul terminale anziché nasconderlo, se è visibile.
* `workbench.action.terminal.focusNext`: Mostra l'istanza di terminale successiva.
* `workbench.action.terminal.focusPrevious`: Mostra l'istanza di terminale precedente.
* `workbench.action.terminal.kill`: Rimuove l'istanza di terminale corrente.
* `workbench.action.terminal.runSelectedText`: Esegue il testo selezionato nell'istanza di terminale.
* `workbench.action.terminal.runActiveFile`: Esegue il file attivo nell'istanza di terminale.

### <a name="run-selected-text"></a>Eseguire il testo selezionato

Al fine di utilizzare il comando `runSelectedText`, selezionare il testo in un editor ed eseguire il comando **Terminale: Esegui il testo selezionato nel terminale attivo** tramite il **riquadro comandi** (**Ctrl+MAIUSC+P**). Il terminale proverà ad eseguire il testo selezionato:

![Eseguire il testo selezionato](media/integrated-terminal/terminal_run_selected.png)

Se non è selezionato alcun testo nell'editor attivo, viene eseguita nel terminale la riga su cui si trova il cursore.

### <a name="copy--paste"></a>Copia e Incolla

I tasti di scelta rapida per copiare e incollare seguono gli standard di piattaforma:

* Linux: **Ctrl+Maiusc+C** e **Ctrl+MAIUSC+V**
* Mac: **Cmd+C** e **Cmd+V**
* Windows: **Ctrl+C** e **Ctrl+V**

### <a name="find"></a>Trova

Il terminale integrato dispone di funzionalità di ricerca di base attivabile tramite **Ctrl+F**.

Se si desidera che **Ctrl+F** venga eseguito sulla shell anziché come ricerca in Linux e Windows, è necessario rimuovere il tasto di scelta rapida:

```js
{ "key": "ctrl+f", "command": "-workbench.action.terminal.focusFindWidget",
                      "when": "terminalFocus" },
```

### <a name="rename-terminal-sessions"></a>Rinominare le sessioni del terminale

Le sessioni del terminale integrato possono essere rinominate ora utilizzando il comando **Terminale: Rinomina** (`workbench.action.terminal.rename`). Il nuovo nome viene visualizzato nell'elenco a discesa di selezione terminale.

### <a name="forcing-key-bindings-to-pass-through-the-terminal"></a>Utilizzo forzato di tasti di scelta rapida per il passaggio tra i terminali

Mentre il terminale integrato è attivo, molti tasti di scelta rapida non funzioneranno perché tali sequenze sono utilizzati dal terminale stesso. L'impostazione `terminal.integrated.commandsToSkipShell` può essere utilizzata per risolvere il problema. Contiene una lista di nomi di comando con tasti di scelta rapida che verranno ignorati dalla shell al fine di essere elaborati dal sistema di associazione tasti di [!INCLUDE[name-sos](../includes/name-sos-short.md)]. Per impostazione predefinita, questo include tutte le associazioni di tasti del terminale più una selezione di alcuni dei più comuni tasti di scelta rapida.

