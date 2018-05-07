---
title: Creare e personalizzare i tasti di scelta rapida in SQL Operations Studio (anteprima) | Microsoft Docs
description: Informazioni su come creare e personalizzare i tasti di scelta rapida in SQL Operations Studio (anteprima).
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: article
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a96204723bd56a63ec23841ede47b5844fbad313
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="keyboard-shortcuts-in-includename-sosincludesname-sosmd"></a>Tasti di scelta rapida in [!INCLUDE[name-sos](../includes/name-sos.md)]

In questo articolo viene mostrata la procedura per visualizzare, modificare e creare tasti di scelta rapida in [!INCLUDE[name-sos](../includes/name-sos-short.md)].

Poiché SQL Operations Studio (anteprima) eredita le associazioni dei tasti di Visual Studio Code, le informazioni dettagliate sulle personalizzazioni avanzate, l'utilizzo di diversi layout di tastiera e così via sono disponibili nell'articolo [associazione di tasti di Visual Studio Code](https://code.visualstudio.com/docs/getstarted/keybindings). Alcune funzionalità di associazione tasti potrebbero non essere disponibili (ad esempio, le estensioni di mappatura non sono supportate in [!INCLUDE[name-sos](../includes/name-sos-short.md)]).


## <a name="open-the-keyboard-shortcuts-editor"></a>Aprire l'editor dei tasti di scelta rapida

Per visualizzare tutti i tasti attualmente definiti:

Aprire il l'editor dei **tasti di scelta rapida** dal menu **File**: **File**>**Preferenze**>**Tasti di scelta rapida** (**[!INCLUDE[name-sos](../includes/name-sos-short.md)]**>**Preferenze**>**Tasti di scelta rapida** su Mac).

Oltre a visualizzare i tasti di scelta rapida correnti, l'editor dei **tasti di scelta rapida** elenca i comandi disponibili che non dispongono di tasti di scelta rapida definiti.


## <a name="edit-existing-keyboard-shortcuts"></a>Modificare i tasti di scelta rapida da tastiera

Per modificare l'associazione di un tasto di scelta rapida esistente:

1. Individuare il tasto di scelta rapida che si desidera modificare utilizzando la casella di ricerca o lo scorrimento nell'elenco.
   > [!TIP]
   > Cercare per chiave, per comando, per sorgente e così via per restituire tutti i tasti pertinenti. 

1. Premere il tasto destro del mouse sulla voce desiderata e selezionare **Cambia tasto di scelta rapida**

   ![modificare i tasti di scelta rapida](media/keyboard-shortcuts/change-keybinding.png)

1. Premere la combinazione desiderata, quindi premere **Invio** per salvarla. 

   ![salvare i tasti di scelta rapida](media/keyboard-shortcuts/save-keybinding.png)

## <a name="create-new-keyboard-shortcuts"></a>Creare nuovi tasti di scelta rapida 

Per creare nuovi tasti di scelta rapida: 

1. Premere il tasto destro del mouse su di un comando che non dispone di associazioni e selezionare **Aggiungi tasto di scelta rapida**.

   ![creare tasti di scelta rapida](media/keyboard-shortcuts/add-keybinding.png)

1. Premere la combinazione desiderata, quindi premere **Invio** per salvarla. 


