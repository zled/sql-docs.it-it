---
title: Configurazione del Firewall PDW (Analitica piattaforma sistema)
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 191f292d-16bc-4166-b855-158854ad062d
caps.latest.revision: 28
ms.openlocfilehash: 8795f2254160a4ba605643b89dc4b9df0cce4c7f
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="pdw-firewall-configuration"></a>Configurazione del Firewall PDW
Il **Firewall** pagina di Gestione configurazione SQL Server PDW consente di abilitare o disabilitare regole firewall che consentono o impediscono l'accesso a porte specifiche sul dispositivo di sistema della piattaforma Analitica.  
  
## <a name="to-manage-ports-and-firewall-rules-for-appliance-nodes"></a>Per gestire le porte e firewall le regole per i nodi dello strumento  
  
1.  Avviare Gestione configurazione. Per altre informazioni, vedere [avviare Gestione configurazione &#40;Analitica Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  Nel riquadro a sinistra di Configuration Manager, espandere **Parallel Data Warehouse topologia**, quindi fare clic su **Firewall**.  
  
3.  Individuare la regola di porta o un firewall per aggiornare l'elenco di configurazione, quindi selezionare o deselezionare la casella accanto a tale elemento. In questo elenco, incluse le porte con connessione esterna di nodi, vengono visualizzate solo opzioni configurabili dall'amministratore di SQL Server PDW.  
  
4.  Fare clic su **applica** per salvare le modifiche.  
  
![DWConfig Appliance PDW Firewall](./media/pdw-firewall-configuration/SQL_Server_PDW_DWConfig_ApplPDWFirewall.png "SQL_Server_PDW_DWConfig_ApplPDWFirewall")  
  
## <a name="external-ports"></a>Porte esterne  
Le seguenti porte siano aperte per le connessioni client provenienti da di fuori di PDW.  
  
|Scopo|Porta #|Nodi|  
|-----------|-----------|---------|  
|Accesso SQL Client per PDW TDS|17001|CTL|  
|Accesso ai Client del caricatore (dwloader & SSIS)|8001|CTL|  
|Accesso desktop remoto|3389|CTL, CMP|  
|BinaryLoaderDataChannel SSIS|16551|CTL|  
|dwloader BinaryLoaderDataChannel|16551|CMP|  
|SSL crittografata connessioni (per comunicazioni interne, per accedere alla Console di amministrazione e di accedere ai servizi del cluster HDInsight)|443|Tutti i nodi|  
|SQL Server PDW carico il flusso di controllo - le credenziali di Windows|8002|CTL|  
|_Kerberos|88|AD01 e AD02,|  
|_ldap|389|AD01 e AD02|  
  
## <a name="internal-ports"></a>Porte interne  
Le seguenti porte utilizzate da PDW per le comunicazioni interne, ma non vengono aperti per le connessioni provenienti di fuori del dispositivo di PDW.  
  
|Scopo|Porta #|Nodi|  
|-----------|-----------|---------|  
|Traffico del canale di controllo DMS|16450|CTL, CMP|  
|Traffico del canale dati DMS|16550|CTL, CMP|  
|Diagnostica interna|16650|CTL, CMP|  
|Stato di failover (DMS)|15000|CTL, CMP|  
|Stato di failover (modulo)|15001|CMP|  
|Intervallo di porte dinamiche di (temporaneo)|20000-65535|CTL, CMP|  
|Intervalli di porte di SQL Server (TDS)|1433, 1500-1508|CTL, CMP|  
  
> [!NOTE]  
> Creazione di tabelle esterne o origini dati esterne utilizza la porta TCP 8020 per impostazione predefinita. Queste istruzioni possono essere configurate per utilizzare invece le altre porte. La porta predefinita Hortonworks JOB_TRACKER_LOCATION è 50300. L'integrazione con altri sistemi e gli strumenti possono richiedere le porte aggiuntive.  
  
<!-- MISSING LINKS ## See Also  
[HDInsight Firewall Configuration &#40;Analytics Platform System&#41;](hdinsight-firewall-configuration.md)  -->  
  
