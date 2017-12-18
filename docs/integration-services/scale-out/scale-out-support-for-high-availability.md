---
title: "Supporto della disponibilità elevata in SQL Server Integration Services (SSIS) Scale Out | Microsoft Docs"
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
ms.openlocfilehash: 2202b61a9efce26edb0edcef53204351338ecee6
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="scale-out-support-for-high-availability"></a>Supporto della disponibilità elevata in Scale Out

In SSIS Scale Out la disponibilità elevata sul lato ruolo di lavoro viene assicurata attraverso l'esecuzione dei pacchetti con più istanze di Scale Out Worker.
La disponibilità elevata sul lato master si ottiene con [Always On for SSIS Catalog](../service/ssis-catalog.md#always-on-for-ssis-catalog-ssisdb) (Always On per il catalogo SSIS) e il cluster di failover Windows. Un cluster di failover Windows ospita più istanze di Scale Out Master. Quando il servizio Scale Out Master o il database SSISDB è inattivo nel nodo primario, il servizio o il database SSISDB nel nodo secondario continuerà ad accettare le richieste degli utenti e a comunicare con le istanze di Scale Out Worker. 

Per impostare la disponibilità elevata sul lato master, seguire questa procedura.

## <a name="1-prerequisites"></a>1. Prerequisiti
Configurare un cluster di failover di Windows Vedere il post del blog relativo all’ [installazione della funzionalità e degli strumenti per il cluster di failover per Windows Server 2012](http://blogs.msdn.com/b/clustering/archive/2012/04/06/10291601.aspx) per le istruzioni. È necessario installare la funzionalità e gli strumenti in tutti i nodi del cluster.

## <a name="2-install-scale-out-master-on-primary-node"></a>2. Installare Scale Out Master nel nodo primario
Installare i servizi del motore di database, Integration Services e Scale Out Master nel nodo primario per Scale Out Master. 

Durante l'installazione è necessario 
### <a name="21-set-the-account-running-scale-out-master-service-to-a-domain-account"></a>2.1 Impostare l'account che esegue il servizio Scale Out Master su un account di dominio.
In futuro, questo account dovrà essere in grado di accedere al database SSISDB nel nodo secondario nel cluster di failover Windows. Poiché il failover del servizio Scale Out Master e del database SSISDB può essere eseguito separatamente, questi due componenti possono anche non trovarsi nello stesso nodo.

![Configurazione del server a disponibilità elevata](media/ha-server-config.PNG)

### <a name="22-include-scale-out-master-service-dns-host-name-in-the-cns-of-scale-out-master-certificate"></a>2.2 Includere il nome host DNS del servizio Scale Out Master nei nomi comuni (CN) del certificato di Scale Out Master.

Questo nome host verrà usato nell'endpoint Scale Out Master. 

![Configurazione del master a disponibilità elevata](media/ha-master-config.PNG)

## <a name="3-install-scale-out-master-on-secondary-node"></a>3. Installare Scale Out Master nel nodo secondario
Installare i servizi del motore di database, Integration Services e Scale Out Master nel nodo secondario per Scale Out Master. 

È consigliabile usare lo stesso certificato di Scale Out Master presente nel nodo primario. Esportare il certificato SSL di Scale Out Master presente nel nodo primario con la chiave privata e installarlo nell'archivio radice dei certificati del computer locale nel nodo secondario. Selezionare questo certificato durante l'installazione di Scale Out Master.

![Configurazione del master a disponibilità elevata 2](media/ha-master-config2.PNG)

> [!Note]
> È possibile configurare più istanze di backup di Scale Out Master ripetendo le operazioni per l'istanza secondaria di Scale Out Master.

## <a name="4-set-up-ssisdb-always-on"></a>4. Configurare la funzionalità Always On per il database SSISDB

Le istruzioni per configurare Always On per il database SSISDB sono disponibili in [Always On for SSIS Catalog (SSISDB)](../service/ssis-catalog.md#always-on-for-ssis-catalog-ssisdb) (Always On per il catalogo SSIS (SSISDB)).

È inoltre necessario creare un listener del gruppo di disponibilità per il gruppo di disponibilità in cui è stato aggiunto il database SSISDB. Vedere [Creare o configurare un listener del gruppo di disponibilità](../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md).

## <a name="5-update-scale-out-master-service-configuration-file"></a>5. Aggiornare il file di configurazione del servizio Scale Out Master
Aggiornare il file di configurazione del servizio Scale Out Master, \<unità\>:\Programmi\Microsoft SQL Server\140\DTS\Binn\MasterSettings.config nei nodi primario e secondario. Aggiornare **SqlServerName** in *[Nome DNS del listener del gruppo di disponibilità],[Porta]*.

## <a name="6-enable-package-execution-logging"></a>6. Abilitare la registrazione dell'esecuzione dei pacchetti

La registrazione in SSISDB viene eseguita dall'account di accesso **##MS_SSISLogDBWorkerAgentLogin##** la cui password viene generata automaticamente. Per il corretto funzionamento della registrazione per tutte le repliche di SSISDB, seguire questa procedura.

### <a name="61-change-the-password-of-msssislogdbworkeragentlogin-on-primary-sql-server"></a>6.1 Cambiare la password di **##MS_SSISLogDBWorkerAgentLogin##** nell'istanza SQL Server primaria.
### <a name="62-add-the-login-to-secondary-sql-server"></a>6.2 Aggiungere l'account di accesso all'istanza SQL Server secondaria.
### <a name="63-update-connection-string-of-logging"></a>6.3 Aggiornare la stringa di connessione della registrazione.
Chiamare la stored procedure [catalog].[update_logdb_info] con 

@server_name = "*[Nome DNS del listener del gruppo di disponibilità],[Porta]*" 

e @connection_string = "Origine dati=*[Nome DNS del listener del gruppo di disponibilità]*,*[Porta]*;Catalogo iniziale=SSISDB;ID utente=##MS_SSISLogDBWorkerAgentLogin##;Password=*[Password]*];".

## <a name="7-congifure-scale-out-master-service-role-of-windows-failover-cluster"></a>7. Configurare il ruolo del servizio Scale Out Master del cluster di failover Windows

In Gestione cluster di failover connettersi al cluster per Scale Out. Selezionare il cluster e fare clic su **Azione** nel menu e quindi su **Configura ruolo...**.

Nella finestra popup **Configurazione guidata disponibilità elevata** selezionare **Servizio generico** nella pagina **Selezione ruolo** e scegliere SQL Server Integration Services Scale Out Master 14.0 nella pagina **Seleziona servizio**.

Nella pagina **Punto di accesso client** immettere il nome host DNS del servizio Scale Out Master.

![Configurazione guidata disponibilità elevata 1](media/ha-wizard1.PNG)

Completare la procedura guidata.

## <a name="8-update-master-address-in-ssisdb"></a>8. Aggiornare l'indirizzo master in SSISDB

Nell'istanza SQL Server primaria eseguire la stored procedure [SSIS].[catalog].[update_master_address] con il parametro @MasterAddress = N'https://[Nome host DNS del servizio Scale Out Master]:[Porta master]'. 

## <a name="9-add-scale-out-worker"></a>9. Aggiungere Scale Out Worker

A questo punto è possibile aggiungere le istanze di Scale Out Worker con l'aiuto di [Scale Out Manager](integration-services-ssis-scale-out-manager.md). Immettere *[Nome DNS del listener del gruppo di disponibilità di SQL Server]*,*[Porta]* nella pagina di connessione.




