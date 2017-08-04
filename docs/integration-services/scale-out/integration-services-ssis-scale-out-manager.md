---
title: "SQL Server Integration Services con scalabilità Manager | Documenti Microsoft"
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
ms.openlocfilehash: 96748296acd1b2f5ba98558335fece9637eadb87
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="integration-services-scale-out-manager"></a>Servizi di integrazione scalabilità Manager

Scala Out Manager è uno strumento di gestione che consente di gestire la topologia completa SSIS scalabile in un'unica posizione. Rimuove il carico di lavoro di gestione su più computer e occupa comandi TSQL. 

Esistono due modi per attivare la gestione di timeout di scala.

## <a name="1-open-scale-out-manager-from-sql-server-management-studio"></a>1. Aprire Gestione di scalabilità da SQL Server Management Studio
Aprire SQL Server Management Studio e connettersi all'istanza di SQL Server di scalabilità Out Master.

Fare doppio clic su **SSISDB** in Esplora oggetti e selezionare **gestire Scale Out...** . 
![Gestire la scalabilità orizzontale](media/manage-scale-out.PNG)

> [!NOTE]
> Si consiglia di eseguire SQL Server Management Studio come amministratore di alcune delle operazioni di gestione orizzontale, ad esempio "aggiunta di una scalabilità lavoratore" richiede privilegi amministrativi.


## <a name="2-open-scale-out-manager-by-runing-ismanagerexe-directly"></a>2. Aprire direttamente scala Out Manager in esecuzione ISManager.exe

ISManager.exe individua in %systemdrive%\Programmi\Microsoft file (x86) \Microsoft SQL Server\140\DTS\Binn\Management. Fare clic destro **ISManager.exe** e selezionare "Esegui come amministratore". 

Dopo che viene aperta, è necessario immettere il nome di Sql Server di scalabilità Out Master e connettersi ad esso prima di gestire le Scale Out.

![Connessione nel portale](media/portal-connect.PNG)

Scala Out Manager offre varie funzionalità, come indicato di seguito. 

## <a name="enable-scale-out"></a>Abilitare la scalabilità orizzontale
Dopo la connessione a SQL Server, se orizzontale non è abilitato, è possibile fare clic sul pulsante "Abilita" per abilitarlo.

![Attiva portale con scalabilità](media/portal-enable-scale-out.PNG) 
## <a name="view-scale-out-master-status"></a>Visualizzare lo stato di scala Out Master
Verrà visualizzato lo stato del database Master Out di scala sul **Dashboard** pagina.

![Dashboard del portale](media/portal-dashboard.PNG)
## <a name="view-scale-out-worker-status"></a>Visualizzare lo stato del lavoro Out di scala
Verrà visualizzato lo stato del processo di lavoro Out di scala sul **responsabile** pagina. È possibile fare clic su ogni thread di lavoro per visualizzare lo stato.

![Portale di gestione di lavoro](media/portal-worker-manager.PNG)

## <a name="add-scale-out-worker"></a>Aggiungere scalabilità lavoro
Per aggiungere una scala il lavoro, fare clic sul pulsante "+" nella parte inferiore dell'elenco di scala il lavoro. 

Immettere il nome del computer di scala il lavoro che si desidera aggiungere e fare clic su "Convalida". La scala Out gestione controllerà se l'utente corrente disponga di accesso per gli archivi di certificati nei computer del scala Out Master e scala il lavoro.

![La connessione di lavoro](media/connect-worker.PNG)

Se la convalida viene eseguita, scala Out Manager tenterà di leggere il file di configurazione del lavoro e ottenere l'identificazione personale del thread di lavoro. Per ulteriori informazioni, vedere [scala Out lavoro](integration-services-ssis-scale-out-worker.md). Se non è in grado di leggere il thread di lavoro del file di configurazione, sono disponibili due metodi alternativi di fornire il certificato di lavoro. 

È possibile immettere l'identificazione personale del certificato di lavoro direttamente 

![Certificato di lavoro 1](media/portal-cert1.PNG)

oppure fornire il file del certificato. 

![Certificato di lavoro 2](media/portal-cert2.PNG)

Dopo aver raccolto tutte le informazioni, scala Out Manager forniscono le azioni da eseguire. Tyically, include installazione del certificato, l'aggiornamento file di configurazione di lavoro e riavviare il servizio di lavoro. 

![Portale aggiungere confermare 1](media/portal-add-confirm1.PNG)

Nel caso in cui il certificato di lavoro non è accessibile, è necessario aggiornarlo manualmente per se stessi e riavviare il servizio di lavoro.

![Portale aggiungere confermare 2](media/portal-add-confirm2.PNG)

Selezionare la casella di controllo di conferma e iniziare ad aggiungere scala il lavoro.

## <a name="delete-scale-out-worker"></a>Eliminare la scalabilità orizzontale di lavoro
Per eliminare una scala il lavoro, selezionare la scala il lavoro e scegliere il "-" nella parte inferiore dell'elenco di scala il lavoro.


## <a name="enabledisable-scale-out"></a>Abilitare o disabilitare la scalabilità orizzontale
Per abilitare o disabilitare una scala il lavoro, selezionare la scala il lavoro e fare clic sul "Consentono di lavoro" o "Disabilita di lavoro". Lo stato di lavoro in scala Out Manager cambierà di conseguenza se il thread di lavoro non è in linea.

## <a name="edit-scale-out-worker-description"></a>Modificare la descrizione scala Out lavoro
Per modificare la descrizione di una scala il lavoro, selezionare la scala il lavoro e fare clic sul pulsante "Modifica". Al termine della modifica, fare clic sul pulsante "Salva".

![Portale di salvataggio lavoro](media/portal-save-worker.PNG)


