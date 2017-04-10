---
title: "Modificare la modalit&#224; di failover di una replica di disponibilit&#224; (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modalità di failover [SQL Server]"
  - "Gruppi di disponibilità [SQL Server], distribuzione"
  - "gruppi di disponibilità [SQL Server], modalità di failover"
  - "gruppi di disponibilità [SQL Server], configurazione"
ms.assetid: 619a826f-8e65-48eb-8c34-39497d238279
caps.latest.revision: 27
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 27
---
# Modificare la modalit&#224; di failover di una replica di disponibilit&#224; (SQL Server)
  Questo argomento illustra come modificare la modalità di failover di una replica di disponibilità in un gruppo di disponibilità Always On in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] o PowerShell. La modalità di failover è una proprietà della replica che determina la modalità di failover per le repliche eseguite nella modalità di disponibilità con commit sincrono. Per altre informazioni, vedere [Failover e modalità di failover&#40;gruppi di disponibilità Always On&#41;](../../../database-engine/availability-groups/windows/failover-and-failover-modes-always-on-availability-groups.md) e [Modalità di disponibilità &#40;gruppi di disponibilità Always On&#41;](../../../database-engine/availability-groups/windows/availability-modes-always-on-availability-groups.md).  
  
-   **Prima di iniziare:**  
  
     [Prerequisiti e restrizioni](#Prerequisites)  
  
     [Sicurezza](#Security)  
  
-   **Per modificare la modalità di disponibilità di una replica di disponibilità tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Prerequisites"></a> Prerequisiti e restrizioni  
  
-   Questa attività può essere eseguita solo sulle repliche primarie. È necessario essere connessi all'istanza del server che ospita la replica primaria.  
  
-   Le istanze del cluster di failover di SQL Server non supportano il failover automatico da gruppi di disponibilità, pertanto le replica di disponibilità ospitate da un'istanza del cluster di failover possono essere configurate solo per il failover manuale.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 È necessaria l'autorizzazione ALTER AVAILABILITY GROUP nel gruppo di disponibilità, l'autorizzazione CONTROL AVAILABILITY GROUP, l'autorizzazione ALTER ANY AVAILABILITY GROUP o l'autorizzazione CONTROL SERVER.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 **Per modificare la modalità di failover di una replica di disponibilità**  
  
1.  In Esplora oggetti connettersi all'istanza del server che ospita la replica primaria ed espandere l'albero del server.  
  
2.  Espandere il nodo **Disponibilità elevata Always On** e il nodo **Gruppi di disponibilità**.  
  
3.  Fare clic sul gruppo di disponibilità di cui si desidera modificare la replica.  
  
4.  Fare clic con il pulsante destro del mouse sulla replica e scegliere **Proprietà**.  
  
5.  Nella finestra di dialogo **Proprietà replica di disponibilità** utilizzare l'elenco a discesa **Modalità di failover** per modificare la modalità di failover di questa replica.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 **Per modificare la modalità di failover di una replica di disponibilità**  
  
1.  Connettersi all'istanza del server che ospita la replica primaria.  
  
2.  Utilizzare l'istruzione [ALTER AVAILABILITY GROUP](../../../t-sql/statements/alter-availability-group-transact-sql.md) , come indicato di seguito:  
  
     ALTER AVAILABILITY GROUP *nome_gruppo* MODIFY REPLICA ON '*nome_server*'  
  
     WITH ( {  
  
     AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT }  
  
     | FAILOVER_MODE = { AUTOMATIC | MANUAL }  
  
     }  )  
  
     dove  
  
    -   *nome_gruppo* è il nome del gruppo di disponibilità.  
  
    -   { '*_sistema*[\\*nome_istanza*]' | '*nome_rete_FCI*[\\*nome_istanza*]' }  
  
         Specifica l'indirizzo dell'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] che ospita la replica di disponibilità da modificare. I componenti di questo indirizzo sono i seguenti:  
  
         *nome_sistema*  
         Nome NetBIOS del computer in cui risiede un'istanza autonoma del server.  
  
         *nome_rete_FCI*  
         Nome di rete utilizzato per accedere a un cluster di failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in cui un'istanza del server di destinazione è un partner di failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
         *instance_name*  
         Nome dell'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] che ospita la replica di disponibilità di destinazione. Per un'istanza del server predefinita, *nome_istanza* è facoltativo.  
  
     Per altre informazioni su questi parametri, vedere [ALTER AVAILABILITY GROUP &#40; Transact-SQL &#41;](../../../t-sql/statements/alter-availability-group-transact-sql.md).  
  
     L'esempio seguente, relativo alla replica primaria del gruppo di disponibilità *MyAG* , mostra come impostare la modalità di failover automatico sulla replica di disponibilità situata in un'istanza del server predefinita in un computer denominato *COMPUTER01*.  
  
    ```  
    ALTER AVAILABILITY GROUP MyAG MODIFY REPLICA ON 'COMPUTER01' WITH  
       (FAILOVER_MODE = AUTOMATIC);  
    ```  
  
##  <a name="PowerShellProcedure"></a> Utilizzo di PowerShell  
 **Per modificare la modalità di failover di una replica di disponibilità**  
  
1.  Passare alla directory (**cd**) dell'istanza del server che ospita la replica primaria.  
  
2.  Usare il cmdlet **Set-SqlAvailabilityReplica** con il parametro **FailoverMode**. Quando si imposta una replica sul failover automatico, potrebbe essere necessario usare il parametro **AvailabilityMode** per impostare la replica sulla modalità di disponibilità con commit sincrono.  
  
     Ad esempio, con il comando seguente si modifica la replica `MyReplica` nel gruppo di disponibilità `MyAg` in modo da utilizzare la modalità di disponibilità con commit asincrono e supportare il failover automatico.  
  
    ```  
    Set-SqlAvailabilityReplica -AvailabilityMode "SynchronousCommit" -FailoverMode "Automatic" `   
    -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\Replicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  Per visualizzare la sintassi di un cmdlet, usare il cmdlet **Get-Help** nell'ambiente [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Per altre informazioni, vedere [Get Help SQL Server PowerShell](../../../relational-databases/scripting/get-help-sql-server-powershell.md).  
  
 **Per impostare e utilizzare il provider PowerShell per SQL Server**  
  
-   [Provider PowerShell per SQL Server](../../../relational-databases/scripting/sql-server-powershell-provider.md)  
  
## Vedere anche  
 [Panoramica di Gruppi di disponibilità Always On &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Modalità di disponibilità &#40;gruppi di disponibilità Always On&#41;](../../../database-engine/availability-groups/windows/availability-modes-always-on-availability-groups.md)   
 [Failover e modalità di failover &#40;gruppi di disponibilità Always On&#41;](../../../database-engine/availability-groups/windows/failover-and-failover-modes-always-on-availability-groups.md)  
  
  