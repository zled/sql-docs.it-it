---
title: "Configurazione del Motore di database per l&#39;attesa su pi&#249; porte TCP | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "porte [SQL Server], multiple"
  - "TDS"
  - "attesa su più porte"
  - "endpoint [SQL Server], TDS"
  - "aggiunta di porte"
  - "flusso TDS (Tabular Data Stream, flusso di dati tabulare)"
  - "più porte"
ms.assetid: 8e955033-06ef-403f-b813-3d8241b62f1f
caps.latest.revision: 26
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 26
---
# Configurazione del Motore di database per l&#39;attesa su pi&#249; porte TCP
  In questo argomento viene illustrato come configurare il [!INCLUDE[ssDE](../../includes/ssde-md.md)] per l'ascolto su più porte TCP in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando Gestione configurazione SQL Server. Quando TCP/IP è abilitato per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il [!INCLUDE[ssDE](../../includes/ssde-md.md)] è in attesa delle connessioni in ingresso su un punto di connessione composto da un indirizzo IP e dal numero di porta TCP. Le procedure riportate di seguito consentono di creare un endpoint del flusso TDS, in modo che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] possa essere in ascolto su una porta TCP aggiuntiva.  
  
 Possibili motivi per la creazione di un secondo endpoint TDS:  
  
-   Aumentare la sicurezza configurando il firewall in modo da limitare l'accesso all'endpoint predefinito ai computer client locali in una subnet specifica. Mantenere l'accesso tramite Internet a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per il personale di supporto tecnico, creando un nuovo endpoint che il firewall espone a Internet e autorizzando la connessione all'endpoint al solo personale di supporto tecnico del server.  
  
-   Impostare l'affinità fra connessioni e processori specifici quando si utilizza la configurazione NUMA (Non-Uniform Memory Access).  
  
 La configurazione di un endpoint TDS include i passaggi seguenti, che possono essere eseguiti in qualsiasi ordine:  
  
-   Creare l'endpoint TDS per la porta TCP e ripristinare l'accesso all'endpoint predefinito, ove appropriato.  
  
-   Concedere l'accesso all'endpoint alle entità del server desiderate.  
  
-   Specificare il numero della porta TCP per l'indirizzo IP selezionato.  
  
 Per altre informazioni sulle impostazioni predefinite di Windows Firewall e per una descrizione delle porte TCP che interessano il motore di database, Analysis Services, Reporting Services e Integration Services, vedere [Configurare Windows Firewall per consentire l'accesso a SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
##  <a name="SSMSProcedure"></a>  
  
#### Per creare un endpoint TDS  
  
-   Eseguire l'istruzione seguente per creare un endpoint denominato **CustomConnection** per la porta 1500 per tutti gli indirizzi TCP disponibili nel server.  
  
    ```  
    USE master;  
    GO  
    CREATE ENDPOINT [CustomConnection]  
    STATE = STARTED  
    AS TCP  
       (LISTENER_PORT = 1500, LISTENER_IP =ALL)  
    FOR TSQL() ;  
    GO  
    ```  
  
 La creazione di un nuovo endpoint [!INCLUDE[tsql](../../includes/tsql-md.md)] comporta la revoca delle autorizzazioni di connessione **public** nell'endpoint TDS predefinito. Se per l'endpoint predefinito è necessario l'accesso al gruppo **public** , riapplicare l'autorizzazione utilizzando l'istruzione `GRANT CONNECT ON ENDPOINT::[TSQL Default TCP] to [public];` .  
  
#### Per concedere l'accesso all'endpoint  
  
-   Eseguire l'istruzione seguente per concedere l'accesso all'endpoint **CustomConnection** al gruppo SQLSupport nel dominio aziendale.  
  
    ```  
    GRANT CONNECT ON ENDPOINT::[CustomConnection] to [corp\SQLSupport] ;  
    GO  
    ```  
  
#### Per configurare il Motore di database di SQL Server per l'attesa su una porta TCP aggiuntiva  
  
1.  In Gestione configurazione SQL Server espandere **Configurazione di rete SQL Server** e quindi fare clic su **Protocolli per***<nome_istanza>*.  
  
2.  Espandere **Protocolli per*** <nome_istanza>* e quindi fare clic su **TCP/IP**.  
  
3.  Nel riquadro di destra, fare clic con il pulsante destro del mouse sugli indirizzi IP disabilitati da attivare, quindi scegliere **lita**.  
  
4.  Fare clic con il pulsante destro del mouse su **IPAll** e quindi scegliere **Proprietà**.  
  
5.  Nella casella **Porta TCP** digitare le porte sulle quali si desidera che [!INCLUDE[ssDE](../../includes/ssde-md.md)] resti in attesa, separate da virgole. Nell'esempio, se è elencata la porta predefinita 1433, digitare **,1500** in modo che il valore nella casella sia **1433,1500**e quindi fare clic su **OK**.  
  
    > [!NOTE]  
    >  Se non si sta abilitando la porta su tutti gli indirizzi IP, configurare la porta aggiuntiva nella casella delle proprietà per il solo indirizzo desiderato. Nel riquadro della console fare quindi clic con il pulsante destro del mouse su **TCP/IP**, scegliere **Proprietà** e nella casella **Attesa su tutti** selezionare **No**.  
  
6.  Nel riquadro di sinistra fare clic su **Servizi di SQL Server**.  
  
7.  Nel riquadro di destra fare clic con il pulsante destro del mouse su **SQL Server***<nome_istanza>* e quindi scegliere **Riavvia**.  
  
     Dopo il riavvio di [!INCLUDE[ssDE](../../includes/ssde-md.md)], il log degli errori conterrà l'elenco delle porte sulle quali [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in attesa.  
  
#### Per eseguire la connessione al nuovo endpoint  
  
-   Per eseguire la connessione all'endpoint **CustomConnection** dell'istanza predefinita di SQL Server nel server ACCT, usando una connessione trusted e supponendo che l'utente sia membro del gruppo [corp\SQLSupport], eseguire questa istruzione.  
  
    ```  
    sqlcmd -SACCT,1500  
    ```  
  
## Vedere anche  
 [CREATE ENDPOINT &#40;Transact-SQL&#41;](../../t-sql/statements/create-endpoint-transact-sql.md)   
 [DROP ENDPOINT &#40;Transact-SQL&#41;](../../t-sql/statements/drop-endpoint-transact-sql.md)   
 [GRANT - autorizzazioni per endpoint &#40;Transact-SQL&#41;](../../t-sql/statements/grant-endpoint-permissions-transact-sql.md)   
 [Eseguire il mapping delle porte TCP/IP ai nodi NUMA &#40;SQL Server&#41;](../../database-engine/configure-windows/map-tcp-ip-ports-to-numa-nodes-sql-server.md)  
  
  