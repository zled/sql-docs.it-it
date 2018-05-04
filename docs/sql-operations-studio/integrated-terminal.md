---
title: Terminal integrata in Studio operazioni SQL (anteprima) | Documenti Microsoft
description: Scopri il terminale integrato in Studio operazioni SQL (anteprima).
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: e33468679c7c499c4f55d25cff2ac816c051e272
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="integrated-terminal"></a>Terminale integrato

In [!INCLUDE[name-sos](../includes/name-sos-short.md)], è possibile aprire un terminale integrato, inizialmente iniziando dalla radice dell'area di lavoro. Può risultare utile perché non è necessario passare windows o modificare lo stato di un terminale esistente per eseguire un'attività da riga di comando rapida.

Per aprire i servizi terminal:

* Utilizzare il **Ctrl +'** tasto di scelta rapida con il carattere apice inverso.
* Utilizzare il **vista** | **Terminal integrata** comando di menu.
* Dal **comando tavolozza** (**Ctrl + MAIUSC + P**), utilizzare il **Terminal integrata Visualizza: Attiva/disattiva** comando.

![Terminal](media/integrated-terminal/terminal-screen.png)

> [!NOTE]
> È comunque possibile aprire una shell esterna con Esplora **nel prompt dei comandi aprire** comando (**aprire terminal** su Mac o Linux) se si preferisce [!INCLUDE[name-sos](../includes/name-sos-short.md)].

## <a name="managing-multiple-terminals"></a>La gestione di più terminali

È possibile creare più terminali aperto in diverse posizioni e spostarsi facilmente tra di esse. È possibile aggiungere istanze terminale facendo clic sull'icona più in alto a destra del **TERMINAL** pannello o al trigger il **Ctrl + Maiusc +'** comando. Consente di creare un'altra voce nell'elenco a discesa che può essere usato per passare tra di essi.

![Terminali di più](media/integrated-terminal/terminal-multiple-instances.png)

Rimuovere le istanze terminale premendo che possibile pulsante Cestino.

