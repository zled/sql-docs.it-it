---
title: Gruppi di server in SQL Operations Studio (anteprima) | Microsoft Docs
description: Informazioni sui gruppi di server in SQL Operations Studio (anteprima).
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
ms.openlocfilehash: 1eec4684b1a06e5226029a3a2409f831bffff04f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="server-groups-in-includename-sosincludesname-sos-shortmd"></a>Gruppi di server in [!INCLUDE[name-sos](../includes/name-sos-short.md)]

I gruppi di server consentono di organizzare le connessioni ai server e ai database sui quali si lavora. Quando si creano gruppi di server, i dettagli di configurazione vengono salvati nelle *Impostazioni utente*.

## <a name="create-and-edit-server-groups"></a>Creare e modificare gruppi di server

1. Fare clic sull'icona **Nuovo gruppo di server** nella parte alta della barra laterale *SERVER*.
2. Immettere un nome per il gruppo e selezionare un colore. Facoltativamente, aggiungere una descrizione.

   ![Aggiungi gruppo di server](./media/server-groups/add-server-group.png)

Per modificare un gruppo di server esistente, scegliere il gruppo, premere il tasto destro del mouse e selezionare **Modifica gruppo di Server**.

Per modificare i colori disponibili da utilizzare per i gruppi di server, modificare i valori della proprietà *serverGroup.colors* sulle [impostazioni utente](settings.md).

> [!TIP]
> È possibile spostare i server tra i diversi gruppi di server tramite trascinamento.



## <a name="additional-resources"></a>Risorse aggiuntive
- [Area di lavoro e impostazioni utente](settings.md)
