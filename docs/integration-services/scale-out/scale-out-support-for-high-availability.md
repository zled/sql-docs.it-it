---
title: "SQL Server Integration Services (SSIS) supporto per la disponibilità elevata con scalabilità | Documenti Microsoft"
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
ms.openlocfilehash: 2405235bcfa09d2cc49e007f4eae6975d9ebf7a5
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="scale-out-support-for-high-availability"></a>Scala il supporto per la disponibilità elevata

In SSIS scalabile, lavoro lato la disponibilità elevata è fornita tramite l'esecuzione di pacchetti con più Scale Out worker.
Disponibilità elevata lato master viene ottenuta con [Always On per il catalogo SSIS](../service/ssis-catalog.md#always-on-for-ssis-catalog-ssisdb) e cluster di failover di Windows. Più istanze di scala Out Master vengono ospitate in un cluster di failover di Windows. Quando il servizio di scala Out Master o SSISDB verso il basso nel nodo primario, il servizio o il database SSISDB nel nodo secondario continuerà accettare le richieste degli utenti e comunicare con scala i processi di lavoro. 

Per impostare la disponibilità elevata lato master, attenersi alla procedura seguente.

## <a name="1-prerequisites"></a>1. Prerequisiti
Configurare un cluster di failover di Windows Vedere il post del blog relativo all’ [installazione della funzionalità e degli strumenti per il cluster di failover per Windows Server 2012](http://blogs.msdn.com/b/clustering/archive/2012/04/06/10291601.aspx) per le istruzioni. È necessario installare la funzionalità e gli strumenti in tutti i nodi del cluster.

## <a name="2-install-scale-out-master-on-primary-node"></a>2. Installare scala Out Master nel nodo primario
Installa Servizi motore di Database, servizi di integrazione e scala Out Master nel nodo primario per Scale Out Master. 

Durante l'installazione, è necessario 
### <a name="21-set-the-account-running-scale-out-master-service-to-a-domain-account"></a>2.1 è impostare l'account che esegue servizio scala Out Master per un account di dominio.
Questo account deve essere in grado di accedere a SSISDB nel nodo secondario in cluster di failover di Windows in futuro. Come servizio scala Out Master e SSISDB possono failover separatamente, potrebbe non essere nello stesso nodo.

![Configurazione del server a disponibilità elevata](media/ha-server-config.PNG)

### <a name="22-include-scale-out-master-service-dns-host-name-in-the-cns-of-scale-out-master-certificate"></a>2.2 includono scala Out Master DNS nome host del servizio nel certificato CN della scala Out Master.

Questo nome host da utilizzare nella scala Out Master endpoint. 

![Configurazione di master a disponibilità elevata](media/ha-master-config.PNG)

## <a name="3-install-scale-out-master-on-secondary-node"></a>3. Installare scala Out Master nel nodo secondario
Installa Servizi motore di Database, servizi di integrazione e scala Out Master nel nodo secondario per Scale Out Master. 

È consigliabile utilizzare lo stesso certificato scala Out Master con nodo primario. Esportare il certificato SSL di scala Out Master nel nodo primario con la chiave privata e installarlo nell'archivio certificati radice del computer loacl nel nodo secondario. Selezionare questo certificato durante l'installazione di scala Out Master.

![Disponibilità elevata master configurazione 2](media/ha-master-config2.PNG)

> [!Note]
> È possibile impostare più Scale Out schemi per i backup, ripetere le operazioni di scala Out Master secondario.

## <a name="4-set-up-ssisdb-always-on"></a>4. Impostare sempre SSISDB in

Le istruzioni per impostare AlwaysOn per SSISDB possono essere visualizzati in [Always On per catalogo SSIS (SSISDB)](../service/ssis-catalog.md#always-on-for-ssis-catalog-ssisdb).

Inoltre, è necessario creare un listener gourp disponibilità per il gruppo di disponibilità che aggiungere SSISDB. Vedere [creare o configurare un listener del gruppo di disponibilità](../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md).

## <a name="5-update-scale-out-master-service-configuration-file"></a>5. Aggiornare il file di configurazione servizio scala Out Master
Aggiornamento scala Out Master del servizio file di configurazione \<driver\>: \Programmi\Microsoft SQL Server\140\DTS\Binn\MasterSettings.config, sui nodi primari e secondari. Aggiornamento **SqlServerName** a *[nome DNS del Listener gruppo di disponibilità], [porta]*.

## <a name="6-enable-package-execution-logging"></a>6. Abilitare la registrazione per l'esecuzione del pacchetto

Registrazione in SSISDB viene eseguita dall'account di accesso **MS_SSISLogDBWorkerAgentLogin # # # #**, la cui password viene generato automaticamente. Per rendere il funzionamento della registrazione per tutte le repliche di SSISDB, effettuare le operazioni seguenti.

### <a name="61-change-the-password-of-msssislogdbworkeragentlogin-on-primary-sql-server"></a>6.1 modificare la password di **MS_SSISLogDBWorkerAgentLogin # # # #** nel Sql Server primario.
### <a name="62-add-the-login-to-secondary-sql-server"></a>6.2 aggiungere l'account di accesso a Sql Server secondario.
### <a name="63-update-connection-string-of-logging"></a>6.3 aggiornare la stringa di connessione della registrazione.
Chiamare stored procedure [catalog]. [update_logdb_info] con 

@server_name= '*[Nome DNS del Listener gruppo di disponibilità], [porta]*' 

e @connection_string = ' origine dati =*[nome DNS del Listener gruppo di disponibilità]*,*[porta]*; Initial Catalog = SSISDB; Id utente = # # MS_SSISLogDBWorkerAgentLogin # #; Password =*[Password]*];'.

## <a name="7-congifure-scale-out-master-service-role-of-windows-failover-cluster"></a>7. Ruolo Congifure scala Out Master del servizio del cluster di failover di Windows

Nel failover del cluster di failover, connettersi al cluster per orizzontale. Selezionare il cluster e fare clic su **azione** nel menu e quindi **Configura ruolo...** .

Nell'estratto di **configurazione guidata disponibilità elevata**selezionare **servizio generico** in **selezionare il ruolo** pagina e selezionare SQL Server Integration Services scala Out Master 14.0 in **Seleziona servizio** pagina.

Nel **punto di accesso Client** pagina, immettere il nome host DNS del servizio scala Out Master.

![Disponibilità elevata guidata 1](media/ha-wizard1.PNG)

Completare la procedura guidata.

## <a name="8-update-master-address-in-ssisdb"></a>8. Aggiornare Master indirizzo in SSISDB

Nel Server SQL primario, eseguire stored procedure [SSIS]. [catalog]. [update_master_address] con il parametro @MasterAddress = N'https: / / [nome host DNS service scala Out Master]: [Port Master]'. 

## <a name="9-add-scale-out-worker"></a>9. Aggiungere scalabilità lavoro

A questo punto, è possibile aggiungere una scala i processi di lavoro con l'aiuto di [scala Out Manager](integration-services-ssis-scale-out-manager.md). Immettere *[nome DNS di Listener gruppo di disponibilità di SQL Server]*,*[porta]* nella pagina di connessione.





