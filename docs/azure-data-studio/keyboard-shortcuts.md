---
title: Creare e personalizzare i tasti di scelta rapida in Studio di Azure Data | Microsoft Docs
description: Informazioni su come creare e personalizzare i tasti di scelta rapida in Azure Data Studio.
ms.custom: tools|sos
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3452e2e19d237f8ba5135c723e9971c0932ba61c
ms.sourcegitcommit: 35e4c71bfbf2c330a9688f95de784ce9ca5d7547
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2018
ms.locfileid: "49356472"
---
# <a name="keyboard-shortcuts-in-includename-sosincludesname-sosmd"></a>Tasti di scelta rapida in [!INCLUDE[name-sos](../includes/name-sos.md)]

In questo articolo viene mostrata la procedura per visualizzare, modificare e creare tasti di scelta rapida in [!INCLUDE[name-sos](../includes/name-sos-short.md)].

Poiché [!INCLUDE[name-sos](../includes/name-sos-short.md)] eredita le associazioni dei tasti di Visual Studio Code, le informazioni dettagliate sulle personalizzazioni avanzate, l'utilizzo di diversi layout di tastiera e così via sono disponibili nell'articolo [associazione di tasti di Visual Studio Code](https://code.visualstudio.com/docs/getstarted/keybindings). Alcune funzionalità di associazione tasti potrebbero non essere disponibili (ad esempio, le estensioni di mappatura non sono supportate in [!INCLUDE[name-sos](../includes/name-sos-short.md)]).


## <a name="open-the-keyboard-shortcuts-editor"></a>Aprire l'editor dei tasti di scelta rapida

Per visualizzare tutti i tasti di scelta rapida attualmente definiti:

Aprire il l'editor dei **tasti di scelta rapida** dal menu **File**: **File** > **Preferenze** > **Tasti di scelta rapida** (**[!INCLUDE[name-sos](../includes/name-sos-short.md)]** > **Preferenze** > **Tasti di scelta rapida** su Mac).

Oltre a visualizzare i tasti di scelta rapida correnti, l'editor dei **tasti di scelta rapida** elenca i comandi disponibili che non dispongono di tasti di scelta rapida definiti. L'editor dei **Tasti di scelta rapida** consente di modificare, rimuovere, reimpostare e definire facilmente nuovi tasti di scelta rapida.  


## <a name="edit-existing-keyboard-shortcuts"></a>Modifica tasti di scelta rapida esistenti

Per modificare l'associazione di un tasto di scelta rapida esistente:

1. Individuare il tasto di scelta rapida che si desidera modificare usando la casella di ricerca o scorrere l'elenco.
   > [!TIP]
   > Cercare per chiave, per comando, per sorgente e così via per restituire tutti i tasti pertinenti.

1. Premere il tasto destro del mouse sulla voce desiderata e selezionare **Cambia tasto di scelta rapida**

   ![Modifica tasto di scelta rapida](media/keyboard-shortcuts/change-keybinding.png)

1. Premere la combinazione desiderata, quindi premere **Invio** per salvarla. 

   ![salvare i tasti di scelta rapida](media/keyboard-shortcuts/save-keybinding.png)

## <a name="create-new-keyboard-shortcuts"></a>Creare nuovi tasti di scelta rapida

Per creare nuovi tasti di scelta rapida:

1. Premere il tasto destro del mouse su di un comando che non dispone di associazioni e selezionare **Aggiungi tasto di scelta rapida**.

   ![creare tasti di scelta rapida](media/keyboard-shortcuts/add-keybinding.png)

1. Premere la combinazione desiderata, quindi premere **Invio** per salvarla.


