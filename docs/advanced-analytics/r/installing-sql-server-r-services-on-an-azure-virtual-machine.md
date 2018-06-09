---
title: Installare funzionalità di apprendimento del computer SQL Server in una macchina virtuale di Azure | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: a0780d4f974761af563ff2ed6e20e444b2d85ef9
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34563679"
---
# <a name="install-sql-server-machine-learning-features-on-an-azure-virtual-machine"></a>Installare le funzionalità in una macchina virtuale Azure di apprendimento automatico SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
 
Si consiglia di usare il [macchina virtuale di analisi scientifica dei dati](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/provision-vm), ma se si desidera che una macchina virtuale che dispone solo servizi di SQL Server 2017 Machine Learning o SQL Server 2016 R Services, in questo articolo in modo semplificato i passaggi.

## <a name="create-a-virtual-machine-on-azure"></a>Creare una macchina virtuale in Azure

1. Nel portale di Azure nell'elenco a sinistra, fare clic su **macchine virtuali** e quindi fare clic su **Add**.
2. Ricerca di SQL Server 2017 Enterprise Edition o SQL Server 2016 Enterprise Edition.
3. Configurare il nome del server e le autorizzazioni dell'account e selezionare un piano tariffario.
4. In **impostazioni di SQL Server** (passaggio 4 dell'installazione guidata macchina virtuale), individuare **Machine Learning Services (Advanced Analitica)** (oppure **R Services** per SQL Server 2016) e fare clic su  **Abilitare**.
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

### <a name="disable-machine-learning-features-on-a-sql-server-vm"></a>Disabilitare le funzionalità di machine learning in una macchina virtuale di SQL Server

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

Se si prevede che i client remoti di accedere al server come un contesto di calcolo di SQL Server remoto, sono richiesti alcuni passaggi aggiuntivi.

### <a name="firewall"></a>Sbloccare il firewall

Per impostazione predefinita, il firewall nella macchina virtuale di Azure include una regola che blocca l'accesso per gli account utente locale rete.

È necessario disabilitare questa regola per assicurarsi che sia possibile accedere il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza da un client di analisi scientifica dei dati remota.  In caso contrario, i machine learning codice non è possibile eseguire in contesti di calcolo che utilizzano l'area di lavoro della macchina virtuale.

Per abilitare l'accesso dai client di analisi scientifica dei dati remoti:

1. Nella macchina virtuale aprire Windows Firewall con protezione avanzata.
2. Selezionare **Regole in uscita**
3. Disabilitare la regola seguente:
  
     `Block network access for R local user accounts in SQL Server instance MSSQLSERVER`
  
### <a name="enable-odbc-callbacks-for-remote-clients"></a>Abilitare i callback ODBC per i client remoti

Se si prevede che i client che chiamano il server saranno necessario inviare query ODBC come parte del loro di machine learning solutions, è necessario assicurarsi che la finestra di avvio può effettuare chiamate ODBC per conto del client remoto. A tale scopo, è necessario consentire agli account di lavoro SQL usati da Launchpad di accedere all'istanza.
Per altre informazioni, vedere [installare SQL Server 2016 R Services](../install/sql-r-services-windows-install.md).

### <a name="network"></a>Aggiungere protocolli di rete

+ Abilitare Named Pipes
  
  Attualmente, [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] usa il protocollo Named Pipes per le connessioni tra i computer client e server e per alcune connessioni interne. Se il protocollo Named Pipes non è abilitato, è necessario installarlo e abilitarlo sia nella macchina virtuale di Azure che nei client di data science che si connettono al server.
  
+ Abilitare TCP/IP

  TCP/IP è obbligatorio per le connessioni loopback. Se viene visualizzato il seguente errore, abilitare TCP/IP nella macchina virtuale che supporta l'istanza:

  "DBNETLIB; SQL Server non esiste o accesso negato"
