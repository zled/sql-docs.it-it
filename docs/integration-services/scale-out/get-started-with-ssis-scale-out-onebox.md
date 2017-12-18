---
title: Introduzione a SSIS Scale Out in un singolo computer | Microsoft Docs
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
ms.openlocfilehash: 8514cd548b003a39bf198b83b6b80d775a55384b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="get-started-with-integration-services-ssis-scale-out-on-a-single-computer"></a>Introduzione a Integration Services Scale Out (SSIS) in un singolo computer
Questa sezione contiene le linee guida per configurare Integration Services Scale Out in un singolo ambiente con impostazioni predefinite.

## <a name="1-install-sql-server-features"></a>1. Installare le funzionalità di SQL Server
Nell'installazione guidata di SQL Server selezionare Servizi motore di database, Integration Services, Scale Out Master e Scale Out Worker nella pagina **Selezione funzionalità**.

![Selezione funzionalità computer 1](media/feature-select-onebox1.PNG)

![Selezione funzionalità computer 2](media/feature-select-onebox2.PNG)

Nella pagina **Configurazione server** fare semplicemente clic su "Avanti" per usare gli account del servizio predefiniti e i tipi di avvio.

Nella pagina **Configurazione del motore di database** selezionare "**Modalità mista**"e fare clic sul pulsante "**Aggiungi utente corrente**". 

![Configurazione del motore](media/engine-config.PNG)

Nelle pagine **Configurazione di Integration Services Scale Out - Nodo master** e **Configurazione di Integration Services Scale Out - Nodo di lavoro** fare semplicemente clic su "Avanti" per applicare le impostazioni predefinite della porta e dei certificati.

Concludere l'Installazione guidata di SQL Server.

## <a name="2-install-sql-server-management-studio"></a>2. Installare SQL Server Management Studio

[Scaricare](../../ssms/download-sql-server-management-studio-ssms.md) SQL Server Management Studio e installarlo.

## <a name="3-enable-scale-out"></a>3. Abilitare Scale Out
Aprire SSMS e connettersi all'istanza di QL Server locale.
In Esplora oggetti fare clic con il pulsante destro del mouse su **Cataloghi di Integration Services** e selezionare **Creazione catalogo**.

Nella finestra di dialogo **Creazione catalogo** l'opzione **Abilita questo server come SSIS Scale Out Master** è selezionata per impostazione predefinita. Creazione comune del catalogo. 

## <a name="4-enable-scale-out-worker"></a>4. Abilitare Scale Out Worker
In SSMS fare clic con il pulsante destro del mouse su **SSISDB** e selezionare **Gestisci Scale Out...** . ![Gestisci Scale Out](media/manage-scale-out.PNG)

Si aprirà Integration Services Scale Out Manager, che consente di gestire Scale Out. Per altre informazioni, vedere [Integration Services Scale Out Manager](integration-services-ssis-scale-out-manager.md).

Per abilitare l'istanza di Scale Out Worker, passare a **Strumento di gestione dei ruoli di lavoro** e selezionare il ruolo di lavoro da abilitare. Il ruolo di lavoro è inizialmente disabilitato. Fare clic su **Abilita ruolo di lavoro** per abilitarlo.

## <a name="5-run-packages-in-scale-out"></a>5. Eseguire pacchetti in modalità di scalabilità orizzontale
A questo punto, è possibile eseguire pacchetti SSIS in Scale Out. Vedere [Eseguire i pacchetti in Integration Services (SSIS) Scale Out](run-packages-in-integration-services-ssis-scale-out.md).


Per aggiungere più istanze di Scale Out Worker, vedere [Aggiungere un'istanza di Scale Out Worker con Scale Out Manager ](add-scale-out-worker.md).
