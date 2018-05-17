---
title: Controllo del codice sorgente in SQL Operations Studio (anteprima) | Microsoft Docs
description: Informazioni su come configurare il controllo del codice sorgente in SQL Operations Studio (anteprima).
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 58475a1c7bfb27f29c1e040de286c82d9c7a204f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
#  <a name="using-source-control-in-includename-sosincludesname-sos-shortmd"></a>Utilizzo del controllo del codice sorgente in [!INCLUDE[name-sos](../includes/name-sos-short.md)]

[!INCLUDE[name-sos](../includes/name-sos-short.md)] supporta Git per il controllo della versione/sorgente.


## <a name="git-support-in-includename-sosincludesname-sos-shortmd"></a>Supporto di GIT in [!INCLUDE[name-sos](../includes/name-sos-short.md)]

[!INCLUDE[name-sos](../includes/name-sos-short.md)] viene fornito con la gestione di controllo un origine Git (SCM), ma è comunque necessario [installare Git (versione 2.0.0 o versione successiva)](https://git-scm.com/download) prima di queste funzionalità sono disponibili. 



## <a name="open-an-existing-git-repository"></a>Aprire un repository Git esistente

1. Nel menu **File** selezionare **Apri cartella...**
2. Passare alla cartella contenente i file tracciati da Git e fare clic su **Seleziona cartella**. È possibile selezionare anche le sottocartelle del repository locale.


## <a name="initialize-a-new-git-repository"></a>Inizializzare un nuovo repository Git

1. Selezionare **Controllo del codice sorgente** nella barra laterale sinistra, quindi selezionare l'icona di Git.


   ![Icona Git del controllo del codice sorgente](media/source-control/source-control.png)

1. Immettere il percorso della cartella in cui si desidera inizializzare un repository Git e premere **Invio**.

   ![inizializzare il repository Git](media/source-control/initialize-git-repository.png)

## <a name="working-with-git-repositories"></a>Utilizzo di un repository Git

[!INCLUDE[name-sos](../includes/name-sos-short.md)] eredita l'implementazione di Git da Visual Studio Code, ma attualmente non supporta altri provider di Gestione controllo servizi. Per i dettagli sull'uso di Git dopo avere aperto o inizializzare un repository, vedere [supporto Git in Visual Studio Code](https://code.visualstudio.com/docs/editor/versioncontrol#_git-support).


## <a name="additional-resources"></a>Risorse aggiuntive
- [Documentazione di Git](https://git-scm.com/documentation)
