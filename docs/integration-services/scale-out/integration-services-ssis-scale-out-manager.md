---
title: SQL Server Integration Services Scale Out Manager | Microsoft Docs
ms.description: This article describes the Scale Out Manager tool which you can use to manager SSIS Scale Out
ms.custom: ''
ms.date: 12/19/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: scale-out
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: craigg
ms.openlocfilehash: 4f5ea5696c99a10b2e9b64a92c91c38e117430cd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="integration-services-scale-out-manager"></a>Integration Services Scale Out Manager

Scale Out Manager è uno strumento che consente di gestire l'intera topologia di SSIS Scale Out da un'unica app. In tal modo riduce il carico di lavoro rappresentato dalle attività di gestione e dall'esecuzione di comandi Transact-SQL in più computer.

## <a name="open-scale-out-manager"></a>Aprire Scale Out Manager

È possibile aprire Scale Out Manager in due modi.

### <a name="1-open-scale-out-manager-from-sql-server-management-studio"></a>1. Aprire Scale Out Manager da SQL Server Management Studio
Aprire SQL Server Management Studio (SSMS) e connettersi all'istanza SQL Server di Scale Out Master.

In Esplora oggetti di SQL Server fare clic con il pulsante destro del mouse su **SSISDB** e selezionare **Gestisci Scale Out**.

![Gestisci Scale Out](media/manage-scale-out.PNG)

> [!NOTE]
> È consigliabile eseguire SQL Server Management Studio come amministratore, poiché alcune operazioni di gestione di Scale Out, quali l'aggiunta di un'istanza Scale Out Worker, richiedono privilegi amministrativi.

### <a name="2-open-scale-out-manager-by-running-ismanagerexe"></a>2. Aprire Scale Out Manager eseguendo il file ISManager.exe

Trovare `ISManager.exe` in `%SystemDrive%\Program Files (x86)\Microsoft SQL Server\140\DTS\Binn\Management`. Fare clic con il pulsante destro del mouse su **ISManager.exe** e selezionare **Esegui come amministratore**. 

Dopo l'apertura di Scale Out Manager, immettere il nome istanza SQL Server di Scale Out Master e connettersi a tale istanza per gestire l'ambiente Scale Out.

![Connessione nel portale](media/portal-connect.PNG)

## <a name="tasks-available-in-scale-out-manager"></a>Attività disponibili in Scale Out Manager
In Scale Out Manager è possibile eseguire le operazioni seguenti:

### <a name="enable-scale-out"></a>Abilitare Scale Out
Dopo aver eseguito la connessione a SQL Server, selezionare **Abilita** per abilitare Scale Out se non è abilitato.

![Abilitare Scale Out nel portale](media/portal-enable-scale-out.PNG) 

### <a name="view-scale-out-master-status"></a>Visualizzare lo stato di Scale Out Master
Lo stato di Scale Out Master viene visualizzato nella pagina **Dashboard**.

![Dashboard del portale](media/portal-dashboard.PNG)

### <a name="view-scale-out-worker-status"></a>Visualizzare lo stato di Scale Out Worker
Lo stato di Scale Out Worker viene visualizzato nella pagina **Dashboard**. È possibile selezionare ogni istanza Scale Out Worker per visualizzarne lo stato.

![Strumento di gestione dei ruoli di lavoro del portale](media/portal-worker-manager.PNG)

### <a name="add-a-scale-out-worker"></a>Aggiungere un'istanza Scale Out Worker
Per aggiungere un'istanza di Scale Out Worker, fare clic sul pulsante **+** nella parte inferiore dell'elenco Scale Out Worker. 

Immettere il nome computer dell'istanza di Scale Out Worker che si vuole aggiungere e fare clic su **Convalida**. Scale Out Manager verifica se l'utente corrente dispone di accesso agli archivi certificati nei computer che eseguono Scale Out Master e Scale Out Worker

![Connessione di un ruolo di lavoro](media/connect-worker.PNG)

Se la convalida ha esito positivo, Scale Out Manager prova a leggere il file di configurazione del servizio worker e ad ottenere l'identificazione personale del certificato corrispondente. Per altre informazioni, vedere [Scale Out Worker](integration-services-ssis-scale-out-worker.md). Se Scale Out Manager non è in grado di leggere il file di configurazione del servizio worker, esistono due metodi alternativi per ottenere il certificato del worker. 

1.  È possibile immettere direttamente l'identificazione personale del certificato worker.

    ![Certificato del ruolo di lavoro 1](media/portal-cert1.PNG)

2.  In alternativa è possibile rendere disponibile il file del certificato. 

    ![Certificato del ruolo di lavoro 2](media/portal-cert2.PNG)

Dopo aver raccolto le informazioni necessarie, Scale Out Manager indica le operazioni da eseguire. In genere queste operazioni includono l'installazione del certificato, l'aggiornamento del file di configurazione del servizio worker e il riavvio del servizio worker.

![Aggiungere conferma 1 del portale](media/portal-add-confirm1.PNG)

Se il certificato worker non è accessibile, aggiornarlo manualmente e riavviare il servizio worker.

![Aggiungere conferma 2 del portale](media/portal-add-confirm2.PNG)

Selezionare la casella di controllo **Conferma** e quindi selezionare **OK** per iniziare ad aggiungere un componente Scale Out Worker.

### <a name="delete-a-scale-out-worker"></a>Eliminare un componente Scale Out Worker
Per eliminare un componente Scale Out Worker, selezionarlo e quindi selezionare **-** nella parte inferiore dell'elenco Scale Out Worker.

### <a name="enable-or-disable-a-scale-out-worker"></a>Abilitare o disabilitare un componente Scale Out Worker
Per abilitare o disabilitare un componente Scale Out Worker, selezionarlo e quindi selezionare **Abilita ruolo di lavoro** o **Disabilita ruolo di lavoro**. Se il servizio worker non è offline, lo stato del servizio visualizzato in Scale Out Manager viene modificato di conseguenza.

## <a name="edit-a-scale-out-worker-description"></a>Modificare la descrizione di un componente Scale Out Worker
Per modificare la descrizione di un componente Scale Out Worker, selezionarlo e quindi selezionare **Modifica**. Dopo aver completato la modifica della descrizione, selezionare **Salva**.

![Salvare il ruolo di lavoro nel portale](media/portal-save-worker.PNG)

## <a name="next-steps"></a>Passaggi successivi
Per altre informazioni, vedere gli articoli seguenti:
-   [Integration Services (SSIS) Scale Out Master](integration-services-ssis-scale-out-master.md)
-   [Integration Services (SSIS) Scale Out Worker](integration-services-ssis-scale-out-worker.md)