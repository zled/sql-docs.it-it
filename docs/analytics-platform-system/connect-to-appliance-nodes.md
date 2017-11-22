---
title: Connettersi a nodi dello strumento (Analitica piattaforma sistema)
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f975aa91-c816-4b29-89bf-923ab5b4abb4
caps.latest.revision: "19"
ms.openlocfilehash: 00db55a8c4835407d9b5aeb2ce7dac30f94eb888
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="connect-to-appliance-nodes"></a>Connettersi a nodi dello strumento
Questo argomento illustra i vari modi per connettersi a ogni nodo del dispositivo di sistema della piattaforma Analitica.  
  
## <a name="connecting-with-hadoop"></a>Connessione Hadoop  
Prima di usare Hadoop con SQL Server PDW, chiedere all'amministratore di dispositivo per installare l'ambiente di Runtime Java su SQL Server PDW. Per istruzioni, vedere [configurare la connettività di PolyBase per i dati esterni &#40; Sistema della piattaforma Analitica &#41; ](configure-polybase-connectivity-to-external-data.md) nelle operazioni di Appliance Guida.  
  
## <a name="ConnectingToIndividualNodes"></a>Connessione a nodi dello strumento  
Ciascuno dei nodi dello strumento è possibile accedere direttamente solo in scenari di utilizzo specifici e dai tipi di utente specifico. La tabella seguente elenca ogni nodo del dispositivo e gli scenari in cui gli utenti si connetteranno direttamente a tale nodo.  
  
<!-- MISSING LINKS For information on the purpose of each node, see [Understanding SQL Server PDW &#40;SQL Server PDW&#41;](../sqlpdw/understanding-sql-server-pdw-sql-server-pdw.md).  -->  
  
|||  
|-|-|  
|**Nodo**|**Scenari di accesso**|  
|Nodo di controllo|Utilizzare un web browser per accedere alla Console di amministrazione, che viene eseguito sul nodo del controllo. Per ulteriori informazioni, vedere [monitorare il dispositivo tramite la Console di amministrazione &#40; Sistema della piattaforma Analitica &#41; ](monitor-the-appliance-by-using-the-admin-console.md).<br /><br />Tutti gli strumenti e applicazioni client di connettono al nodo di controllo, indipendentemente dal fatto che utilizzi la connessione Ethernet o InfiniBand.<br /><br />Per configurare una connessione Ethernet al nodo di controllo, utilizzare l'indirizzo IP del Cluster del nodo di controllo e la porta **17001**. Ad esempio, "192.168.0.1,17001".<br /><br />Per configurare una connessione InfiniBand al nodo di controllo, utilizzare  ***appliance_domain*-SQLCTL01** e la porta **17001**. Utilizzando  ***appliance_domain*-SQLCTL01**, il server DNS accessorio si connetterà il server alla rete InfiniBand attiva. Per configurare il server non strumento per utilizzare questa opzione, vedere [configurare schede di rete InfiniBand](configure-infiniband-network-adapters.md).<br /><br />L'amministratore del dispositivo si connette al nodo di controllo per eseguire operazioni di gestione. L'amministratore del dispositivo, ad esempio, esegue le operazioni seguenti dal nodo di controllo:<br /><br />Configurare il sistema di piattaforma Analitica con il **dwconfig.exe** dello strumento di configurazione.|  
|Nodo di calcolo|Consente di calcolare le connessioni di nodo sono indirizzate al nodo di controllo. Gli indirizzi IP dei nodi di calcolo non vengono immessi mai in comandi dell'applicazione come parametri.<br /><br />Per il caricamento, backup, copia della tabella remota, Hadoop e SQL Server PDW inviare o ricevere i dati direttamente in parallelo tra i nodi di calcolo e i nodi non accessorio o il server. Queste applicazioni connesse con SQL Server PDW connettendosi al nodo di controllo e quindi il nodo di controllo indica a SQL Server PDW per stabilire la comunicazione tra i nodi di calcolo e il server non strumento.<br /><br />Ad esempio, queste operazioni di trasferimento dei dati avviene in parallelo con le connessioni dirette ai nodi di calcolo:<br /><br />Caricamento dal server durante il caricamento di SQL Server PDW.<br /><br />Backup di un database da SQL Server PDW al server di backup.<br /><br />Ripristino di un database dal server di backup in SQL Server PDW.<br /><br />Eseguire query sui dati di Hadoop da SQL Server PDW.<br /><br />Esportazione dei dati da SQL Server PDW in una tabella esterna di Hadoop.<br /><br />Copia di una tabella di SQL Server PDW a un database SMP SQL Server remoto.|  
  
## <a name="connecting-to-the-ethernet-and-infiniband-networks"></a>La connessione per le reti Ethernet e InfiniBand  
Server remoti possono connettersi tramite rete InfiniBand accessorio o tramite rete Ethernet. Per motivi di prestazioni, il caricamento di server, server di backup e la ricezione dei dati tramite server **CREATE REMOTE TABLE AS SELECT** istruzioni, in genere trasferire i dati attraverso la rete InfiniBand di dispositivo.  
  
È possibile configurare il server non strumento per appartengono al cliente del gruppo di lavoro o dominio e quindi utilizzare la propria rete cliente per connettersi a tali server e il trasferimento di dati su di essi. Inoltre, il server non strumento connesso al dispositivo InfiniBand hanno l'opzione per trasferire dati attraverso la rete InfiniBand accessorio; Prestare attenzione con questo poiché può rallentare le prestazioni di SQL Server PDW.  
  
Ad esempio, questa istruzione aggiunge le credenziali di rete per l'esecuzione di backup per un server di backup che ha un indirizzo IP InfiniBand 192.168.0.1 InfiniBand. Il dominio applicazione è *mypdw*, e l'istruzione viene eseguita dal server di backup. Prima di eseguire questa istruzione, è necessario specificare i propri parametri.  
  
```  
sqlcmd -S "mypdw-sqlctl01,17001" -U sa -P password -I -Q "exec sp_pdw_add_network_credentials '192.168.0.1', 'mypdw\Administrator', 'password'"  
```  
  
Ad esempio, un comando di caricamento inizierà con gli elementi seguenti:  
  
```  
dwloader –S mypdw-SQLCTL01  
```  
  
<!-- MISSING LINKS ## See Also  
[Configure an External Windows System To Receive Remote Table Copies Using InfiniBand &#40;SQL Server PDW&#41;](../sqlpdw/configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband-sql-server-pdw.md)  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
