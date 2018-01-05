---
title: Origine di controllo in Studio operazioni SQL (anteprima) | Documenti Microsoft
description: Informazioni su come configurare controllo del codice sorgente in Studio operazioni SQL (anteprima).
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: 
ms.topic: article
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4f28199262b087ad5362da0ddf56827216aec748
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
#  <a name="using-source-control-in-includename-sosincludesname-sos-shortmd"></a>Utilizzo di controllo del codice sorgente[!INCLUDE[name-sos](../includes/name-sos-short.md)]

[!INCLUDE[name-sos](../includes/name-sos-short.md)]supporta Git per il controllo della versione/origine.


## <a name="git-support-in-includename-sosincludesname-sos-shortmd"></a>Supporto di GIT in[!INCLUDE[name-sos](../includes/name-sos-short.md)]

[!INCLUDE[name-sos](../includes/name-sos-short.md)]viene fornito con un gestore di controllo di origine Git (SCM), ma è comunque necessario [installare Git (versione 2.0.0 o versione successiva)](https://git-scm.com/download) prima di queste funzionalità sono disponibili. 



## <a name="open-an-existing-git-repository"></a>Aprire un repository Git esistente

1. Sotto il **File** dal menu **Apri cartella...**
2. Passare alla cartella che contiene i file rilevati da git e fare clic su **selezionare la cartella**. Le sottocartelle nel repository locale sono integri da selezionare.


## <a name="initialize-a-new-git-repository"></a>Inizializzare un nuovo repository git

1. Selezionare **controllo del codice sorgente**, quindi selezionare l'icona di git.

   ![Icona git del controllo origine](media/source-control/source-control.png)

1. Immettere il percorso della cartella in cui si desidera inizializzare come un repository Git e premere **invio**.

   ![inizializzare il repository Git](media/source-control/initialize-git-repository.png)

## <a name="working-with-git-repositories"></a>Utilizzo di repository Git

[!INCLUDE[name-sos](../includes/name-sos-short.md)]eredita l'implementazione di Git dal codice di Visual Studio, ma attualmente non supporta altri provider di Gestione controllo servizi. Per i dettagli sull'uso di Git dopo avere aperto o inizializzare un repository, vedere [supporto Git in Visual Studio Code](https://code.visualstudio.com/docs/editor/versioncontrol#_git-support).


## <a name="additional-resources"></a>Risorse aggiuntive
- [Documentazione di GIT](https://git-scm.com/documentation)
