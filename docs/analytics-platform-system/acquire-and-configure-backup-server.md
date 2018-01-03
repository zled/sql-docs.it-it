---
title: Acquisire e configurare un Server di Backup per PDW APS
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: 
ms.technology: mpp-data-warehouse
description: "Configurare un sistema di Windows non strumento come un server di backup per l'utilizzo con il backup e ripristino funzionalità Analitica piattaforma di strumenti analitici e di SQL Server Parallel Data Warehouse (PDW)."
ms.date: 10/20/2016
ms.topic: article
caps.latest.revision: "20"
ms.assetid: f8b769fe-c864-4d65-abcb-a9a287061702
ms.openlocfilehash: 760537abd7e3227cc2245c429d0a0c13f7609f8b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="acquire-and-configure-a-backup-server"></a>Acquisire e configurare un server di backup
In questo argomento viene descritto come configurare un sistema di Windows non strumento come un server di backup per l'utilizzo con le funzionalità di backup e ripristino in Analitica piattaforma di strumenti analitici e di SQL Server Parallel Data Warehouse (PDW).  
  
  
## <a name="Basics"></a>Nozioni fondamentali sul server di backup  
Il server di backup:  
  
-   Viene fornita e gestito dal proprio team IT.  
  
-   Non richiede alcun strumenti software specifici PDW. PDW non viene installato alcun software sul server di backup.  
  
-   Si trova nel proprio rack non strumento e non può trovarsi all'interno dell'accessorio punti di accesso.  
  
-   Può essere connesso alla rete InfiniBand accessorio. I backup possono essere eseguiti su InfiniBand o Ethernet; InfiniBand è consigliato per motivi di prestazioni.  
  
-   È nel proprio dominio del cliente, non il dominio applicazione. Non sussiste alcuna relazione di trust tra il dominio del cliente e il dominio applicazione.  
  
-   Ospita una condivisione di file di backup, è una condivisione di file di Windows che utilizza il protocollo di rete a livello di applicazione Server Message Block (SMB). Le autorizzazioni di condivisione file di backup assegnano a un utente di dominio di Windows (in genere si tratta di un utente dedicato per il backup) la possibilità di eseguire backup e ripristino per la condivisione. Le credenziali di nome utente e password dell'utente di dominio di Windows vengono archiviate in PDW in modo che PDW è possibile eseguire backup e ripristinare le operazioni nella condivisione di file di backup.  
  
## <a name="Step1"></a>Passaggio 1: Determinare i requisiti di capacità  
I requisiti di sistema per il server di Backup dipendono quasi completamente il proprio carico di lavoro. Prima di acquisto o il provisioning di un server di backup è necessario stabilire i requisiti di capacità. Il server di Backup non deve essere dedicata solo ai backup, a condizione che gestirà i requisiti di archiviazione e delle prestazioni del carico di lavoro. È inoltre più server di backup per backup e ripristino di ogni database a uno dei diversi server.  
  
Utilizzare il [foglio di lavoro di pianificazione della capacità Backup server](backup-capacity-planning-worksheet.md) per determinare i requisiti di capacità.  
  
## <a name="Step2"></a>Passaggio 2: Ottenere il server di backup  
Ora che è comprendere meglio i requisiti di capacità, è possibile pianificare i server e i componenti di rete che sarà necessario acquistare o effettuare il provisioning. Incorporare il seguente elenco di requisiti al piano di acquisto, quindi acquistare il server o effettuare il provisioning di un server esistente.  
  
### <a name="software-requirements"></a>Requisiti software  
Qualsiasi file server che utilizza il protocollo di condivisione File di Windows (SMB).  
  
Si consiglia di Windows Server 2012 o oltre al fine di:  
  
-   Ottenere il miglioramento delle prestazioni di preallocazione di file su SMB.  
  
-   Utilizzare l'inizializzazione di File immediata (IFI) per le operazioni di backup. Il team IT gestisce questa impostazione nel server di backup. Gestione configurazione PDW (dwconfig.exe) non impostato o controllare IFI sul server di backup. Le versioni precedenti di Windows non dispone di IFI, ma possono comunque essere utilizzate come server di backup.  
  
