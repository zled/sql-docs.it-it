---
title: Configurazione dello strumento (Analitica piattaforma sistema)
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 064e7485-7026-4acf-8084-f5d30757d177
caps.latest.revision: "43"
ms.openlocfilehash: 05670f1727691b1abc0fd98dd5970c7697725b8e
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="appliance-configuration"></a>Configurazione di dispositivo
Fornisce elenchi di controllo per le attività necessarie per configurare il sistema di piattaforma Analitica per il proprio ambiente. Queste attività di configurazione sono necessari prima di poter usare il dispositivo.  
  
> [!WARNING]  
> Tramite il sistema di piattaforma Analitica**Configuration Manager** è il modo migliore, e l'unico modo, per eseguire le attività disponibili nello strumento è supportato.  
  
## <a name="BeforeTasks"></a>Prima di iniziare  
  
### <a name="prerequisites"></a>Prerequisites  
  
1.  Il dispositivo deve essere installato nel data center e attivato.  
  
2.  Assicurarsi di avere le informazioni seguenti, che viene fornite per il fornitore:  
  
    -   L'indirizzo IP esterno per il nodo controllo PDW (*PDW_region -*CTL01)  
  
    -   Nome di dominio di applicazione  
  
    -   Nome utente e password per l'amministratore di dominio del dispositivo  
  
3.  Ottenere un certificato attendibile. Questo viene importato in un passaggio successivo per consentire ai client di connettersi al **Console di amministrazione** con connessioni protette. Salvare il certificato al nodo di controllo in un file PFX protetto da password.  
  
