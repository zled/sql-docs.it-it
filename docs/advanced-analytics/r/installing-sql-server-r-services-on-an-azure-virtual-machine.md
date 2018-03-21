---
title: "Installazione delle funzionalità di SQL Server machine learning in una macchina virtuale di Azure | Documenti Microsoft"
ms.custom: 
ms.date: 10/31/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3c223b8-75c4-412e-a319-d57ecf6533af
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 572aeffdc0d3c06a4c3bda17e3f3d438b2819183
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2018
---
# <a name="installing-sql-server-machine-learning-features-on-an-azure-virtual-machine"></a>Installazione funzionalità su una macchina virtuale di Azure di apprendimento automatico SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
 
Se si distribuisce una macchina virtuale di Azure che include [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], è ora possibile selezionare apprendimento come funzionalità da aggiungere all'istanza quando viene creata la macchina virtuale.

+ [Creare una nuova macchina virtuale che include servizi R e SQL Server 2016](#new)
+ [Aggiungere le funzionalità di machine learning a una macchina virtuale esistente con SQL Server 2016](#existing)

> [!NOTE]
> Macchine virtuali sono ora disponibili per SQL Server 2017! Vedere [questo annuncio](https://azure.microsoft.com/blog/announcing-new-azure-vm-images-sql-server-2017-on-linux-and-windows/) per informazioni dettagliate.
> 
> R è disponibile anche come una funzionalità di anteprima di Database SQL di Azure. Per altre informazioni, vedere [usando R in Database SQL di Azure](../r/using-r-in-azure-sql-database.md).

## <a name="create-a-new-sql-server-2017-virtual-machine"></a>Creare una nuova macchina virtuale di SQL Server 2017

Per utilizzare Python o R in SQL Server 2017, assicurarsi di ottenere una macchina virtuale basata su Windows. [!INCLUDE[sscurrentlong-md](../../includes/sscurrentlong-md.md)] in Linux supporta fast [punteggio native](../sql-native-scoring.md) utilizzando la funzione di stima di T-SQL, ma altre funzionalità di apprendimento non sono disponibili ancora in questa edizione.

Per un elenco di offerte di macchina virtuale SQL Server, vedere questo articolo: [Panoramica di SQL Server in macchine virtuali di Azure (Windows)](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-iaas-overview).

### <a name="new"></a>Creare una nuova VM SQL Server Enterprise con machine learning

1. Nel portale di Azure, fare clic su macchine VIRTUALI e quindi fare clic su nuovo.
2. Select SQL Server 2017 Enterprise Edition.
3. Configurare il nome del server e le autorizzazioni dell'account e selezionare un piano tariffario.
4. In **impostazioni di SQL Server** (passaggio 4 dell'installazione guidata macchina virtuale), individuare **Machine Learning Services (Advanced Analitica)** e fare clic su **abilitare**.
5. Esaminare il riepilogo visualizzato per la convalida e fare clic su **OK**.
6. Quando la macchina virtuale è pronta, connettersi a essa e aprire SQL Server Management Studio, che è preinstallato. Machine learning è pronto per l'esecuzione.
7. Per verificarlo, è possibile aprire una nuova finestra di query ed eseguire un'istruzione semplice come quella illustrata qui, che usa R per generare una sequenza di numeri da 1 a 10.

    ```
    EXEC sp_execute_external_script
    @language = N'R'
    , @script = N' OutputDataSet <- as.data.frame(seq(1, 10, ));'
    , @input_data_1 = N'   ;'
    WITH RESULT SETS (([Sequence] int NOT NULL));
    ```

6. Se si prevede di connettersi all'istanza da un client di analisi scientifica dei dati remoti, completare [passaggi aggiuntivi](#additional-steps) in base alle esigenze.

### <a name="disable-machine-learning-features-on-a-sql-server-vm"></a>Disabilitare le funzionalità di machine learning in una VM SQL Server

È inoltre possibile abilitare o disabilitare la funzionalità in una macchina virtuale di SQL Server esistente in qualsiasi momento.

1. Aprire il pannello della macchina virtuale.
2. Fare clic su **Impostazioni** e selezionare **Configurazione di SQL Server**.
3. Apportare modifiche alle funzionalità e si applicano.

### <a name="existing"></a>Aggiungere R Services a una macchina virtuale esistente SQL Server 2016 Enterprise

Se si crea una macchina virtuale di Azure che incluso SQL Server senza di machine learning, è possibile aggiungere la funzionalità attenendosi alla procedura seguente:

1. Eseguire di nuovo l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e aggiungere la funzionalità nella pagina **Configurazione server** della procedura guidata.
2. Consentire l'esecuzione di script esterni e riavviare l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [installare SQL Server 2016 R Services](../install/sql-r-services-windows-install.md).
3. (Facoltativo) Configurare l'accesso al database per gli account di lavoro R, se necessario per l'esecuzione di script remoti.
4. (Facoltativo) Modificare una regola del firewall nella macchina virtuale di Azure, se si intende consentire l'esecuzione di script R dai client di data science remoti. Per altre informazioni, vedere [Sbloccare il firewall](#firewall).
5. Installare o abilitare le librerie di rete necessarie. Per altre informazioni, vedere [Aggiungere protocolli di rete](#network).

## <a name="additional-steps"></a>Passaggi aggiuntivi

Se si prevede che i client remoti per accedere al server come un contesto di calcolo di SQL Server remoto, sono richiesti alcuni passaggi aggiuntivi.

### <a name="firewall"></a>Sbloccare il firewall

Per impostazione predefinita, il firewall nella macchina virtuale di Azure include una regola che blocca rete l'accesso per gli account utente locale.

È necessario disabilitare questa regola per assicurarsi che sia possibile accedere il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza da un client di analisi scientifica dei dati remota.  In caso contrario, non è possibile eseguire il codice di apprendimento in contesti di calcolo che utilizzano l'area di lavoro della macchina virtuale.

Per abilitare l'accesso dai client di analisi scientifica dei dati remoti:

1. Nella macchina virtuale aprire Windows Firewall con protezione avanzata.
2. Selezionare **Regole in uscita**
3. Disabilitare la regola seguente:
  
     `Block network access for R local user accounts in SQL Server instance MSSQLSERVER`
  
### <a name="enable-odbc-callbacks-for-remote-clients"></a>Abilitare i callback ODBC per i client remoti

Se si prevede che i client che chiamano il server saranno necessario inviare query ODBC come parte della loro soluzioni di apprendimento, è necessario assicurarsi che la finestra di avvio può effettuare chiamate ODBC per conto del client remoto. A tale scopo, è necessario consentire agli account di lavoro SQL usati da Launchpad di accedere all'istanza.
Per altre informazioni, vedere [installare SQL Server 2016 R Services](../install/sql-r-services-windows-install.md).

### <a name="network"></a>Aggiungere protocolli di rete

+ Abilitare Named Pipes
  
  Attualmente, [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] usa il protocollo Named Pipes per le connessioni tra i computer client e server e per alcune connessioni interne. Se il protocollo Named Pipes non è abilitato, è necessario installarlo e abilitarlo sia nella macchina virtuale di Azure che nei client di data science che si connettono al server.
  
+ Abilitare TCP/IP

  È necessaria per le connessioni loopback TCP/IP. Se viene visualizzato il seguente errore, abilitare TCP/IP nella macchina virtuale che supporta l'istanza:

  "DBNETLIB; SQL Server non esiste o accesso negato"

## <a name="related-resources"></a>Risorse correlate

[Uso di R in Database SQL di Azure](../r/using-r-in-azure-sql-database.md)