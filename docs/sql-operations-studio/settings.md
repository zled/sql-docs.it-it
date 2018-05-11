---
title: Impostazioni utente e dell'area di lavoro in SQL Operations Studio (anteprima) | Microsoft Docs
description: Come modificare le impostazioni utente e dell'area di lavoro in SQL Operations Studio (anteprima).
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
ms.openlocfilehash: 93dd73b9ba77e45f284062e8a768c3f035bcac1b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="user-and-workspace-settings"></a>Impostazioni utente e dell'area di lavoro

È facile da configurare [!INCLUDE[name-sos](../includes/name-sos-short.md)] alle proprie esigenze tramite le impostazioni. Quasi tutte le parti di [!INCLUDE[name-sos](../includes/name-sos-short.md)]dell'editor, interfaccia utente e un comportamento funzionale sono disponibili opzioni è possibile modificare.

[!INCLUDE[name-sos](../includes/name-sos-short.md)] fornisce due ambiti diversi per le impostazioni:

* **Utente** : queste impostazioni si applicano globalmente a qualsiasi istanza di[!INCLUDE[name-sos](../includes/name-sos-short.md)].
* **Area di lavoro**: sono impostazioni specifiche di una cartella nel computer e sono disponibili solo quando la cartella è aperta in Esplora risorse dalla barra laterale. Le impostazioni definite in questo ambito ridefiniscono quelle di ambito utente.

## <a name="creating-user-and-workspace-settings"></a>Creazione di impostazioni utente e dell'area di lavoro

Il comando di menu **File** > **Preferenze** > **Impostazioni** (**sqlops**  >  **Preferenze** > **Impostazioni** su Mac) fornisce il punto di ingresso per configurare le impostazioni utente e dell'area di lavoro. Esse vengono fornite con un elenco di impostazioni predefinite. Copiare qualsiasi impostazione si desideri modificare nell'appropriato file `settings.json`. Le schede a destra consentono di passare rapidamente tra i file delle impostazioni utente e dell'area di lavoro.

È inoltre possibile aprire le impostazioni utente e dell'area di lavoro dal **Riquadro comandi** (**Ctrl + MAIUSC + P**) con **Preferenze: Apri impostazioni utente** e  **Preferenze: Apri impostazioni area di lavoro** o utilizzare il tasto di scelta rapida (**Ctrl +**).

Nell'esempio seguente disabilita i numeri di riga nell'editor e configura le righe di codice per essere rientrate automaticamente.

![Impostazioni di esempio](media/settings/sample-settings.png)

Le modifiche alle impostazioni vengono ricaricate da [!INCLUDE[name-sos](../includes/name-sos-short.md)] dopo aver modificato e salvato il file `settings.json`.

>**Nota:** le impostazioni dell'area di lavoro sono utili per la condivisione delle impostazioni specifiche di un progetto in un team.

## <a name="settings-file-locations"></a>Percorsi dei file delle impostazioni

A seconda della piattaforma, il file delle impostazioni utente si trova nei percorsi seguenti:

* **Windows** `%APPDATA%\sqlops\User\settings.json`
* **Mac** `$HOME/Library/Application Support/sqlops/User/settings.json`
* **Linux** `$HOME/.config/sqlops/User/settings.json`

Il file delle impostazioni dell'area di lavoro si trova sotto la cartella `.[!INCLUDE[name-sos](../includes/name-sos-short.md)]` nel progetto.

## <a name="hot-exit"></a>Uscita a caldo

In caso di uscita, SQL Operations Studio memorizza le modifiche non salvate sui file per impostazione predefinita. Si tratta della stessa funzionalità presente in Visual Studio Code.

Per impostazione predefinita, uscita frequente è disattivata. Abilitare l'area uscita modificando il `files.hotExit` impostazione. Per informazioni dettagliate, vedere [Exit a caldo (nella documentazione di Visual Studio Code)](https://code.visualstudio.com/docs/editor/codebasics#_hot-exit).


## <a name="tab-color"></a>Colore della scheda

Per semplificare l'identificazione delle connessioni utilizzate, le schede aperte nell'editor possono essere impostate con un proprio colore in modo che esso corrisponda a quello definito nel gruppo di Server a cui appartiene la connessione. Per impostazione predefinita, i colori delle schede sono disattivati. Abilitare i colori delle schede modificando l'impostazione `sql.tabColorMode`.

## <a name="additional-resources"></a>Risorse aggiuntive

Poiché [!INCLUDE[name-sos](../includes/name-sos-short.md)] eredita le impostazioni utente e dell'area di lavoro da Visual Studio Code, informazioni dettagliate sono incluse nell'articolo sulle [impostazioni per Visual Studio Code](https://code.visualstudio.com/docs/getstarted/settings).
