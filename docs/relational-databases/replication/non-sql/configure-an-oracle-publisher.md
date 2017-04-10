---
title: "Configurazione di un server di pubblicazione Oracle | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pubblicazione Oracle [replica di SQL Server], configurazione"
ms.assetid: 240c8416-c8e5-4346-8433-07e0f779099f
caps.latest.revision: 60
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 60
---
# Configurazione di un server di pubblicazione Oracle
  La creazione di una pubblicazione nei server di pubblicazione Oracle avviene in maniera analoga al processo di creazione delle comuni pubblicazioni snapshot e transazionali, ma prima di poter effettivamente eseguire questo processo è necessario completare la procedura seguente (i primi quattro passaggi verranno descritti in dettaglio di seguito in questo argomento):  
  
1.  Creare un utente di amministrazione della replica nel database Oracle utilizzando l'apposito script.  
  
2.  Concedere direttamente, anziché tramite un ruolo, all'utente di amministrazione di Oracle creato nel passaggio 1 l'autorizzazione SELECT per ogni tabella che verrà pubblicata.  
  
3.  Installare il software client Oracle e il provider OLE DB nel [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] server di distribuzione e quindi arrestare e riavviare il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] istanza. Se il server di distribuzione viene eseguito su una piattaforma a 64 bit, è necessario utilizzare la versione a 64 bit del provider OLE DB Oracle.  
  
4.  Configurare il database Oracle come server di pubblicazione nel server di distribuzione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Per un elenco di oggetti che possono essere replicati da un database Oracle, vedere [Considerazioni sulla progettazione e limitazioni per server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/design-considerations-and-limitations-for-oracle-publishers.md).  
  
> [!NOTE]  
>  È necessario essere un membro del **sysadmin** ruolo predefinito del server per abilitare una pubblicazione o distribuzione e per creare una pubblicazione Oracle o una sottoscrizione da una pubblicazione Oracle.  
  
## Creazione di uno schema utente di amministrazione della replica all'interno del database Oracle  
 Gli agenti di replica si connettono al database Oracle e svolgono operazioni nel contesto di uno schema utente che deve essere appositamente creato. A questo schema devono essere concesse alcune autorizzazioni, elencate nella sezione successiva. Tutti gli oggetti creati dal proprietario di questo schema di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] processo di replica nel server di pubblicazione Oracle, fatta eccezione per un sinonimo public **MSSQLSERVERDISTRIBUTOR**. Per ulteriori informazioni sugli oggetti creati nel database Oracle, vedere [gli oggetti creati nel server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/objects-created-on-the-oracle-publisher.md).  
  
> [!NOTE]  
>  Eliminazione di **MSSQLSERVERDISTRIBUTOR** sinonimo public e l'utente di replica Oracle configurato con il **CASCADE** opzione rimuove tutti gli oggetti di replica dal server di pubblicazione Oracle.  
  
 È disponibile uno script di esempio che consente di agevolare la configurazione dello schema utente di replica Oracle. Lo script è disponibile nella directory seguente dopo l'installazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: *\< unità>*:\\\Programmi\Microsoft SQL Server\\*\< InstanceName>*\mssql\install\oracleadmin.SQL.. È anche incluso nell'argomento [Script per concedere le autorizzazioni di Oracle](../../../relational-databases/replication/non-sql/script-to-grant-oracle-permissions.md).  
  
 Connettersi al database Oracle utilizzando un account con privilegi DBA ed eseguire lo script. Lo script richiede l'indicazione del nome utente e della password per lo schema utente di amministrazione della replica e dello spazio tabella in cui creare gli oggetti (lo spazio tabella deve essere già disponibile nel database Oracle). Per informazioni su come specificare altri spazi tabella per gli oggetti, vedere [gestire spazi di tabella Oracle](../../../relational-databases/replication/non-sql/manage-oracle-tablespaces.md). Scegliere un nome utente e una password complessa e prenderne nota poiché verranno richiesti durante la configurazione del database Oracle come server di pubblicazione. È consigliabile utilizzare lo schema solo per gli oggetti necessari alla replica ed evitare di creare tabelle da pubblicare in questo schema.  
  
### Creazione manuale di uno schema utente  
 Se si crea manualmente uno schema utente di amministrazione della replica, è necessario concedere allo schema le autorizzazioni seguenti, in modo diretto o tramite un ruolo di database.  
  
-   CREATE PUBLIC SYNONYM e DROP PUBLIC SYNONYM  
  
-   CREATE PROCEDURE  
  
-   CREATE SEQUENCE  
  
-   CREATE SESSION  
  
 È inoltre necessario concedere direttamente le autorizzazioni seguenti all'utente (senza utilizzare un ruolo):  
  
