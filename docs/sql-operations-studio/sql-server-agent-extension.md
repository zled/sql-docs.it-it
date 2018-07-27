---
title: SQL Operations Studio (anteprima), estensione di SQL Server Agent | Microsoft Docs
description: Estensione di SQL Server Agent per SQL Operations Studio (anteprima)
ms.custom: tools|sos
ms.date: 07/19/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: 0da107a9f5dab0a9eb468bc3570788cff816b24a
ms.sourcegitcommit: 4b21840f20195d70f255465666f7b409ba839d18
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/19/2018
ms.locfileid: "39147021"
---
# <a name="sql-server-agent-extension"></a>Estensione di SQL Server Agent

L'estensione di SQL Server Agent è un'estensione per la gestione e risoluzione dei problemi di configurazione e i processi di SQL Agent. Questa estensione è attualmente in anteprima.

Azioni principali includono:
- Processi di elenco SQL Server Agent configurati in un Server SQL
- Visualizza cronologia processi con i risultati dell'esecuzione processo
- Controllo processo base per avviare e arrestare i processi

## <a name="install-the-sql-server-agent-extension"></a>Installare l'estensione di SQL Server Agent

1. Per aprire la gestione delle estensioni e accedere alle estensioni disponibili, selezionare l'icona delle estensioni o scegliere **Estensioni** dal menu **Visualizza**.
2. Selezionare un'estensione disponibile per visualizzare i dettagli.

   ![Installare l'agente](media/extensions/sql-server-agent-extension/install-sql-agent.png)

1. Selezionare l'estensione desiderata e scegliere **Installa**.
2. Selezionare **Ricarica** per abilitare l'estensione (richiesto solo la prima volta in cui l'estensione viene installata).
1. Passare al dashboard di gestione facendo clic con il tasto destro del mouse sul server o sul database e selezionando **Gestisci**.
2. Le estensioni installate vengono visualizzate come schede nel dashboard di gestione:

   ![Agente di visualizzazione](media/extensions/sql-server-agent-extension/view-sql-agent.png)

## <a name="view-jobs"></a>Visualizza processi

Quando ci si connette all'estensione di SQL Server Agent, il primo oggetto visualizzato è un elenco di tutti i processi dell'agente.

   ![Visualizza processi](media/extensions/sql-server-agent-extension/job-view.png)

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su SQL Server Agent, [controllare la documentazione.](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent?view=sql-server-2017)


