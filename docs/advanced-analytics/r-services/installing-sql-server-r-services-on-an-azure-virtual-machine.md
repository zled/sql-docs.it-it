---
title: "Installazione di SQL Server R Services in una macchina virtuale di Azure | Microsoft Docs"
ms.custom: ""
ms.date: "12/07/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c3c223b8-75c4-412e-a319-d57ecf6533af
caps.latest.revision: 11
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 8
---
# Installazione di SQL Server R Services in una macchina virtuale di Azure
 
Se si distribuisce una macchina virtuale Azure che include [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], è ora possibile selezionare servizi R come funzionalità da aggiungere all'istanza quando viene creata la macchina Virtuale. 



+ [Creare una nuova macchina Virtuale con SQL Server 2016 e servizi R](#new)
+ [Aggiungere servizi R a una macchina virtuale esistente con SQL Server 2016](#existing)

## <a name="a-namenewacreate-a-new-sql-server-2016-enterprise-virtual-machine-with-r-services-enabled"></a><a name="new"></a>Creare una nuova SQL Server 2016 Enterprise macchina virtuale con R servizi abilitati

1. Nel portale di Azure, fare clic su MACCHINE VIRTUALI e quindi fare clic su NUOVO.
2. Selezionare l'edizione Enterprise SQL Server 2016.
3. Configurare le autorizzazioni di nome e un account di server e selezionare un piano tariffario.
4. Nel passaggio 4 nella macchina Virtuale installazione guidata, in **impostazioni SQL Server**, individuare **servizi R (analisi avanzata)** e fare clic su **abilitare**.
5. Esaminare il riepilogo presentato per la convalida e fare clic su **OK**.
6. Quando la macchina virtuale è pronta, connettersi ad esso e aprire SQL Server Management Studio, che sia già installato. Servizi di R è pronto per l'esecuzione. 
7. Per verificarlo, è possibile aprire una nuova finestra query ed eseguire un'istruzione semplice, ad esempio seguente, che usa R per generare una sequenza di numeri da 1 a 10.
   ```
    execute sp_execute_external_script
    @language = N'R'
    , @script = N' OutputDataSet <- as.data.frame(seq(1, 10, ));'
    , @input_data_1 = N'   ;'
    WITH RESULT SETS (([Sequence] int NOT NULL));
   ```
6. Se connetterà all'istanza da un client di analisi scientifica dei dati remota, completare [passaggi aggiuntivi](#additional-steps) in base alle esigenze.


## <a name="additional-steps"></a>Passaggi aggiuntivi  

Potrebbero essere necessario completare alcuni passaggi aggiuntivi per utilizzare i servizi di R Se si prevede che i client remoti di accedere al server come contesto di calcolo di un Server SQL remoto.

### <a name="a-namefirewallaunblock-the-firewall"></a><a name="firewall"></a>Sblocco del firewall  
  
È necessario modificare una regola del firewall nella macchina virtuale per assicurarsi che sia possibile accedere il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza da un client di analisi scientifica dei dati remota.  In caso contrario, potrebbe non essere in grado di utilizzare la clausola compute contesti che richiedono l'utilizzano dell'area di lavoro della macchina virtuale. 

Per impostazione predefinita, il firewall nella macchina virtuale di Azure include una regola che blocchi di accesso per gli account utente di R locali alla rete.  
  
Per abilitare l'accesso ai servizi R dai client di analisi scientifica dei dati remota:
1. Nella macchina virtuale, aprire Windows Firewall con sicurezza avanzata.
2. Selezionare **regole in uscita**
3. Disabilitare la regola seguente:  
  
     `Block network access for R local user accounts in SQL Server instance MSSQLSERVER`  
  
### <a name="enable-odbc-callbacks-for-remote-clients"></a>Abilita i callback ODBC per i client remoti

Se si prevede che client R chiamano il server sarà necessario eseguire query ODBC come parte delle soluzioni R, è necessario assicurarsi che la finestra di avvio può effettuare chiamate ODBC per conto del client remoto. A tale scopo, è necessario consentire gli account di lavoro SQL che vengono utilizzati dalla finestra di avvio per accedere all'istanza.
Per ulteriori informazioni, vedere [Imposta SQL Server R servizi](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md). 

### <a name="a-namenetworkaadd-network-protocols"></a><a name="network"></a>Aggiungere i protocolli di rete  
  
+ Attivare le Named pipe
  
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] utilizza il protocollo Named Pipes per le connessioni tra i computer client e server e per alcune connessioni interne. Se la Named pipe non è abilitata, è necessario installare e abilitarlo su sia alla macchina virtuale di Azure e su qualsiasi client di analisi scientifica dei dati che si connettono al server.  
  
+ Abilitare TCP/IP

  È necessario per le connessioni loopback per SQL Server R servizi TCP/IP. Se viene visualizzato il seguente errore, abilitare TCP/IP nella macchina virtuale che supporta l'istanza DBNETLIB; Server SQL inesistente o accesso negato.

## <a name="how-to-disable-r-services-on-an-instance"></a>Come disabilitare i servizi di R in un'istanza

È inoltre possibile abilitare o disabilitare la funzionalità in una macchina virtuale esistente in qualsiasi momento. 

1. Aprire il pannello della macchina virtuale
2. Fare clic su **impostazioni**, e selezionare **configurazione di SQL Server**.


## <a name="a-nameexistingaadd-sql-server-r-services-to-an-existing-sql-server-2016-enterprise-virtual-machine"></a><a name="existing"></a>Aggiungere servizi di SQL Server R a una macchina virtuale esistente di SQL Server 2016 Enterprise

Se avete creato una macchina Virtuale di Azure con SQL Server 2016 che non include servizi di R, è possibile aggiungere la funzionalità attenendosi alla procedura seguente:

1. Eseguire di nuovo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] programma di installazione e aggiungere la funzionalità di **configurazione Server** pagina della procedura guidata.
2. Consentire l'esecuzione di script esterni e riavviare il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza. Per ulteriori informazioni, vedere vedere [Imposta SQL Server R servizi](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md).
3. (Facoltativo) Configurare l'accesso al database per gli account di lavoro R, se necessario per l'esecuzione di script remoto.
   Per ulteriori informazioni, vedere [Imposta SQL Server R servizi](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md). 
3. (Facoltativo) Modificare una regola firewall nella macchina virtuale di Azure, se si intende consentire l'esecuzione dello script R dai client di analisi scientifica dei dati remota. Per ulteriori informazioni, vedere [sbloccare firewall](#firewall).
4. Installare o abilitare le librerie di rete necessarie. Per ulteriori informazioni, vedere [aggiungere protocolli di rete](#network).

## <a name="see-also"></a>Vedere anche
[Impostare i servizi di Sql Server, R](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)