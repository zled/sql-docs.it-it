---
title: SQL Server Integration Services Scale Out Manager | Microsoft Docs
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
ms.openlocfilehash: 84fe58d4dc7894728c43cb19d17d3444b5b84820
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="integration-services-scale-out-manager"></a>Integration Services Scale Out Manager

Scala Out Manager è uno strumento che consente di gestire l'intera topologia di SSIS Scale Out in un'unica posizione. In questo modo non sono necessari più computer ed è possibile usare comandi TSQL. 

Scale Out Manager può essere attivato in due modi.

## <a name="1-open-scale-out-manager-from-sql-server-management-studio"></a>1. Aprire Scale Out Manager da SQL Server Management Studio
Aprire SQL Server Management Studio e connettersi all'istanza di SQL Server di Scale Out Master.

Fare clic con il pulsante destro del mouse su **SSISDB** in Esplora oggetti e selezionare **Gestisci Scale Out...**. ![Gestisci Scale Out](media/manage-scale-out.PNG)

> [!NOTE]
> È consigliabile eseguire SQL Server Management Studio come amministratore. Per alcune operazioni di gestione di Scale Out, ad esempio l'aggiunta di un'istanza di Scale Out Worker, sono necessari privilegi amministrativi.


## <a name="2-open-scale-out-manager-by-runing-ismanagerexe-directly"></a>2. Aprire direttamente Scale Out Manager eseguendo il file ISManager.exe

Il file ISManager.exe si trova in %systemdrive%\Programmi (x86)\Microsoft SQL Server\140\DTS\Binn\Gestione. Fare clic con il pulsante destro del mouse su **ISManager.exe** e selezionare "Esegui come amministratore". 

Dopo averlo aperto, immettere il nome SQL Server di Scale Out Master e connettersi prima di gestire Scale Out.

![Connessione nel portale](media/portal-connect.PNG)

Di seguito sono elencate le varie funzionalità di Scale Out Manager. 

## <a name="enable-scale-out"></a>Abilitare Scale Out
Dopo aver eseguito la connessione a SQL Server, fare clic sul pulsante "Abilita" per abilitare Scale Out se non è abilitato.

![Abilitare Scale Out nel portale](media/portal-enable-scale-out.PNG) 
## <a name="view-scale-out-master-status"></a>Visualizzare lo stato di Scale Out Master
Lo stato di Scale Out Master viene visualizzato nella pagina **Dashboard**.

![Dashboard del portale](media/portal-dashboard.PNG)
## <a name="view-scale-out-worker-status"></a>Visualizzare lo stato di Scale Out Worker
Lo stato di Scale Out Worker viene visualizzato nella pagina **Dashboard**. È possibile fare clic su ogni ruolo di lavoro per visualizzare il singolo stato.

![Strumento di gestione dei ruoli di lavoro del portale](media/portal-worker-manager.PNG)

## <a name="add-scale-out-worker"></a>Aggiungere Scale Out Worker
Per aggiungere un'istanza di Scale Out Worker, fare clic sul pulsante "+" nella parte inferiore dell'elenco di Scale Out Worker. 

Immettere il nome del computer dell'istanza di Scale Out Worker che si vuole aggiungere e fare clic su "Convalida". Scale Out Manager controllerà se l'utente corrente ha accesso agli archivi certificati nei computer di Scale Out Master e Scale Out Worker.

![Connessione di un ruolo di lavoro](media/connect-worker.PNG)

Se viene eseguita la convalida, Scale Out Manager tenterà di leggere il file di configurazione del ruolo di lavoro e ottenerne l'identificazione personale certificato. Per altre informazioni, vedere [Integration Services (SSIS) Scale Out Worker](integration-services-ssis-scale-out-worker.md). Se non è possibile leggere il file di configurazione del ruolo di lavoro, esistono due alternative per ottenere il certificato del ruolo di lavoro. 

È possibile immettere direttamente l'identificazione personale certificato del ruolo di lavoro 

![Certificato del ruolo di lavoro 1](media/portal-cert1.PNG)

oppure specificare il file del certificato. 

![Certificato del ruolo di lavoro 2](media/portal-cert2.PNG)

Dopo aver raccolto tutte le informazioni, Scale Out Manager indicherà le operazioni da eseguire, che generalmente includono l'installazione del certificato, l'aggiornamento del file di configurazione del ruolo di lavoro e il riavvio del servizio del ruolo di lavoro. 

![Aggiungere conferma 1 del portale](media/portal-add-confirm1.PNG)

Nel caso in cui il certificato del ruolo di lavoro non sia accessibile, aggiornarlo manualmente e riavviare il servizio del ruolo di lavoro.

![Aggiungere conferma 2 del portale](media/portal-add-confirm2.PNG)

Selezionare la casella di controllo di conferma e iniziare ad aggiungere istanze di Scale Out Worker.

## <a name="delete-scale-out-worker"></a>Eliminare Scale Out Worker
Per eliminare un'istanza di Scale Out Worker, selezionare Scale Out Worker e fare clic sul pulsante "-" nella parte inferiore dell'elenco di Scale Out Worker.


## <a name="enabledisable-scale-out"></a>Abilitare/disabilitare Scale Out
Per abilitare o disabilitare un'istanza di Scale Out Worker, selezionare Scale Out Worker e fare clic sul pulsante "Abilita ruolo di lavoro" e "Disabilita ruolo di lavoro". Lo stato del ruolo di lavoro in Scale Out Manager cambierà a seconda che il ruolo di lavoro sia o meno offline.

## <a name="edit-scale-out-worker-description"></a>Modificare la descrizione di Scale Out Worker
Per modificare la descrizione di un'istanza di Scale Out Worker, selezionare l'istanza e fare clic sul pulsante "Modifica". Al termine della modifica, fare clic sul pulsante "Salva".

![Salvare il ruolo di lavoro nel portale](media/portal-save-worker.PNG)

