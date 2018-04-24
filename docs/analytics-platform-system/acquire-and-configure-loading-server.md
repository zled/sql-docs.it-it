---
title: Acquisire e configurare un server di caricamento - Parallel Data Warehouse | Documenti Microsoft
description: In questo articolo viene descritto come acquisire e configurare un server durante il caricamento di un sistema di Windows non strumento per l'invio di caricamenti di dati per Parallel Data Warehouse (PDW).
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: a796616ad76ba62ea4174cf22c1517c489305055
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="acquire-and-configure-a-loading-server-for-parallel-data-warehouse"></a>Acquisire e configurare un server di caricamento per Parallel Data Warehouse
In questo articolo viene descritto come acquisire e configurare un server durante il caricamento di un sistema di Windows non strumento per l'invio di caricamenti di dati per Parallel Data Warehouse (PDW).  
  
## <a name="Basics"></a>Nozioni di base  
Il server di caricamento:  
  
-   Non è necessario essere un singolo server. È possibile caricare contemporaneamente più server di caricamento.  
  
-   Viene fornita e gestito dal proprio team IT. Potrebbe essere già presente uno o più server che può essere utilizzato per caricare dati in PDW.  
  
-   Si trova nel proprio rack non strumento e non può essere inserito all'interno del dispositivo di sistema della piattaforma Analitica.  
  
-   È connesso al dispositivo tramite la rete InfiniBand accessorio o over Ethernet. Per prestazioni ottimali, è consigliabile utilizzare InfiniBand.  
  
-   È nel proprio dominio del cliente, non il dominio applicazione. Non sussiste alcuna relazione di trust tra il dominio del cliente e il dominio applicazione.  
  
## <a name="Step1"></a>Passaggio 1: Determinare i requisiti di capacità  
Il caricamento del sistema può essere progettato come uno o più server di caricamento che eseguire caricamenti simultanei. Ogni server di caricamento non deve essere dedicata solo durante il caricamento, purché quest ' ultima gestirà i requisiti di archiviazione e delle prestazioni del carico di lavoro.  
  
I requisiti di sistema per un server di caricamento dipendono quasi completamente il proprio carico di lavoro. Utilizzare il [caricamento capacità pianificazione foglio di lavoro Server](loading-server-capacity-planning-worksheet.md) per determinare i requisiti di capacità.  
  
## <a name="Step2"></a>Passaggio 2: Acquisire la sServer  
Ora che è comprendere meglio i requisiti di capacità, è possibile pianificare i server e i componenti di rete che sarà necessario acquistare o effettuare il provisioning. Incorporare il seguente elenco di requisiti al piano di acquisto, quindi acquistare il server o effettuare il provisioning di un server esistente.  
  
### <a name="R"></a>Requisiti software  
Sistemi operativi supportati:  
  
-   Windows Server 2012 o Windows Server 2012 R2. Questi sistemi operativi richiedono la scheda di rete FDR.  
  
-   Windows Server 2008 R2. Questo sistema operativo richiede la scheda di rete DDR.  
  
Il server deve utilizzare le impostazioni locali EN-US per utilizzare lo strumento da riga di comando durante il caricamento dwloader. dwloader non supporta altre impostazioni locali.  
  
### <a name="networking-requirements-for-windows-server-2012-and-windows-server-2012-r2"></a>Requisiti di rete per Windows Server 2012 e Windows Server 2012 R2  
Sebbene non sia necessario per il caricamento, InfiniBand è il tipo di connessione consigliati per il caricamento di server. Per prestazioni ottimali, utilizzare la scheda di rete InfiniBand FDR o Windows Server 2012 R2 e Windows Server 2012 per connettere il server di caricamento per la rete InfiniBand dello strumento.  
  
Per preparare per una connessione di Windows Server 2012 o Windows Server 2012 R2 InfiniBand:  
  
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
  
5.  Configurare le impostazioni per le schede di rete InfiniBand e DNS. Per istruzioni sulla configurazione, vedere [schede di rete InfiniBand configurare](configure-infiniband-network-adapters.md).  
  
