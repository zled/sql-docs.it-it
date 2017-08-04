---
title: Iniziare con una scala SSIS Out in un singolo Computer | Documenti Microsoft
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 7175c63be4c0e15e50f2020f75d283ac0e3dfdbf
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="get-started-with-integration-services-ssis-scale-out-on-a-single-computer"></a>Introduzione a Integration Services (SSIS) Scale Out in un singolo computer
Questa sezione vengono fornite le linee guida di configurazione di Integration Services Scale Out in un ambiente di una casella con le impostazioni predefinite.

## <a name="1-install-sql-server-features"></a>1. Installare le funzionalità di SQL Server
Nell'installazione guidata di SQL Server, selezionare servizi motore di Database, Integration Services, scala Out Master e scala il lavoro sul **Selezione funzionalità** pagina.

![Funzionalità selezionare Onebox 1](media/feature-select-onebox1.PNG)

![Funzionalità selezionare Onebox 2](media/feature-select-onebox2.PNG)

Nel **configurazione Server** pagina, fare clic su "Avanti" per l'utilizzo di account di servizio predefiniti e tipi di avvio.

Nel **configurazione motore di Database** pagina, selezionare "**modalità mista**"e fare clic su"**Aggiungi utente corrente**" pulsante. 

![Configurazione del motore](media/engine-config.PNG)

Uno di **scala Out configurazione di Integration Services - nodo Master** e **scala Out configurazione di Integration Services - nodo di lavoro** pagine, è sufficiente fare clic su "Avanti" per applicare le impostazioni predefinite delle porte e dei certificati.

Completare l'installazione guidata di SQL Server.

## <a name="2-install-sql-server-management-studio"></a>2. Installare SQL Server Management Studio

[Scaricare](../../ssms/download-sql-server-management-studio-ssms.md) SQL Server Management Studio e installarlo.

## <a name="3-enable-scale-out"></a>3. Abilitare la scalabilità orizzontale
Aprire SQL Server Management Studio e connettersi all'istanza locale di Sql Server.
Fare doppio clic su **cataloghi di Integration Services** in Esplora oggetti e selezionare **Crea catalogo**.

Nel **Crea catalogo** finestra di dialogo, **abilitare questo server come SSIS scalabilità master** è selezionata per impostazione predefinita. Dopo aver creato il catalogo come di consueto. 

## <a name="4-enable-scale-out-worker"></a>4. Abilitare la scalabilità di lavoro
In SQL Server Management Studio, fare clic sul **SSISDB** e selezionare **gestire Scale Out...** . 
![Gestire la scalabilità orizzontale](media/manage-scale-out.PNG)

Viene visualizzata l'integrazione di Gestione servizi di scala Out. È possibile gestire orizzontale con esso. Per ulteriori informazioni, vedere [scala Out Gestione servizi di integrazione](integration-services-ssis-scale-out-manager.md).

Per attivare la scala il lavoro, passare a **responsabile** e selezionare il processo di lavoro che si desidera abilitare. Il processo di lavoro è inizialmente disabilitato. Fare clic su **abilitare lavoro** per abilitarlo.

## <a name="5-run-packages-in-scale-out"></a>5. Eseguire pacchetti in modalità di scalabilità orizzontale
A questo punto, si è pronti per eseguire pacchetti SSIS in orizzontale. Vedere [eseguire i pacchetti di Integration Services (SSIS) scalabilità](run-packages-in-integration-services-ssis-scale-out.md).


Per aggiungere più Scale Out worker, vedere [aggiungere una scala Out lavoratore con scala Out Manager](add-scale-out-worker.md).
