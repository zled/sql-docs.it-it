---
title: Aggiungere un'istanza di SSIS Scale Out Worker con Scale Out Manager | Microsoft Docs
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ef11448d03bd188aaea425225312af9f681f530c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="add-a-scale-out-worker-with-scale-out-manager"></a>Aggiungere un'istanza di Scale Out Worker con Scale Out Manager

Integration Services Scale Out Manager semplifica in modo significativo la complessità di aggiungere Scale Out Worker al proprio ambiente Scale Out esistente. 

I passaggi seguenti consentono di aggiungere un'istanza di Scale Out Worker alla propria topologia Scale Out:

## <a name="1-install-scale-out-worker"></a>1. Installare Scale Out Worker
Nell'installazione guidata di SQL Server selezionare Integration Services e Scale Out Worker nella pagina **Selezione funzionalità**. 
![Selezione della funzionalità Ruolo di lavoro](media/feature-select-worker.PNG)

Nella pagina **Configurazione di Integration Services Scale Out - Nodo di lavoro** è possibile semplicemente fare clic su "Avanti" per ignorare la configurazione esistente e usare **Scale Out Manager** per eseguire la configurazione dopo l'installazione.

Terminare l'installazione guidata.

## <a name="2-open-firewall-on-scale-out-master-computer"></a>2. Aprire il firewall nel computer Scale Out Master
Aprire la porta specificata durante l'installazione di Scale Out Master (8391 per impostazione predefinita) e la porta di SQL Server (1433 per impostazione predefinita) usando Windows Firewall nel computer Scale Out Master.

## <a name="3-add-scale-out-worker-with-scale-out-manager"></a>3. Aggiungere Scale Out Worker con Scale Out Manager
Eseguire SQL Server Management Studio come amministratore e connettersi all'istanza di SQL Server di Scale Out Master.

Fare clic con il pulsante destro del mouse su **SSISDB** in Esplora oggetti e selezionare **Gestisci Scale Out**. 

![Gestisci Scale Out](media/manage-scale-out.PNG)

Nella finestra popup di **Scale Out Manager** passare a **Strumento di gestione dei ruoli di lavoro**. Fare clic sul pulsante "+" e seguire le istruzioni nella finestra di dialogo di connessione dei ruoli di lavoro. Per informazioni dettagliate, vedere [Scale Out Manager](integration-services-ssis-scale-out-manager.md).