> [!TIP]
> Se si utilizzano i terminali più ampiamente, è possibile aggiungere tasti di scelta rapida per il `focusNext`, `focusPrevious` e `kill` comandi descritti nella [sezione delle associazioni di chiave](#key-bindings) per consentire lo spostamento tra di esse utilizzando solo la tastiera.

## <a name="configuration"></a>Configurazione

La shell utilizzata l'impostazione predefinita per `$SHELL` su Linux e macOS, PowerShell in Windows 10 e cmd.exe nelle versioni precedenti di Windows. Questi può essere sottoposto a override manualmente impostando `terminal.integrated.shell.*` in [impostazioni](settings.md). Gli argomenti possono essere passati alla shell terminal Linux e macOS utilizzando il `terminal.integrated.shellArgs.*` impostazioni.

### <a name="windows"></a>Windows

Configurare correttamente la shell in Windows è una questione di individuare il file eseguibile di destra e l'aggiornamento dell'impostazione. Di seguito sono un elenco di file eseguibili di shell comuni e i percorsi predefiniti:

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
> Per essere utilizzato come un terminale integrato, il file eseguibile shell deve essere un'applicazione console in modo che `stdin/stdout/stderr` può essere reindirizzato.

> [!TIP]
> La shell integrata terminal è in esecuzione con le autorizzazioni di [!INCLUDE[name-sos](../includes/name-sos-short.md)]. Se è necessario eseguire un comando della shell con privilegi elevati (amministratore) o autorizzazioni diverse, è possibile utilizzare le utilità di piattaforma, ad esempio `runas.exe` all'interno di un terminale.

### <a name="shell-arguments"></a>Argomenti della shell

Quando viene avviata, è possibile passare argomenti alla shell.

Ad esempio, per abilitare bash in esecuzione come una shell di account di accesso (che viene eseguito `.bash_profile`), passare il `-l` argomento (tra virgolette doppie):

```json
// Linux
"terminal.integrated.shellArgs.linux": ["-l"]
```

## <a name="terminal-display-settings"></a>Impostazioni di visualizzazione terminal

È possibile personalizzare il tipo di terminale integrata e l'altezza della riga con le seguenti impostazioni:

* `terminal.integrated.fontFamily`
* `terminal.integrated.fontSize`
* `terminal.integrated.lineHeight`

## <a id="key-bindings"></a>Terminal tasti di scelta rapida

Il **Visualizza: Attiva/Disattiva integrata Terminal** comando associato a **Ctrl +'** per passare rapidamente il pannello terminal integrato rimosso dalla visualizzazione.

Di seguito sono i tasti di scelta rapida per spostarsi rapidamente nel terminale integrato:

Key|Comando
---|---
**CTRL +'**|Mostra terminal integrata
**CTRL + MAIUSC +'**|Creare nuovo terminale
**CTRL + freccia su**|Scorrere verso l'alto
**CTRL + freccia giù**|Scorrere verso il basso
**CTRL + PGSU**|Pagina di scorrimento in alto
**CTRL + PGGIÙ**|Pagina di scorrimento verso il basso
**CTRL + Home**|Scorrere fino all'inizio
**CTRL + fine**|Scorrere verso il basso
**CTRL + K**|Cancellare i servizi terminal

Altri comandi terminali sono disponibili e possono essere associati ai Preferiti tasti di scelta rapida.

ovvero:

* `workbench.action.terminal.focus`: Concentrare l'attenzione i servizi terminal. Si tratta come elemento toggle, ma si concentra terminal anziché nasconderlo, se è visibile.
* `workbench.action.terminal.focusNext`: Viene illustrata l'istanza successiva terminal.
* `workbench.action.terminal.focusPrevious`: Viene illustrata l'istanza terminal precedente.
* `workbench.action.terminal.kill`: Rimuovere l'istanza terminal corrente.
* `workbench.action.terminal.runSelectedText`: Eseguire il testo selezionato nell'istanza terminal.
* `workbench.action.terminal.runActiveFile`: Eseguire il file attivo nell'istanza terminal.

### <a name="run-selected-text"></a>Eseguire il testo selezionato

Utilizzare il `runSelectedText` comando, selezionare il testo in un editor ed eseguire il comando **Terminal: eseguire il testo selezionato in Terminal attive** tramite il **riquadro comandi** (**Ctrl + MAIUSC + P**). I servizi terminal tenta di eseguire il testo selezionato:

![Eseguire il testo selezionato](media/integrated-terminal/terminal_run_selected.png)

Se è selezionato alcun testo nell'editor attivo, viene eseguita la riga che si trova il cursore su nei Servizi terminal.

### <a name="copy--paste"></a>Copia e Incolla

Per copiare e incollare i tasti di scelta rapida standard piattaforma:

* Linux: **Ctrl + Maiusc + C** e **Ctrl + MAIUSC + V**
* Mac: **Cmd + C** e **Cmd + V**
* Windows: **Ctrl + C** e **Ctrl + V**

### <a name="find"></a>Trova

Il terminale integrata dispone di funzionalità di ricerca di base che può essere attivata con **Ctrl + F**.

Se si desidera **Ctrl + F** per passare alla shell anziché avviare il widget di ricerca in Linux e Windows, è necessario rimuovere il tasto di scelta rapida, come illustrato di seguito:

```js
{ "key": "ctrl+f", "command": "-workbench.action.terminal.focusFindWidget",
                      "when": "terminalFocus" },
```

### <a name="rename-terminal-sessions"></a>Rinominare le sessioni terminal

Le sessioni Terminal integrate possono essere rinominate ora utilizzando il **Terminal: rinominare** (`workbench.action.terminal.rename`) comando. Il nuovo nome viene visualizzato l'elenco a discesa di selezione terminal.

### <a name="forcing-key-bindings-to-pass-through-the-terminal"></a>Utilizzo forzato di tasti di scelta rapida per il passaggio attraverso i servizi terminal

Mentre lo stato attivo si trova in terminal integrato, molti tasti di scelta rapida non funzionerà perché le sequenze di tasti sono passati e utilizzati da terminal stesso. Il `terminal.integrated.commandsToSkipShell` impostazione può essere utilizzata per risolvere il problema. Contiene una matrice di nomi di comando con tasti di scelta rapida ignorare l'elaborazione dalla shell e invece essere elaborati dal [!INCLUDE[name-sos](../includes/name-sos-short.md)] chiave di sistema di associazione. Per impostazione predefinita, questo include tutte le associazioni di chiave terminale oltre un selezionare alcuni diffuse tasti di scelta rapida.