4.  Avviare il **Configuration Manager**, eseguire le operazioni seguenti:  
  
    1.  Utilizzare **Desktop remoto** per connettersi al nodo di controllo PDW (*PDW_region*-CTL01). (Potrebbe essere necessario per la connessione con l'indirizzo IP esterno per CTL01)  
  
    2.  Avviare il **Configuration Manager** dal **avviare** rapida del nodo di controllo di PDW. La prima schermata di Configuration Manager consente di visualizzare la topologia del dispositivo, che è stata creata tramite il fornitore. È un elenco dei nodi hardware riconosciuto dal software di SQL Server PDW come parte del dispositivo. Non è necessario modificare le impostazioni nella schermata di topologia dello strumento.  
  
## <a name="CMTasks"></a>Eseguire attività di Configuration Manager  
SQL Server PDW**Configuration Manager** (PDWCM) è uno strumento di amministrazione accessorio che gli amministratori di sistema di SQL Server PDW utilizzano per eseguire operazioni a livello di dispositivo e per modificare le impostazioni a livello di dispositivo. Ad esempio, è possibile utilizzare PDWCM per reimpostare le password, impostare il fuso orario, modificare gli indirizzi IP, configurare i certificati SSL, abilitare l'accesso remoto attraverso il firewall, avviare o arrestare il dispositivo e impostare l'inizializzazione immediata dei File.  
  
Utilizzare **Configuration Manager** per eseguire attività di configurazione seguenti.  
  
|Attività di configurazione|Description|  
|----------------------|---------------|  
|Acquisire familiarità con i nomi di componenti fisici|[PDW e componenti fisici dell'infrastruttura di dispositivo &#40; Sistema della piattaforma Analitica &#41;](pdw-and-appliance-fabric-physical-components.md)|  
|Avviare Gestione configurazione di SQL Server PDW|[Avviare Gestione configurazione &#40; Sistema della piattaforma Analitica &#41;](launch-the-configuration-manager.md)|  
|Modificare la password di amministratore di dominio|Il dispositivo è un privato Windows Active Directory Domain Services che viene usato per autenticare i nodi all'interno del dispositivo.<br /><br />Il fornitore consente di impostare il dispositivo con una password di amministratore di dominio predefinito. Questa operazione deve essere modificato in una password sicura.<br /><br />Il **Configuration Manager** è supportato l'unico modo per modificare la password di amministratore di dominio.<br /><br />Per ulteriori informazioni, vedere [di reimpostazione della Password &#40; Sistema della piattaforma Analitica &#41; ](password-reset.md).|  
|Modificare la password per il **sa** accesso|SQL Server PDW è un accesso di amministratore di sistema denominato **sa**. Il **sa** accesso dispone di tutti i privilegi. Non è possibile concedere, negare o revocare qualsiasi autorizzazione. Inoltre possibile visualizzare tutte le viste di sistema.<br /><br />Per ulteriori informazioni, vedere [di reimpostazione della Password &#40; Sistema della piattaforma Analitica &#41; ](password-reset.md).|  
|Impostare il fuso orario del dispositivo|Impostare l'ora (locale o altri desiderato) per tutti i nodi dello strumento.<br /><br />Per ulteriori informazioni, vedere [configurazione del fuso orario dispositivo &#40; Sistema della piattaforma Analitica &#41; ](appliance-time-zone-configuration.md).|  
|Specificare le impostazioni di rete accessibile pubblicamente per l'applicazione di SQL Server PDW|[Configurazione di rete dispositivo &#40; Sistema della piattaforma Analitica &#41;](appliance-network-configuration.md)|  
|Importare un certificato di sicurezza per la Console di amministrazione|Un certificato può fornire le connessioni Secure Sockets Layer (SSL) su HTTPS per il [monitorare il dispositivo tramite la Console di amministrazione &#40; Sistema della piattaforma Analitica &#41; ](monitor-the-appliance-by-using-the-admin-console.md). Per impostazione predefinita, il **Console di amministrazione** include un certificato autofirmato che fornisce privacy, ma non l'autenticazione server. Questo certificato restituisce inoltre un errore in cui viene indicato di Internet Explorer: "Si verifica un problema con il certificato di sicurezza del sito Web" quando l'utente si connette. Anche se la connessione esegue la crittografia dei dati in transito tra il client e il server, la connessione è ancora al rischio di attacchi da.<br /><br />Gli amministratori di SQL Server PDW immediatamente devono acquisire un certificato concatenato a un'autorità di certificazione riconosciuta dai client, per avere una connessione protetta e rimuovere l'errore che segnala Internet Explorer. Ciò richiede un nome di dominio completo che esegue il mapping di indirizzo IP virtuale del nodo di controllo (scelta consigliata) o le barre di un nome di certificato che corrisponda al valore digitato dagli utenti, l'indirizzo del browser per accedere alla Console di amministrazione.<br /><br />Utilizzare il **Configuration Manager** per aggiungere o rimuovere certificati attendibili. Direttamente tramite lo strumento di configurazione certificato Microsoft Windows HTTP Services (`winHttpCertCfg.exe`) per gestire i certificati non è supportata.<br /><br />Per ulteriori informazioni, vedere [PDW Provisioning di certificati &#40; Sistema della piattaforma Analitica &#41; ](pdw-certificate-provisioning.md).|  
|Abilitare o disabilitare le regole di Windows Firewall che consentono o impediscono l'accesso a porte specifiche sullo strumento di SQL Server PDW.|Il fornitore verrà configurare e abilitare le regole del firewall necessarie per l'applicazione di funzionare correttamente. Nella maggior parte dei casi verranno Impossibile abilitare o disabilitare le regole del firewall.<br /><br />Per ulteriori informazioni, vedere [configurazione del Firewall PDW &#40; Sistema della piattaforma Analitica &#41; ](pdw-firewall-configuration.md).|  
|Avviare e arrestare il dispositivo di SQL Server PDW|Arresta o Avvia lo strumento di SQL Server PDW. Per ulteriori informazioni, vedere [PDW stato del servizio &#40; Sistema della piattaforma Analitica &#41; ](pdw-services-status.md).|  
|Verifica opzioni di inizializzazione immediata dei File utilizzando il **privilegi** la finestra di dialogo|Inizializzazione immediata dei File è una funzionalità di SQL Server che consente operazioni di file di dati eseguire più rapidamente. In SQL Server PDW è abilitata solo se l'account del servizio di rete è stato concesso il privilegio SE_MANAGE_VOLUME_NAME. È stato disattivato per impostazione predefinita.<br /><br />Per ulteriori informazioni, vedere [configurazione di inizializzazione File immediata &#40; Sistema della piattaforma Analitica &#41; ](instant-file-initialization-configuration.md).|  
|Ripristinare il database master da un backup|Elimina corrente **master** database e lo sostituisce con un backup. Per ulteriori informazioni, vedere [ripristinare il Master Database &#40; Sistema della piattaforma Analitica &#41; ](restore-the-master-database.md).|  
  
## <a name="AddTasks"></a>Eseguire attività di configurazione aggiuntive  
Dopo aver eseguito la **Configuration Manager** attività, eseguire il seguente elenco di attività di configurazione aggiuntive. Alcune di queste attività sono facoltativi.  
  
|Attività di configurazione|Description|  
|----------------------|---------------|  
|Il software antivirus di terze parti può essere installato e configurato nel dispositivo per esterni nodi SQL Server PDW.<br /><br />(Facoltativo)|Per ulteriori informazioni, vedere [Software Antivirus &#40; Sistema della piattaforma Analitica &#41; ](antivirus-software.md).|  
|La password per la modalità ripristino servizi directory può essere modificata.<br /><br />(Facoltativo)|Per ulteriori informazioni, vedere [imposta Password di amministratore per accedere a nodi di Active Directory in modalità ripristino servizi Directory &#40; modalità ripristino servizi directory &#41; &#40; Sistema della piattaforma Analitica &#41; ](set-admin-password-for-logging-on-to-ad-nodes-in-directory-services-restore-mode.md).|  
|Configurare il dispositivo per ricevere gli aggiornamenti software<br /><br />(Consigliato)|Il dispositivo deve essere configurato per ricevere gli aggiornamenti di SQL Server PDW e software sottostante.<br /><br />Per ulteriori informazioni, vedere [configurare Windows Server Update Services &#40; Windows Server Update Services &#41; &#40; Sistema della piattaforma Analitica &#41; ](configure-windows-server-update-services-wsus.md). Per informazioni su WSUS, vedere [Software manutenzione &#40; Sistema della piattaforma Analitica &#41; ](software-servicing.md).|  
|Configurare la connettività ai dati esterni, ad esempio Hadoop o Azure nell'archivio blob.<br /><br />(Facoltativo)|Per ulteriori informazioni, vedere [configurare la connettività di PolyBase per i dati esterni &#40; Sistema della piattaforma Analitica &#41; ](configure-polybase-connectivity-to-external-data.md).|  
|Configurare il Software Antivirus<br /><br />(Facoltativo)|Le soluzioni antivirus di terze parti può essere utilizzato per proteggere i nodi accessibile pubblicamente, ma non è obbligatorio. Seguire le istruzioni in.|  
|Configurare le schede di rete InfiniBand nel Backup e il caricamento dei server<br /><br />(Facoltativo)|Per configurare il Backup e il caricamento di server per connettersi a SQL Server PDW tramite la rete InfiniBand, è necessario configurare le schede di rete per consentire il dispositivo di DNS per risolvere la connessione InfiniBand alla rete InfiniBand attualmente attiva.|  
|Configurare per l'invio di dati di telemetria a Microsoft<br /><br />(Facoltativo)|Per configurare il sistema di piattaforma Analitica per inviare dati di telemetria a Microsoft, è necessario eseguire uno script di PowerShell nel nodo di controllo. Per istruzioni dettagliate, vedere [Invia commenti e suggerimenti dati di telemetria a Microsoft &#40; SQL Server PDW &#41; ](send-telemetry-feedback-to-microsoft-sql-server-pdw.md).|  
  
## <a name="see-also"></a>Vedere anche  
[Il Software antivirus &#40; Sistema della piattaforma Analitica &#41;](antivirus-software.md)  
[Configurare le schede di rete InfiniBand &#40; SQL Server PDW &#41;](configure-infiniband-network-adapters.md)  
  
