---
title: Configurare il Server SQL SMP esterni per la ricezione di copie della tabella remota (PDW)
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/13/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6bbd2ed6-064e-4b45-b67b-608dc0f2b2bc
caps.latest.revision: 13
ms.openlocfilehash: 94b62dbae331c19fa97c1625a53804f4cd96bfa5
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="configure-an-external-smp-sql-server-to-receive-remote-table-copies"></a>Configurare un Server SQL SMP esterni per ricevono una copia di tabella remota
Viene descritto come configurare un'istanza esterna di SQL Server per ricevere copie tabella remota di SQL Server PDW.  
  
In questo argomento viene descritto uno dei passaggi di configurazione per la configurazione di copia della tabella remota. Per un elenco di tutti i passaggi di configurazione, vedere [copia della tabella remota](remote-table-copy.md).  
  
## <a name="before-you-begin"></a>Prima di iniziare  
Prima di poter configurare il Server SQL esterno, è necessario:  
  
-   Disporre di un sistema di Windows con SQL Server 2008 Enterprise Edition o versione successiva pronta per essere installata o già installato. Il sistema di Windows deve essere già configurato seguendo le istruzioni di [configurare un esterno Windows sistema per ricevere remoto tabella copie utilizzando InfiniBand](configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband.md).  
  
-   Un account di amministrazione di Windows con la possibilità di configurare l'istanza di SQL Server e il sistema di Windows.  
  
-   Un account accesso SQL Server (se è già installato SQL Server) con la possibilità di creare account di accesso e concedere le autorizzazioni per i database di destinazione.  
  
## <a name="HowToSQLServer"></a>Configurare un Server SQL SMP esterni per ricevono una copia di tabella remota  
La funzionalità di copia della tabella remota copia tabelle dal dispositivo pwd di SQL Server in un database SMP SQL Server esterno che è in esecuzione in un sistema di Windows. Dopo aver configurato il sistema esterno di Windows per la ricezione di copie di una tabella remota, il passaggio successivo è di installare e configurare SQL Server al sistema di Windows.  
  
Per configurare SQL Server, attenersi alla procedura seguente:  
  
1.  Nel sistema Windows, installare SQL Server 2008 Enterprise Edition o versione successiva. Si parla di SQL server SMP.  
  
2.  Configurare SQL Server per accettare connessioni TCP/IP su una porta TCP predefinita. Questa configurazione è disabilitata per impostazione predefinita e deve essere abilitata per consentire a SQL Server PDW per connettersi a SQL Server SMP.  
  
3.  Disabilitare Windows firewall o configurare la porta TCP di SQL Server SMP in modo che funzionerà con Windows firewall è abilitato.  
  
4.  Configurare SQL Server per consentire la modalità di autenticazione di SQL Server. Esportazione di dati paralleli sempre utilizza gli account di SQL Server per l'autenticazione.  
  
5.  Stabilire un account di SQL Server nel Server SQL SMP che verrà utilizzato per l'autenticazione. Concedere all'account il privilegio per creare, eliminare e inserire dati in tabelle nel database di destinazione per l'operazione di esportazione di dati paralleli.  
  
## <a name="BPSQLConfig"></a>Procedure consigliate per la configurazione del Server SQL SMP per copia della tabella remota  
Quando si configura il Server SQL SMP per ricevono una copia di tabella remota, è possibile utilizzare le seguenti procedure consigliate per migliorare le prestazioni.  
  
1.  Seguire le procedure consigliate, come illustrato nella documentazione del prodotto SQL Server. Ad esempio, abilitare la crittografia dei dati. Per ulteriori informazioni sulla sicurezza di SQL Server, vedere [sicurezza di SQL Server](../relational-databases/security/securing-sql-server.md) su MSDN.  
  
2.  Utilizzare il modello di recupero di massa o semplice.  
  
    Durante i dati paralleli di operazioni di esportazione, dati inserite nella tabella di destinazione appena creato in blocco. Per ottenere prestazioni ottimali durante l'inserimento bulk, impostare il database di destinazione da utilizzare una delle operazioni bulk o il modello di recupero con registrazione minima.  
  
3.  Per recuperare lo spazio del log, utilizzare l'opzione batch_size.  
  
    Sebbene il recupero di massa o semplice modelli di utilizzo minimo la registrazione per l'inserimento bulk dei dati, si verifica ancora alcuni registrazione. Per impedire che i file di log aumentano troppo, utilizzare l'opzione batch_size di SQL Server per recuperare periodicamente lo spazio di log.  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
