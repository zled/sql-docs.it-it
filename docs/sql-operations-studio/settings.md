---
title: Studio operazioni SQL (anteprima) utente e le impostazioni dell'area di lavoro | Documenti Microsoft
description: Come modificare Studio operazioni SQL (anteprima) utente e le impostazioni dell'area di lavoro.
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

È facile da configurare [!INCLUDE[name-sos](../includes/name-sos-short.md)] alle proprie esigenze tramite le impostazioni. Quasi tutte le parti di [!INCLUDE[name-sos](../includes/name-sos-short.md)]dell'editor, interfaccia utente e un comportamento funzionale sono disponibili opzioni è possibile modificare.

[!INCLUDE[name-sos](../includes/name-sos-short.md)] fornisce due ambiti diversi per le impostazioni:

* **Utente** queste impostazioni si applicano globalmente a qualsiasi istanza di [!INCLUDE[name-sos](../includes/name-sos-short.md)] si apre.
* **Area di lavoro** le impostazioni dell'area sono impostazioni specifiche per una cartella nel computer in uso e sono disponibili solo quando la cartella è aperta nella barra laterale di Explorer. Le impostazioni definite in questo ambito di eseguire l'override l'ambito dell'utente.

## <a name="creating-user-and-workspace-settings"></a>Creazione di utenti e le impostazioni dell'area di lavoro

Il comando di menu **File** > **preferenze** > **impostazioni** (**codice**  >  **Preferenze** > **impostazioni** su Mac) fornisce il punto di ingresso per configurare le impostazioni utente e dell'area di lavoro. Vengono fornite con un elenco di impostazioni predefinite. Copia di qualsiasi impostazione che si desidera modificare appropriati `settings.json` file. Le schede a destra consentono di passare rapidamente tra i file delle impostazioni utente e dell'area di lavoro.

È inoltre possibile aprire le impostazioni utente e dell'area di lavoro dal **comando tavolozza** (**Ctrl + MAIUSC + P**) con **preferenze: aprire le impostazioni utente** e  **Preferenze: Aprire le impostazioni dell'area** o utilizzare il tasto di scelta rapida (**Ctrl +**).

Nell'esempio seguente disabilita i numeri di riga nell'editor e configura le righe di codice per essere rientrate automaticamente.

![Impostazioni di esempio](media/settings/sample-settings.png)

Le modifiche alle impostazioni vengono ricaricate da [!INCLUDE[name-sos](../includes/name-sos-short.md)] dopo aver modificato `settings.json` viene salvato.

>**Nota:** dell'area di lavoro impostazioni sono utili per la condivisione delle impostazioni specifiche di un progetto in un team.

## <a name="settings-file-locations"></a>Percorsi dei File di impostazioni

A seconda della piattaforma, il file di impostazioni utente si trova qui:

* **Windows** `%APPDATA%\sqlops\User\settings.json`
* **Mac** `$HOME/Library/Application Support/sqlops/User/settings.json`
* **Linux** `$HOME/.config/sqlops/User/settings.json`

Il file di impostazione dell'area di lavoro si trova sotto il `.[!INCLUDE[name-sos](../includes/name-sos-short.md)]` cartella nel progetto.

## <a name="hot-exit"></a>Uscita a caldo

Operazioni SQL Studio verranno memorizzate le modifiche non salvate per i file quando si esce per impostazione predefinita. Questo è lo stesso come la funzionalità di uscita di frequente in Visual Studio Code.

Per impostazione predefinita, uscita frequente è disattivata. Abilitare l'area uscita modificando il `files.hotExit` impostazione. Per informazioni dettagliate, vedere [Exit a caldo (nella documentazione di Visual Studio Code)](https://code.visualstudio.com/docs/editor/codebasics#_hot-exit).


## <a name="tab-color"></a>Colore della scheda

Per semplificare l'identificazione le connessioni che si sta utilizzando, le schede aperte nell'editor possono avere i loro colori impostati in modo che corrisponda il colore del gruppo di Server a cui appartiene la connessione. Per impostazione predefinita, i colori delle schede sono disattivati per impostazione predefinita. Abilitare i colori delle schede modificando il `sql.tabColorMode` impostazione.

## <a name="additional-resources"></a>Risorse aggiuntive

Poiché [!INCLUDE[name-sos](../includes/name-sos-short.md)] eredita le impostazioni utente e dell'area di lavoro funzionalità dal codice di Visual Studio, informazioni dettagliate sulle impostazioni sono incluse nel [impostazioni per il codice di Visual Studio](https://code.visualstudio.com/docs/getstarted/settings) articolo.