-   CREATE ANY TRIGGER. È obbligatorio solo in caso di replica transazionale e snapshot.  
  
-   CREATE TABLE  
  
-   CREATE VIEW  
  
## Installazione e configurazione del software di rete client Oracle nel server di distribuzione SQL Server  
 È necessario installare e configurare il software di rete client Oracle e il provider OLE DB Oracle sul server di distribuzione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] affinché il server di distribuzione possa creare connessioni con il server di pubblicazione Oracle. Dopo aver installato il software, impostare le autorizzazioni appropriate per le cartelle in cui è installato il software e arrestare e riavviare l'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per garantire che tutte le impostazioni vengano aggiornate (le autorizzazioni verranno descritte di seguito nella sezione "Impostazione delle autorizzazioni per le directory").  
  
> [!NOTE]  
>  La versione del software di rete client Oracle deve essere aggiornata. È consigliabile installare l'ultima versione del software client. Per tale motivo, la versione del software client è spesso successiva a quella del software del database.  
  
 Il modo più diretto per installare e configurare il software di rete client consiste nell'utilizzare Oracle Universal Installer e Net Configuration Assistant dal disco del client Oracle.  
  
 In Oracle Universal Installer, è necessario inserire le informazioni seguenti:  
  
|Informazioni|Descrizione|  
|-----------------|-----------------|  
|Oracle Home|Percorso della directory di installazione del software Oracle. Accettare il percorso predefinito (C:\oracle\ora90 o simile) o inserirne un altro. Per ulteriori informazioni su Oracle Home, vedere la sezione relativa alle considerazioni su Oracle Home più avanti in questo argomento.|  
|Oracle home name|Alias del percorso di Oracle Home.|  
|Installation type|In Oracle 10g, selezionare il **amministratore** opzione di installazione.|  
  
 Dopo aver completato la procedura di Oracle Universal Installer, utilizzare Net Configuration Assistant per configurare la connettività di rete. È necessario indicare quattro informazioni per configurare la connettività di rete. L'amministratore del database Oracle definisce la configurazione di rete quando imposta il database e il listener e deve essere in grado di offrire queste informazioni se l'utente non le possiede. Eseguire le operazioni seguenti:  
  
|Azione|Descrizione|  
|------------|-----------------|  
|Identificazione del database|Per l'identificazione del database sono disponibili due modalità. La prima modalità utilizza il SID (Oracle System Identifier) ed è disponibile in ogni release di Oracle. La seconda utilizza il Service Name, disponibile a partire da Oracle 8.0. Entrambe le modalità utilizzano un valore configurato alla creazione del database ed è importante che la configurazione di rete del client utilizzi la stessa modalità di denominazione utilizzata dall'amministratore nella configurazione del listener per il database.|  
|Identificazione di un alias di rete per il database|È necessario specificare un alias di rete che verrà utilizzato per accedere al database Oracle. L'alias deve inoltre essere specificato quando si identifica il database Oracle come server di pubblicazione nel server di distribuzione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Si tratta in sostanza di un puntatore al Service Name o al SID remoto che è stato configurato quando è stato creato il database. Per l'alias di rete sono stati utilizzati diversi nomi nelle diverse release e nei diversi prodotti Oracle, tra cui Net Service Name e TNS Alias. SQL*Plus richiede questo alias come parametro "Host String" al momento dell'accesso.|  
|Selezione del protocollo di rete|Selezionare i protocolli appropriati che si desidera supportare. La maggioranza delle applicazioni utilizza il protocollo TCP.|  
|Inserimento dei dati host per identificare il listener del database|L'host è il nome o l'alias DNS del computer su cui viene eseguito il listener Oracle, in genere lo stesso computer contenente il database. Per alcuni protocolli è necessario indicare informazioni aggiuntive. Ad esempio, se si seleziona il protocollo TCP è necessario indicare la porta su cui il listener rimane in attesa di richieste di connessione al database di destinazione. La configurazione TCP predefinita utilizza la porta 1521.|  
  
### Impostazione delle autorizzazioni per le directory  
 All'account utilizzato per eseguire il servizio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sul server di distribuzione devono essere concesse autorizzazioni di lettura ed esecuzione per la directory e per tutte le relative sottodirectory in cui è installato il software di rete client Oracle.  
  
### Verifica della connettività tra il server di distribuzione SQL Server e il server di pubblicazione Oracle  
 Nei passaggi finali di Net Configuration Assistant può essere disponibile un'opzione che consente di testare la connessione al server di pubblicazione Oracle. Prima di verificare la connessione, verificare che l'istanza del database Oracle sia online e che il listener Oracle sia in esecuzione. Se la verifica non riesce, rivolgersi al DBA Oracle responsabile del database a cui si tenta di connettersi.  
  
 Dopo aver stabilito una connessione al server di pubblicazione Oracle, tentare di eseguire l'accesso al database utilizzando l'account e la password associati allo schema utente di amministrazione della replica creato. La procedura seguente deve essere eseguita utilizzando lo stesso account di Windows adoperato dal servizio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:  
  
