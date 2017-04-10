---
title: "Always On for SSIS Catalog (SSISDB) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.ssms.alwayson.f1"
ms.assetid: 7f089455-35ee-4c13-884e-9254b685d07d
caps.latest.revision: 17
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 16
---
# Always On for SSIS Catalog (SSISDB)
  I gruppi di disponibilità Always On sono una soluzione di disponibilità elevata e recupero di emergenza che offre un'alternativa di livello enterprise al mirroring del database. Un gruppo di disponibilità supporta un ambiente di failover per un set discreto di database utente, noto come database di disponibilità, il cui failover avviene contemporaneamente. Per altre informazioni, vedere [Gruppi di disponibilità AlwaysOn](https://msdn.microsoft.com/library/hh510230.aspx).  
  
 Per garantire una disponibilità elevata del catalogo SSIS (SSISDB) e del relativo contenuto (progetti, pacchetti, log di esecuzione e così via) è possibile aggiungere il database SSISDB a un gruppo di disponibilità Always On, come accade con qualsiasi altro database utente. Quando si verifica un failover, uno dei nodi secondari diventa automaticamente il nuovo nodo primario.  
 
 > [!IMPORTANT]  Quando si verifica un failover, i pacchetti in esecuzione non vengono riavviati o ripresi. 
 
 **Contenuto dell'argomento:**  
  
