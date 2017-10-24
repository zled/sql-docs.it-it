---
title: Installazione di SQL Server R Services in una macchina virtuale di Azure | Microsoft Docs
ms.custom: 
ms.date: 07/10/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3c223b8-75c4-412e-a319-d57ecf6533af
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e673268b1f6b56890f22576d293135b2675ed4ab
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="installing-sql-server-r-services-on-an-azure-virtual-machine"></a>Installazione di SQL Server R Services in una macchina virtuale di Azure
 
Se si distribuisce una macchina virtuale di Azure che include [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], è ora possibile selezionare l'apprendimento come funzionalità da aggiungere all'istanza quando viene creata la macchina virtuale.

+ [Creare una nuova VM con SQL Server 2016 e R Services](#new)
+ [Aggiungere R Services a una macchina virtuale esistente con SQL Server 2016](#existing)

## <a name="new"></a>Creare una nuova macchina virtuale SQL Server 2016 Enterprise con R Services abilitato

1. Nel portale di Azure, fare clic su macchine VIRTUALI e quindi fare clic su nuovo.
2. Selezionare SQL Server 2016 Enterprise Edition.
3. Configurare il nome del server e le autorizzazioni dell'account e selezionare un piano tariffario.
4. Nel passaggio 4 dell'installazione guidata della VM, in **Impostazioni di SQL Server** individuare **Servizi R (analisi avanzata)** e fare clic su **Abilita**.
5. Esaminare il riepilogo visualizzato per la convalida e fare clic su **OK**.
6. Quando la macchina virtuale è pronta, connettersi a essa e aprire SQL Server Management Studio, che è preinstallato. R Services è pronto per l'esecuzione.
7. Per verificarlo, è possibile aprire una nuova finestra di query ed eseguire un'istruzione semplice come quella illustrata qui, che usa R per generare una sequenza di numeri da 1 a 10.
   ```
    execute sp_execute_external_script
    @language = N'R'
    , @script = N' OutputDataSet <- as.data.frame(seq(1, 10, ));'
    , @input_data_1 = N'   ;'
    WITH RESULT SETS (([Sequence] int NOT NULL));
   ```
6. Se ci si connetterà all'istanza da un client di data science remoto, completare i [passaggi aggiuntivi](#additional-steps) in base alle esigenze.


## <a name="additional-steps"></a>Passaggi aggiuntivi  

Se si prevede che i client remoti di accedere al server come un contesto di calcolo di SQL Server remoto, sono richiesti alcuni passaggi aggiuntivi.

### <a name="firewall"></a>Sbloccare il firewall

Per impostazione predefinita, il firewall della macchina virtuale di Azure include una regola che blocca l'accesso alla rete per gli account utente R locali.

È necessario disabilitare questa regola per assicurarsi che sia possibile accedere il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza da un client di analisi scientifica dei dati remota.  In caso contrario, il codice R non è possibile eseguire in contesti di calcolo che utilizzano l'area di lavoro della macchina virtuale, anche se altro codice R utilizza il contesto di calcolo di SQL Server senza problemi.

Per consentire l'accesso a R Services dai client di data science remoti:

1. Nella macchina virtuale aprire Windows Firewall con protezione avanzata.
2. Selezionare **Regole in uscita**
3. Disabilitare la regola seguente:
  
     `Block network access for R local user accounts in SQL Server instance MSSQLSERVER`
  
### <a name="enable-odbc-callbacks-for-remote-clients"></a>Abilitare i callback ODBC per i client remoti

Se si prevede che i client R che chiamano il server dovranno eseguire query ODBC come parte delle soluzioni R, è necessario assicurarsi che Launchpad possa effettuare chiamate ODBC per conto del client remoto. A tale scopo, è necessario consentire agli account di lavoro SQL usati da Launchpad di accedere all'istanza.
Per altre informazioni, vedere [Configurare SQL Server R Services](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md).

### <a name="network"></a>Aggiungere protocolli di rete

+ Abilitare Named Pipes
  
  Attualmente, [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] usa il protocollo Named Pipes per le connessioni tra i computer client e server e per alcune connessioni interne. Se il protocollo Named Pipes non è abilitato, è necessario installarlo e abilitarlo sia nella macchina virtuale di Azure che nei client di data science che si connettono al server.
  
+ Abilitare TCP/IP

  Il protocollo TCP/IP è necessario per le connessioni loopback a SQL Server R Services. Se viene visualizzato il seguente errore, abilitare TCP/IP nella macchina virtuale che supporta l'istanza:

  "DBNETLIB; SQL Server non esiste o accesso negato"

## <a name="how-to-disable-r-services-on-an-instance"></a>Come disabilitare R Services in un'istanza

È anche possibile abilitare o disabilitare la funzionalità in una macchina virtuale esistente in qualsiasi momento.

1. Aprire il pannello della macchina virtuale
2. Fare clic su **Impostazioni** e selezionare **Configurazione di SQL Server**.

## <a name="existing"></a>Aggiungere una macchina virtuale esistente di SQL Server 2016 Enterprise Edition di SQL Server R Services

Se si crea una macchina virtuale di Azure che non includono R Services, è possibile aggiungere la funzionalità attenendosi alla procedura seguente:

1. Eseguire di nuovo l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e aggiungere la funzionalità nella pagina **Configurazione server** della procedura guidata.
2. Consentire l'esecuzione di script esterni e riavviare l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [Configurare SQL Server R Services](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md).
3. (Facoltativo) Configurare l'accesso al database per gli account di lavoro R, se necessario per l'esecuzione di script remoti.
   Per altre informazioni, vedere [Configurare SQL Server R Services](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md).
3. (Facoltativo) Modificare una regola del firewall nella macchina virtuale di Azure, se si intende consentire l'esecuzione di script R dai client di data science remoti. Per altre informazioni, vedere [Sbloccare il firewall](#firewall).
4. Installare o abilitare le librerie di rete necessarie. Per altre informazioni, vedere [Aggiungere protocolli di rete](#network).

## <a name="related-resources"></a>Risorse correlate

[Configurare SQL Server R Services](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)