1.  Fare clic su **avviare**, quindi fare clic su **eseguire**.  
  
2.  Tipo `cmd` e fare clic su **OK**.  
  
3.  Al prompt dei comandi digitare:  
  
     `sqlplus <UserSchemaLogin>/<UserSchemaPassword>@<NetServiceName>`  
  
     Esempio: `sqlplus replication/$tr0ngPasswerd@Oracle90Server`  
  
4.  Se la configurazione di rete è riuscita, sarà possibile accedere e verrà visualizzato il prompt `SQL`.  
  
5.  Se si verificano problemi di connessione al database Oracle, vedere la sezione "il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] server di distribuzione non può connettersi all'istanza del database Oracle" in [risoluzione dei problemi di server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/troubleshooting-oracle-publishers.md).  
  
### Considerazioni su Oracle Home  
 Oracle supporta l'installazione side-by-side di file binari dell'applicazione, ma la replica può utilizzare un solo set di file binari alla volta. Ogni set di file binari è associato a un Oracle Home; tali file si trovano nella directory %ORACLE_HOME%\bin. Quando la replica stabilisce le connessioni al server di pubblicazione Oracle è necessario verificare che venga utilizzato il set corretto di file binari, in particolare la versione più recente del software di rete client.  
  
 Accedere al server di distribuzione con gli account utilizzati dal servizio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e dal servizio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent e impostare le corrette variabili d'ambiente. La variabile %ORACLE_HOME% deve essere impostata in modo da fare riferimento al punto di installazione specificato quando è stato installato il software client di rete. %PATH% deve includere la directory %ORACLE_HOME% \bin come prima voce Oracle rilevata. Per informazioni sull'impostazione delle variabili d'ambiente, vedere la documentazione di Windows.  
  
## Configurazione del database Oracle come server di pubblicazione nel server di distribuzione SQL Server  
 Poiché i server di pubblicazione Oracle utilizzano sempre un server di distribuzione remoto, è necessario configurare un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] affinché funga da server di distribuzione per il server di pubblicazione Oracle (un server di pubblicazione Oracle può utilizzare un solo server di distribuzione, mentre un server di distribuzione può gestire più di un server di pubblicazione Oracle). Dopo aver configurato un server di distribuzione, identificare l'istanza di database Oracle come server di pubblicazione nel server di distribuzione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], Transact-SQL o RMO (Replication Management Objects). Per ulteriori informazioni sulla configurazione di un server di distribuzione, vedere [Configura distribuzione](../../../relational-databases/replication/configure-distribution.md).  
  
> [!NOTE]  
>  Il nome del server di pubblicazione Oracle non può essere identico a quello del relativo server di distribuzione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] o di alcun server di pubblicazione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] che utilizzi lo stesso server di distribuzione.  
  
 Quando si identifica il database Oracle come server di pubblicazione, è necessario scegliere un'opzione di pubblicazione Oracle: Complete o Oracle Gateway. Dopo aver identificato un server di pubblicazione, questa opzione può essere modificata solo eliminando e riconfigurando il server di pubblicazione. L'opzione Complete è progettata per offrire alle pubblicazioni snapshot e transazionali il set completo di funzionalità supportate per la pubblicazione Oracle. L'opzione Oracle Gateway prevede ottimizzazioni della progettazione specifiche per migliorare le prestazioni quando la replica funge da gateway tra i sistemi.  
  
 Dopo l'identificazione del server di pubblicazione Oracle nel server di distribuzione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], la replica crea un server collegato con nome identico a quello del servizio TNS del database Oracle. Tale server può essere utilizzato solo dalla replica. Se è necessario connettersi al server di pubblicazione Oracle tramite una connessione al server collegato, creare un altro nome del servizio TNS e quindi utilizzare tale nome quando si chiama [sp_addlinkedserver & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md).  
  
 Per configurare un server di pubblicazione Oracle e creare una pubblicazione, vedere [creare una pubblicazione da un Database Oracle](../../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md).  
  
## Vedere anche  
 [Considerazioni amministrative per i server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/administrative-considerations-for-oracle-publishers.md)   
 [Mapping dei tipi di dati per i server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)   
 [Glossario dei termini per la pubblicazione Oracle](../../../relational-databases/replication/non-sql/glossary-of-terms-for-oracle-publishing.md)   
 [Panoramica della pubblicazione Oracle](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)  
  
  