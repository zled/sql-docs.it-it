---
title: Le impostazioni utente e dell'area di lavoro in SQL Operations Studio (anteprima) | Microsoft Docs
description: Come modificare le impostazioni utente e dell'area di lavoro in SQL Operations Studio (anteprima).
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: article
author: yualan
ms.author: alayu
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bbabb96b46a7054ed22daf034413df05c903e553
ms.sourcegitcommit: 31df356f89c4cd91ba90dac609a7eb50b13836de
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2018
---
# <a name="user-and-workspace-settings"></a>Impostazioni utente e dell'area di lavoro

È facile configurare [!INCLUDE[name-sos](../includes/name-sos-short.md)] in base alle proprie esigenze tramite le impostazioni. Quasi tutte le parti dell'editor di [!INCLUDE[name-sos](../includes/name-sos-short.md)], l'interfaccia utente e i comportamenti funzionali sono modificabili tramite apposite opzioni.

[!INCLUDE[name-sos](../includes/name-sos-short.md)] fornisce due ambiti diversi per le impostazioni:

* **Utente**: queste impostazioni si applicano globalmente a qualsiasi istanza di [!INCLUDE[name-sos](../includes/name-sos-short.md)].
* **Area di lavoro**: sono impostazioni specifiche di una cartella nel computer e sono disponibili solo quando la cartella è aperta in Esplora risorse dalla barra laterale. Le impostazioni definite in questo ambito ridefiniscono quelle di ambito utente.

## <a name="creating-user-and-workspace-settings"></a>Creazione di impostazioni utente e dell'area di lavoro

Il comando **File**>**Preferenze**>**Impostazioni** (**sqlops**>**Preferenze**>**Impostazioni** su Mac) fornisce il punto di ingresso per configurare le impostazioni utente e dell'area di lavoro. Esse vengono fornite con un elenco di impostazioni predefinite. Copiare qualsiasi impostazione si desideri modificare nell'appropriato file `settings.json`. Le schede a destra consentono di passare rapidamente tra i file delle impostazioni utente e dell'area di lavoro.

È inoltre possibile aprire le impostazioni utente e dell'area di lavoro dal **Riquadro comandi** (**Ctrl+MAIUSC+P**) con **Preferenze: Apri impostazioni utente** e **Preferenze: Apri impostazioni area di lavoro** o utilizzare il tasto di scelta rapida (**Ctrl+,**).

Nell'esempio seguente vengono disabilitati i numeri di riga nell'editor e viene abilitata la funzionalità di *indentazione automatica* del codice al cambio del testo.

![Impostazioni di esempio](media/settings/sample-settings.png)

Le modifiche alle impostazioni vengono ricaricate da [!INCLUDE[name-sos](../includes/name-sos-short.md)] dopo aver modificato e salvato il file `settings.json`.

>**Nota:** le impostazioni dell'area di lavoro sono utili per la condivisione delle impostazioni specifiche di un progetto in un team.

## <a name="settings-file-locations"></a>Percorsi dei file delle impostazioni

A seconda della piattaforma, il file delle impostazioni utente si trova nei percorsi seguenti:

* **Windows** `%APPDATA%\sqlops\User\settings.json`
* **Mac** `$HOME/Library/Application Support/sqlops/User/settings.json`
* **Linux** `$HOME/.config/sqlops/User/settings.json`

Il file delle impostazioni dell'area di lavoro si trova sotto la cartella `.sqlops` nel progetto.

## <a name="hot-exit"></a>Uscita a caldo

In caso di uscita, SQL Operations Studio memorizza le modifiche non salvate sui file per impostazione predefinita. Si tratta della stessa funzionalità presente in Visual Studio Code.

Per gestire tale comportamento, modificare l'opzione `files.hotExit`. Per informazioni dettagliate, vedere [Uscita a caldo (nella documentazione di Visual Studio Code)](https://code.visualstudio.com/docs/editor/codebasics#_hot-exit).


## <a name="tab-color"></a>Colore della scheda

Per semplificare l'identificazione delle connessioni utilizzate, le schede aperte nell'editor possono essere impostate con un proprio colore in modo che esso corrisponda a quello definito nel gruppo di Server a cui appartiene la connessione. Per impostazione predefinita, i colori delle schede sono disattivati. Abilitare i colori delle schede modificando l'impostazione `sql.tabColorMode`.

## <a name="additional-resources"></a>Risorse aggiuntive

Poiché [!INCLUDE[name-sos](../includes/name-sos-short.md)] eredita le impostazioni utente e dell'area di lavoro da Visual Studio Code, informazioni dettagliate sono incluse nell'articolo sulle [impostazioni per Visual Studio Code](https://code.visualstudio.com/docs/getstarted/settings).
