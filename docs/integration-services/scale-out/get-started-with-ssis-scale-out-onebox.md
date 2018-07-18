---
title: Introduzione a SSIS Scale Out in un singolo computer | Microsoft Docs
description: Questo articolo spiega tutto ciò che occorre per iniziare a usare SSIS Scale Out in un singolo computer
ms.custom: performance
ms.date: 12/13/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: douglasl
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: craigg
ms.openlocfilehash: 8152a96d894304e46c7a1d46824a75e6cd69b9d1
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2018
ms.locfileid: "35403333"
---
# <a name="get-started-with-integration-services-ssis-scale-out-on-a-single-computer"></a>Introduzione a Integration Services Scale Out (SSIS) in un singolo computer
Questa sezione contiene le linee guida per configurare Integration Services Scale Out in un ambiente a computer singolo con impostazioni predefinite.

## <a name="1-install-sql-server-features"></a>1. Installare le funzionalità di SQL Server
Nell'installazione guidata di SQL Server selezionare gli elementi seguenti dalla pagina **Selezione caratteristica**:
-   Servizi motore di database
-   Integration Services
    -   Scale Out Master
    -   Scale Out Worker

![Prima metà dell'elenco della pagina Selezione caratteristica](media/feature-select-onebox1.PNG)

![Seconda metà dell'elenco della pagina Selezione caratteristica](media/feature-select-onebox2.PNG)

Nella pagina **Configurazione server** fare clic su **Avanti** per accettare gli account del servizio e i tipi di avvio predefiniti.

Nella pagina **Configurazione del motore di database** selezionare **Modalità mista** e fare clic su **Aggiungi utente corrente**. 

![Configurazione del motore](media/engine-config.PNG)

Nelle pagine **Configurazione di Integration Services Scale Out - Nodo master** e **Configurazione di Integration Services Scale Out - Nodo di lavoro** fare clic su **Avanti** per accettare le impostazioni predefinite per la porta e i certificati.

Concludere l'Installazione guidata di SQL Server.

## <a name="2-install-sql-server-management-studio"></a>2. Installare SQL Server Management Studio

Scaricare e installare [SQL Server Management Studio (SSMS)](../../ssms/download-sql-server-management-studio-ssms.md).

## <a name="3-enable-scale-out"></a>3. Abilitare Scale Out
Aprire SSMS e connettersi all'istanza di QL Server locale.
In Esplora oggetti fare clic con il pulsante destro del mouse su **Cataloghi di Integration Services** e selezionare **Creazione catalogo**.

Nella finestra di dialogo **Creazione catalogo** l'opzione **Abilita questo server come SSIS Scale Out Master** è selezionata per impostazione predefinita.

## <a name="4-enable-a-scale-out-worker"></a>4. Abilitare un'istanza di Scale Out Worker
In SSMS fare clic con il pulsante destro del mouse su **SSISDB** e selezionare **Gestisci Scale Out**. 

![Gestisci Scale Out](media/manage-scale-out.PNG)

Si apre l'app Integration Services Scale Out Manager. Per altre informazioni, vedere [Scale Out Manager](integration-services-ssis-scale-out-manager.md).

Per abilitare un'istanza di Scale Out Worker, passare a **Strumento di gestione dei ruoli di lavoro** e selezionare il ruolo di lavoro da abilitare. Alcuni ruoli di lavoro sono disabilitati per impostazione predefinita. Fare clic su **Abilita ruolo di lavoro** per abilitare il ruolo di lavoro selezionato.

## <a name="5-run-packages-in-scale-out"></a>5. Eseguire pacchetti in modalità di scalabilità orizzontale
A questo punto, è possibile eseguire pacchetti SSIS in Scale Out. Per altre informazioni, vedere [Eseguire pacchetti nel servizio Integration Services (SSIS) Scale Out](run-packages-in-integration-services-ssis-scale-out.md).

## <a name="next-steps"></a>Passaggi successivi
-   [Aggiungere un'istanza di Scale Out Worker con Scale Out Manager](add-scale-out-worker.md).