### <a name="networking-requirements"></a>Requisiti di rete  
Sebbene non obbligatorio, InfiniBand è il tipo di connessione consigliati per i server di Backup. Per preparare per la connessione al server di caricamento alla rete InfiniBand dispositivo:  
  
1.  Pianificare il server rack abbastanza ravvicinati per il dispositivo in modo da consentire la connessione al dispositivo InfiniBand attiva. Per ulteriori informazioni dalle tecnologie Mellanox InfiniBand, vedere il white paper, [introduzione InfiniBand](http://www.mellanox.com/pdf/whitepapers/IB_Intro_WP_190.pdf).  
  
2.  Acquistare una scheda di rete InfiniBand FDR Mellanox ConnectX-3 porta singola o doppia. È consigliabile acquistare la scheda di rete con due porte per la tolleranza di errore durante la trasmissione dei dati. Una scheda di rete due porte è necessaria per la disponibilità elevata.  
  
3.  Acquistare cavi FDR InfiniBand 2 per una scheda a porta doppia o cavo FDR InfiniBand 1 per una scheda di singola porta. I cavi FDR InfiniBand si connetteranno il server di caricamento alla rete InfiniBand accessorio. La lunghezza del cavo dipende la distanza tra il server di caricamento e le opzioni di InfiniBand accessorio, in base al proprio ambiente.  
  
## <a name="Step3"></a>Passaggio 3: Connettere il server alle reti InfiniBand  
Usare questi passaggi per connettere il server di caricamento alla rete InfiniBand. Se il server non utilizza la rete InfiniBand, ignorare questo passaggio.  
  
1.  Rack server abbastanza ravvicinati per il dispositivo in modo che è possibile connettersi alla rete InfiniBand di dispositivo.  
  
2.  Installare la scheda di rete InfiniBand Mellanox ConnectX-3 FDR InfiniBand nel server durante il caricamento.  
  
3.  Utilizzare i cavi FDR per collegare una delle due opzioni InfiniBand nel rack accessorio prima la scheda di rete InfiniBand.  
  
4.  Installare e configurare il driver di Windows appropriato per la scheda di rete InfiniBand.  
  
    -   Driver InfiniBand per Windows vengono sviluppati da OpenFabrics Alliance, un consorzio di settore di fornitori InfiniBand.  Il driver corretto può distribuito con la scheda di rete InfiniBand. In caso contrario, il driver può essere scaricato da www.openfabrics.org.  
  
5.  Configurare le impostazioni per le schede di rete InfiniBand e DNS. Per istruzioni sulla configurazione, vedere [configurare schede di rete InfiniBand](configure-infiniband-network-adapters.md).  
  
## <a name="Step4"></a>Passaggio 4: Configurare la condivisione di file di backup  
PDW potranno accedere il server di backup tramite una condivisione file UNC. Per impostare la condivisione file:  
  
1.  Creare una cartella nel server di backup per l'archiviazione dei backup.  
  
2.  Creare una condivisione di file, la chiamata a una condivisione di backup, per la cartella di backup.  
  
3.  Definire o creare un account di dominio di Windows nel dominio cliente che si desidera utilizzare ai fini dell'esecuzione di backup e ripristini. Per motivi di sicurezza, è consigliabile utilizzare un account dedicato come l'utente per il backup.  
  
4.  Aggiungere le autorizzazioni per il backup condividono in modo che sia possibile accedere solo agli account attendibili e un account di dominio di backup, leggere e scrivere nel percorso di condivisione.  
  
5.  Aggiungere le credenziali dell'account di dominio di backup a PDW.  
  
    Ad esempio  
  
    ```sql  
    EXEC sp_pdw_add_network_credentials '10.192.147.63', 'seattle\david', '********';  
    ```  
  
    Per ulteriori informazioni, vedere queste stored procedure:  
  
    -   [sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md)  
  
    -   [sp_pdw_remove_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md)  
  
## <a name="Step5"></a>Passaggio 5: Avviare il backup dei dati  
A questo punto si è pronti avviare il backup dei dati al server di backup.  
  
Per il backup dei dati, utilizzare un client di query per connettersi a SQL Server PDW e inviare quindi i BACKUP del DATABASE o ripristinare DATABASE i comandi. Utilizzare il disco = clausola per specificare il percorso di backup e server di Backup.  
  
> [!IMPORTANT]  
> Ricordarsi di utilizzare l'indirizzo IP InfiniBand del server di backup. In caso contrario, verranno copiati i dati su Ethernet anziché InfiniBand.  
  
Ad esempio  
  
```sql  
BACKUP DATABASE Invoices TO DISK = '\\10.172.14.255\backups\yearly\Invoices2013Full';  
  
RESTORE DATABASE Invoices2013Full  
FROM DISK = '\\10.172.14.255\backups\yearly\Invoices2013Full'  
```  
  
Per altre informazioni, vedere: 
  
-   [DATABASE DI BACKUP](../t-sql/statements/backup-database-parallel-data-warehouse.md)   
  
-   [RIPRISTINO DI DATABASE](../t-sql/statements/restore-database-parallel-data-warehouse.md)  
  
## <a name="Security"></a>Avvisi di sicurezza  
Il server di backup non è unito al dominio privato per l'applicazione. È in rete e non vi è alcuna relazione di trust tra dominio e dominio accessorio privata.  
  
Poiché i backup PDW non sono archiviati nel dispositivo, il team IT è responsabile per la gestione di tutti gli aspetti della sicurezza del backup. Ad esempio, include la gestione della protezione di dati di backup, la sicurezza del server utilizzato per archiviare i backup e la sicurezza dell'infrastruttura di rete che si connette il server di backup per il dispositivo di punti di accesso.  
  
### <a name="manage-network-credentials"></a>Gestire le credenziali di rete  
  
Accesso alla rete per la directory di backup è basato su standard Windows condivisione file security. Prima di eseguire un backup, è necessario creare o designare un account di Windows che verrà utilizzato per l'autenticazione PDW alla directory di backup. Questo account di windows deve disporre dell'autorizzazione per accedere, creare e scrivere nella directory di backup.  
  
> [!IMPORTANT]  
> Per ridurre i rischi di sicurezza con i dati, è consigliabile che definisce un account di Windows solo scopo di operazioni di backup e di operazioni di ripristino. Consente questo account dispone delle autorizzazioni per il percorso di backup e non altrove.  
  
Per archiviare il nome utente e password in PDW, utilizzare il [sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md) stored procedure. PDW Usa Gestione credenziali di Windows per archiviare e crittografare i nomi utente e password nel nodo di controllo e nodi di calcolo. Le credenziali non vengono eseguito il backup con il comando BACKUP DATABASE.  
  
Per rimuovere le credenziali di rete da PDW, utilizzare il [sp_pdw_remove_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md) stored procedure.  
  
Per elencare tutte le credenziali di rete archiviate in SQL Server PDW, utilizzare il [sys.dm_pdw_network_credentials](../relational-databases/system-dynamic-management-views/sys-dm-pdw-network-credentials-transact-sql.md) vista a gestione dinamica.  
  
### <a name="secure-communications"></a>Proteggere le comunicazioni  
  
Operazioni nel server durante il caricamento è possono utilizzare un percorso UNC consente di estrarre dati dall'esterno della rete interna attendibile. Un utente malintenzionato sulla rete o con possibilità di influire sulla risoluzione dei nomi può intercettare o modificare i dati inviati a di PDW. Ciò rappresenta un rischio di divulgazione manomissioni e informazioni. Per aiutare a ridurre il rischio di manomissione:

- Richiedere la firma per la connessione. 
- Nel server di caricamento, impostare l'opzione di criteri di gruppo seguenti in protezione\Criteri Locali\opzioni di protezione: il client di rete Microsoft: Aggiungi firma digitale alle comunicazioni (sempre): abilitato.  
  
## <a name="see-also"></a>Vedere anche  
[Backup e ripristino](backup-and-restore-overview.md)  
  