1.  [Prerequisiti](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#prereq)  
  
2.  [Configurare il supporto SSIS per Always On](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#Firsttime)  
  
3.  [Aggiornamento di SSISDB in un gruppo di disponibilità](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#Upgrade)  
  
##  <a name="a-nameprereqa-prerequisites"></a><a name="prereq"></a> Prerequisiti  
 È necessario eseguire questi passaggi prerequisiti prima di abilitare il supporto Always On per il database SSISDB.  
  
1.  Configurare un cluster di failover di Windows Vedere il post del blog relativo all’ [installazione della funzionalità e degli strumenti per il cluster di failover per Windows Server 2012](http://blogs.msdn.com/b/clustering/archive/2012/04/06/10291601.aspx) per le istruzioni. È necessario installare la funzionalità e gli strumenti in tutti i nodi del cluster.  
  
2.  Installare SQL Server 2016 con Integration Services (SSIS) in ogni nodo del cluster.  
  
3.  Abilitare la funzionalità Always On per ogni istanza di SQL Server. Per altre informazioni, vedere [Abilitare e disabilitare la funzionalità Gruppi di disponibilità AlwaysOn](https://msdn.microsoft.com/library/ff878259.aspx) .  
  
##  <a name="a-namefirsttimea-configure-ssis-support-for-always-on"></a><a name="Firsttime"></a> Configurare il supporto SSIS per Always On  
  
-   [Passaggio 1: Creare un catalogo di Integration Services](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#Step1)  
  
-   [Passaggio 2: Aggiungere SSISDB a un gruppo di disponibilità Always On](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#Step2)  
  
-   [Passaggio 3: Abilitare il supporto SSIS per Always On](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#Step3)  
  
> [!IMPORTANT]  
>  -   È necessario attenersi alla procedura seguente nel **nodo primario** del gruppo di disponibilità.  
> -   Abilitare il **supporto SSIS per Always On** dopo aver aggiunto SSISDB a un gruppo Always On.  
  
###  <a name="a-namestep1a-step-1-create-integration-services-catalog"></a><a name="Step1"></a> Passaggio 1: Creare un catalogo di Integration Services  
  
1.  Avviare **SQL Server Management Studio** e connettersi a un'istanza di SQL Server nel cluster che si vuole definire come **nodo primario** del gruppo di disponibilità Always On per SSISDB.  
  
2.  In Esplora oggetti espandere il nodo del server, fare clic con il pulsante destro del mouse sul nodo **Cataloghi di Integration Services** e quindi fare clic su **Creazione catalogo**.  
  
3.  Fare clic su **Abilitazione integrazione con CLR**. Nel catalogo vengono utilizzate stored procedure CLR.  
  
4.  Fare clic su **Abilita l’esecuzione automatica della stored procedure di Integration Services all’avvio di SQL Server** per abilitare l’esecuzione della stored procedure [catalog.startup](https://msdn.microsoft.com/library/hh230984.aspx) a ogni riavvio dell’istanza del server SSIS. La stored procedure esegue la manutenzione dello stato delle operazioni per il catalogo SSISDB. Corregge lo stato di eventuali pacchetti in esecuzione in caso di arresto dell'istanza del server SSIS.  
  
5.  Immettere una **password**e quindi fare clic su **Ok**. La password consente di proteggere la chiave del database master utilizzata per crittografare i dati del catalogo. Salvare la password in un percorso sicuro. È consigliabile eseguire inoltre il backup della chiave master del database. Per ulteriori informazioni, vedere [Backup della chiave master di un database](https://msdn.microsoft.com/library/aa337546.aspx).  
  
###  <a name="a-namestep2a-step-2-add-ssisdb-to-an-always-on-availability-group"></a><a name="Step2"></a>Passaggio 2: Aggiungere SSISDB a un gruppo di disponibilità Always On  
 Per aggiungere il database SSISDB a un gruppo di disponibilità Always On, si procede come per l'aggiunta di qualsiasi altro database utente a un gruppo di disponibilità. Vedere [Utilizzare la Creazione guidata Gruppo di disponibilità](https://msdn.microsoft.com/library/hh403415.aspx).  
  
 È necessario inserire la password specificata durante la creazione del catalogo SSIS nella pagina **Seleziona database** della creazione guidata **Nuovo gruppo di disponibilità** .  
  
 ![New Availability Group](../../integration-services/service/media/ssis-newavailabilitygroup.png "New Availability Group")  
  
###  <a name="a-namestep3a-step-3-enable-ssis-support-for-always-on"></a><a name="Step3"></a> Passaggio 3: Abilitare il supporto SSIS per Always On  
 Dopo aver creato il catalogo di Integration Services, fare clic con il pulsante destro del mouse sul nodo **Cataloghi di Integration Services** e quindi fare clic su **Abilita supporto per AlwaysOn** Verrà visualizzata la finestra di dialogo **Abilita supporto per AlwaysOn** illustrata di seguito. Se questa voce di menu è disabilitata, verificare di avere installato tutti i prerequisiti e fare clic su **Aggiorna**.  
  
 ![Enable Support for AlwaysOn](../../integration-services/service/media/ssis-enablesupportforalwayson.png "Enable Support for AlwaysOn")  
  
> [!WARNING]  
>  Fino a quando non si abilita il supporto SSIS per Always On, il failover automatico del database SSISDB non è supportato.  
  
 Le repliche secondarie appena aggiunte dal gruppo di disponibilità AlwaysOn sono visualizzate nella tabella. Fare clic su **Connetti** per ogni replica dell'elenco e immettere le credenziali di autenticazione per la connessione alla replica. Per abilitare il supporto SSIS per Always On, l'account utente deve appartenere al gruppo sysadmin di ogni replica. Dopo aver eseguito la connessione a ogni replica, fare clic su **OK** per abilitare il supporto SSIS per Always On.  
  
##  <a name="a-nameupgradea-upgrading-ssisdb-in-an-availability-group"></a><a name="Upgrade"></a> Aggiornamento di SSISDB in un gruppo di disponibilità  
 Se si sta aggiornando SQL Server da una versione precedente e SSISDB è incluso in un gruppo di disponibilità Always On, l'aggiornamento può essere bloccato dalla regola "Verifica presenza di SSISDB in un gruppo di disponibilità Always On". Si ha tale blocco perché l'aggiornamento viene eseguito in modalità utente singolo, mentre un database di disponibilità deve essere un database multiutente. Di conseguenza durante l'aggiornamento o l'applicazione di patch, tutti i database di disponibilità, incluso SSISDB, sono portati offline e non sono aggiornati né corretti. Per completare l'aggiornamento rimuovere prima SSISDB dal gruppo di disponibilità, quindi eseguire l'aggiornamento o l’applicazione della patch di ogni nodo e infine aggiungere di nuovo SSISDB al gruppo di disponibilità.  
  
 Se la regola "Verifica presenza di SSISDB in un gruppo di disponibilità Always On" blocca l'aggiornamento, per aggiornare SQL Server è necessario seguire questa procedura.  
  
1.  Rimuovere il database SSISDB dal gruppo di disponibilità. Per altre informazioni, vedere [Rimuovere un database secondario da un gruppo di disponibilità &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/remove-a-secondary-database-from-an-availability-group-sql-server.md) e [Rimuovere un database primario da un gruppo di disponibilità &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/remove-a-primary-database-from-an-availability-group-sql-server.md).  
  
2.  Fare clic su **Riesegui** nell'aggiornamento guidato. Viene verificata la presenza di SSISDB in un gruppo di disponibilità Always On.  
  
3.  Fare clic su **Avanti** per continuare l’aggiornamento.  
  
4.  Dopo aver aggiornato tutti i nodi, aggiungere di nuovo il database SSISDB al gruppo di disponibilità Always On. Per altre informazioni, vedere [Aggiungere un database a un gruppo di disponibilità &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/add-a-database-to-an-availability-group-sql-server.md).  
  
 Se durante l'aggiornamento di SQL Server non si verifica alcun blocco e se SSISDB è presente in un gruppo di disponibilità Always On, è necessario aggiornare separatamente SSISDB dopo aver aggiornato il motore di database di SQL Server. Usare l'aggiornamento guidato SSIS per aggiornare il database SSISDB come descritto nella procedura seguente.  
  
1.  Spostare il database SSISDB dal gruppo di disponibilità, o eliminare quest’ultimo se SSISDB è l'unico database nel gruppo. Per eseguire questa attività è necessario avviare **SQL Server Management Studio** sul **nodo primario** del gruppo di disponibilità.  
  
2.  Rimuovere il database SSISDB da tutti i **nodi di replica**.  
  
3.  Aggiornare il database SSISDB nel **nodo primario**. In**Esplora oggetti** di SQL Server Management Studio espandere i **Cataloghi di Integration Services**, fare clic con il pulsante destro del mouse su **SSISDB**e quindi scegliere **Aggiornamento database**. Seguire le istruzioni dell’ **Aggiornamento guidato SSISDB** per aggiornare il database. È necessario avviare l’ **Aggiornamento guidato SSIDB** localmente sul **nodo primario**.  
  
4.  Seguire le istruzioni incluse in [Passaggio 2: Aggiungere SSISDB al gruppo di disponibilità AlwaysOn](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#Step2) per aggiungere di nuovo il database SSISDB a un gruppo di disponibilità.  
  
5.  Seguire le istruzioni incluse in [Passaggio 3: Abilitare il supporto SSIS per AlwaysOn](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#Step3).  
  
  