## <a name="Step4"></a>Passaggio 4: Installare gli strumenti di caricamento  
Gli strumenti Client sono disponibili per il download da Microsoft Download Center. 

Per installare dwloader, eseguire l'installazione di dwloader agli strumenti client.
  
Se si prevede di utilizzare Integration Services per il caricamento, è necessario installare Integration Services e gli adattatori di destinazione di Integration Services. Gli adattatori sono disponibili negli strumenti di Client.

<!-- To install the des[Install Integration Services Destination Adapters](install-integration-services-destination-adapters.md). 
--> 
  
## <a name="Step5"></a>Passaggio 5: Avviare il caricamento  
A questo punto si è pronti avviare il caricamento dei dati. Per altre informazioni, vedere:  
  
1.  [dwloader strumento durante il caricamento della riga di comando](dwloader.md)  
  
2.  [Panoramica di carico](load-overview.md)  
  
## <a name="performance"></a>restazioni  
Per ottenere migliori prestazioni in Windows Server 2012 e versioni successive di caricamento, attivare l'inizializzazione immediata dei File in modo che quando i dati vengono sovrascritti, il sistema operativo non sovrascrive i dati esistenti con zeri. Se si tratta di un rischio per la sicurezza perché sono ancora presenti dati precedenti sui dischi, quindi assicurarsi di disattivare l'inizializzazione immediata dei File.  
  
## <a name="Security"></a>Avvisi di sicurezza  
Poiché i dati da caricare non vengono archiviati nel dispositivo, il team IT è responsabile per la gestione di tutti gli aspetti di sicurezza per i dati da caricare. Ad esempio, include la gestione di protezione dei dati da caricare, la sicurezza del server utilizzato per archiviare i carichi e la sicurezza dell'infrastruttura di rete che connette il server di caricamento per il dispositivo di SQL Server PDW.  
  
> [!IMPORTANT]  
> È particolarmente importante per la protezione di ogni server di caricamento che verrà utilizzato lo strumento da riga di comando durante il caricamento di dwloader. Quando dwloader carica i dati, prima l'autenticazione con il nodo di controllo e quindi dopo l'autenticazione sposta dati dal server durante il caricamento direttamente ai nodi di calcolo attraverso i canali di dati. Convalida del certificato non viene eseguito durante l'agitazione mano tra i server di caricamento e ogni nodo di calcolo. In questo modo i nodi di calcolo esposti a potenziali attacchi man-in-the-middle su ogni canale di dati durante il caricamento. Questi attacchi potrebbe comportare dati manomessi e/o la divulgazione di informazioni.  
  
Per ridurre i rischi di sicurezza con i dati, si consiglia quanto segue:  
  
-   Specificare un account di Windows che viene utilizzato unicamente per il caricamento di dati in PDW. Consente questo account dispone delle autorizzazioni per il percorso di caricamento e non altrove.  
  
-   Designare un utente PDW che dispone delle autorizzazioni per caricare i dati. A seconda dei requisiti di sicurezza, è possibile che un utente specifico per ogni database.  
  
-   Operazioni nel server durante il caricamento possono accettare un percorso UNC da cui consente di estrarre dati dall'esterno della rete interna attendibile. Un utente malintenzionato sulla rete o con possibilità di influire sulla risoluzione dei nomi può intercettare o modificare i dati inviati a SQL Server PDW. Ciò rappresenta un rischio di divulgazione manomissioni e informazioni. Manomissione deve essere risolti tramite la richiesta di firma per la connessione. Per limitare questo rischio, impostare l'opzione di criteri di gruppo seguenti nel **protezione\Criteri Locali\opzioni di protezione** nel server durante il caricamento: **client di rete Microsoft: Aggiungi firma digitale alle comunicazioni (sempre): Abilitato**  
  
-   Disattivare l'inizializzazione immediata dei File in Windows Server 2012 e versioni successive. Si tratta di un compromesso tra prestazioni e sicurezza, come indicato nella sezione prestazioni. È necessario stabilire la soluzione migliore in base ai requisiti di sicurezza.  
  
## <a name="see-also"></a>Vedere anche  
[Panoramica di backup e ripristino](backup-and-restore-overview.md)  
  
