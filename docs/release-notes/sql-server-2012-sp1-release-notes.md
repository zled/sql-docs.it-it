---
title: Note sulla versione di SQL Server 2012 SP1 | Microsoft Docs
ms.prod: sql-server-2012
ms.technology: server-general
ms.custom: 
ms.date: 01/31/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72171357-28de-4edd-bdfd-194f97225a6f
caps.latest.revision: 49
author: byham
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 47cba5e99626a7b378c29a9dde4923963fae09da
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-2012-sp1-release-notes"></a>SQL Server 2012 SP1 Release Notes
Nel presente documento Note sulla versione vengono descritti i problemi noti di cui è necessario essere a conoscenza prima di installare o risolvere i problemi relativi a [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Service Pack 1. Questo documento è disponibile solo online, non nei supporti di installazione, e viene aggiornato periodicamente.  
  
## <a name="bkmk_top"></a>Sommario  
[1.0 Prima di installare](#bmk_Install)  
  
[2.0 Analysis Services e PowerPivot](#bkmk_AS)  
  
[3.0 Reporting Services](#bkmk_RS)  
  
[4.0 Data Quality Services](#bkmk_DQS)  
  
[5.0 SQL Server Express](#bkmk_Express)  
  
[6.0 Servizio Change Data Capture e Designer per Oracle di Attunity](#bkmk_CDC)  
  
[7.0 SQL Server Data-Tier Application Framework (DACFx)](#DACFx)  
  
[8.0 Problemi noti risolti in questo Service Pack](#bkmk_known_issues_fixed)  
  
## <a name="bmk_Install"></a>1.0 Prima di installare  
Prima di installare SQL Server 2012 SP1, si considerino le informazioni riportate di seguito.  
  
### <a name="11-reinstalling-an-instance-of-sql-server-failover-custer-fails-if-you-use-the-same-ip-address"></a>1.1 La reinstallazione di un'istanza del cluster di failover di SQL Server non viene completata se si utilizza lo stesso indirizzo IP  
**Problema:** se si specifica un indirizzo IP non corretto durante un'installazione di un'istanza del cluster di failover di SQL Server, l'installazione non riesce. Dopo la disinstallazione dell'istanza con errori, e in caso di tentativo di reinstallazione dell'istanza del cluster di failover di SQL Server con lo stesso nome istanza, e indirizzo IP corretto, l'installazione non viene completata. L'errore è dovuto al gruppo di risorse duplicate lasciato dall'installazione precedente.  
  
**Soluzione alternativa:** per risolvere il problema, utilizzare un nome istanza diverso durante la reinstallazione oppure eliminare manualmente il gruppo di risorse prima della reinstallazione. Per altre informazioni, vedere la pagina relativa all' [aggiunta o alla rimozione di nodi in un cluster di failover di SQL Server](http://msdn.microsoft.com/library/ms191545).  
  
### <a name="12-choose-the-correct-file-to-download-and-install"></a>1.2 Scegliere il file corretto da scaricare e installare  
Fare riferimento alla tabella seguente per determinare il file da scaricare e installare. Verificare di disporre dei requisiti di sistema corretti prima di installare il Service Pack. I requisiti di sistema sono indicati nelle pagine di download di cui viene fornito il collegamento all'interno della tabella.  
  
|Versione attualmente installata|Operazione da eseguire|File da scaricare e installare|  
|-------------------------------------------|----------------------|---------------------------|  
|**Installazioni a&amp;32; bit:**|||  
|Versione a 32 bit di qualsiasi edizione di SQL Server 2012|Eseguire l'aggiornamento alla versione a 32 bit di SQL Server 2012 SP1|SQLServer2012SP1-KB2674319-x86-ENU.exe in [questa pagina](http://go.microsoft.com/fwlink/p/?LinkID=268158)|  
|Versione a 32 bit di SQL Server 2012 RTM Express|Eseguire l'aggiornamento alla versione a 32 bit di SQL Server 2012 Express SP1|SQLServer2012SP1-KB2674319-x86-ENU.exe in [questa pagina](http://go.microsoft.com/fwlink/p/?LinkID=268158)|  
|Versione a 32 bit solo degli strumenti client e di gestibilità per SQL Server 2012 (incluso SQL Server 2012 Management Studio)|Eseguire l'aggiornamento degli strumenti client e di gestibilità alla versione a 32 bit di SQL Server 2012 SP1|SQLManagementStudio_x86_ENU.exe in [questa pagina](http://go.microsoft.com/fwlink/p/?LinkID=267905)|  
|Versione a 32 bit di SQL Server 2012 Management Studio Express|Eseguire l'aggiornamento alla versione a 32 bit di SQL Server 2012 SP1 Management Studio Express|SQLManagementStudio_x86_ENU.exe in [questa pagina](http://go.microsoft.com/fwlink/p/?LinkID=267905)|  
|Versione a 32 bit di qualsiasi edizione di SQL Server 2012 **e** versione a 32 bit degli strumenti client e di gestibilità (incluso SQL Server 2012 RTM Management Studio)|Eseguire l'aggiornamento di tutti i prodotti alla versione a 32 bit di SQL Server 2012 SP1|SQLServer2012SP1-KB2674319-x86-ENU.exe in [questa pagina](http://go.microsoft.com/fwlink/p/?LinkID=268158)|  
|Versione a 32 bit di uno o più strumenti di [Microsoft SQL Server 2012 RTM Feature Pack](http://www.microsoft.com/download/details.aspx?id=16978)|Eseguire l'aggiornamento degli strumenti alla versione a 32 bit di Microsoft SQL Server 2012 SP1 Feature Pack|Uno o più file di [Microsoft SQL Server 2012 SP1 Feature Pack](http://go.microsoft.com/fwlink/p/?LinkID=268266)|  
|Nessuna installazione a 32 bit di SQL Server 2012|Installare SQL Server 2012 a 32 bit con SP1 (nuova istanza con SP1 preinstallato)|SQLServer2012SP1-FullSlipstream-x86-ENU.exe **e** SQLServer2012SP1-FullSlipstream-x86-ENU.box in [questa pagina](http://go.microsoft.com/fwlink/p/?LinkID=268158)|  
|Nessuna installazione a 32 bit di SQL Server 2012 Management Studio|Installare SQL Server 2012 Management Studio a 32 bit con SP1|SQLManagementStudio_x86_ENU.exe in [questa pagina](http://go.microsoft.com/fwlink/p/?LinkId=267905)|  
|Nessuna versione a 32 bit di SQL Server 2012 RTM Express|Installare SQL Server 2012 Express a 32 bit con SP1|SQLEXPR32_x86_ENU.exe in [questa pagina](http://go.microsoft.com/fwlink/p/?LinkId=267905)|  
|Installazione a 32 bit di **SQL Server 2008** o **SQL Server 2008 R2**|**Aggiornamento sul posto** a SQL Server 2012 a 32 bit con SP1|SQLServer2012SP1-FullSlipstream-x86-ENU.exe **e** SQLServer2012SP1-FullSlipstream-x86-ENU.box in [questa pagina](http://go.microsoft.com/fwlink/p/?LinkID=268158)|  
|**Installazioni a&amp;64; bit:**|||  
|Versione a 64 bit di qualsiasi edizione di SQL Server 2012|Eseguire l'aggiornamento alla versione a 64 bit di SQL Server 2012 SP1|SQLServer2012SP1-KB2674319-x64-ENU.exe in [questa pagina](http://go.microsoft.com/fwlink/p/?LinkID=268158)|  
|Versione a 64 bit di SQL Server 2012 RTM Express|Eseguire l'aggiornamento alla versione a 64 bit di SQL Server 2012 SP1|SQLServer2012SP1-KB2674319-x64-ENU.exe in [questa pagina](http://go.microsoft.com/fwlink/p/?LinkID=268158)|  
|Versione a 64 bit solo degli strumenti client e di gestibilità per SQL Server 2012 (incluso SQL Server 2012 Management Studio)|Eseguire l'aggiornamento degli strumenti client e di gestibilità alla versione a 64 bit di SQL Server 2012 SP1|SQLManagementStudio_x64_ENU.exe in [questa pagina](http://go.microsoft.com/fwlink/p/?LinkID=267905)|  
|Versione a 64 bit di SQL Server 2012 Management Studio Express|Eseguire l'aggiornamento alla versione a 64 bit di SQL Server 2012 SP1 Management Studio Express|SQLManagementStudio_x64_ENU.exe in [questa pagina](http://go.microsoft.com/fwlink/p/?LinkID=267905)|  
|Versione a 64 bit di qualsiasi edizione di SQL Server 2012 **e** versione a 64 bit degli strumenti client e di gestibilità (incluso SQL Server 2012 RTM Management Studio)|Eseguire l'aggiornamento di tutti i prodotti alla versione a 64 bit di SQL Server 2012 SP1|SQLServer2012SP1-KB2674319-x64-ENU.exe in [questa pagina](http://go.microsoft.com/fwlink/p/?LinkID=268158)|  
|Versione a 64 bit di uno o più strumenti di [Microsoft SQL Server 2012 RTM Feature Pack](http://www.microsoft.com/download/en/details.aspx?id=16978)|Eseguire l'aggiornamento degli strumenti alla versione a 64 bit di Microsoft SQL Server 2012 SP1 Feature Pack|Uno o più file di [Microsoft SQL Server 2012 SP1 Feature Pack](http://go.microsoft.com/fwlink/p/?LinkID=268266)|  
|Nessuna installazione a 64 bit di SQL Server 2012|Installare SQL Server 2012 a 64 bit con SP1 (nuova istanza con SP1 preinstallato)|SQLServer2012SP1-FullSlipstream-x64-ENU.exe **e** SQLServer2012SP1-FullSlipstream-x64-ENU.box in [questa pagina](http://go.microsoft.com/fwlink/p/?LinkID=268158)|  
|Nessuna installazione a 64 bit di SQL Server 2012 Management Studio|Installare SQL Server 2012 Management Studio a 64 bit con SP1|SQLManagementStudio_x64_ENU.exe in [questa pagina](http://go.microsoft.com/fwlink/p/?LinkID=267905)|  
|Nessuna versione a 64 bit di SQL Server 2012 RTM Express|Installare SQL Server 2012 Express a 64 bit con SP1|SQLEXPR_x64_ENU.exe in [questa pagina](http://go.microsoft.com/fwlink/p/?LinkID=267905)|  
|Installazione a 64 bit di **SQL Server 2008** o **SQL Server 2008 R2**|**Aggiornamento sul posto** a SQL Server 2012 a 64 bit con SP1|SQLServer2012SP1-FullSlipstream-x64-ENU.exe **e** SQLServer2012SP1-FullSlipstream-x64-ENU.box in [questa pagina](http://go.microsoft.com/fwlink/p/?LinkID=268158)|  
  
![Icona freccia usata con il collegamento Torna all'inizio](../release-notes/media/uparrow16x16.gif "Icona freccia usata con il collegamento Torna all'inizio")[Sommario](#bkmk_top)  
  
## <a name="bkmk_AS"></a>2.0 Analysis Services e PowerPivot  
  
### <a name="21-powerpivot-configuration-tool-does-not-create-the-powerpivot-gallery"></a>2.1 Tramite lo strumento di configurazione PowerPivot non viene creata la raccolta PowerPivot  
**Problema:** tramite lo strumento di configurazione PowerPivot viene eseguito il provisioning del sito di un team, pertanto non viene creata alcuna raccolta PowerPivot.  
  
**Soluzione alternativa:** creare una nuova applicazione (libreria).  
  
1.  Verificare che la funzionalità per le raccolte siti **Integrazione della funzionalità di PowerPivot per le raccolte siti** sia attiva.  
  
2.  Nella pagina **Contenuto sito** di un sito esistente fare clic su **Aggiungi applicazione**.  
  
3.  Fare clic su **Raccolta PowerPivot**.  
  
### <a name="22-to-use-powerpivot-for-excel-with-excel-2013-you-must-use-the-add-in-that-is-installed-with-excel"></a>2.2 Per utilizzare PowerPivot per Excel con Excel 2013, è necessario utilizzare il componente aggiuntivo installato con Excel  
**Problema:** con Office 2010, PowerPivot per Excel è un componente aggiuntivo autonomo che può essere scaricato da [http://www.microsoft.com/bi/powerpivot.aspx](http://www.microsoft.com/bi/powerpivot.aspx). In alternativa, può essere scaricato anche dall' [Area download Microsoft](http://www.microsoft.com/download/details.aspx?id=29074). Si noti che sono disponibili due versioni del componente aggiuntivo PowerPivot: una fornita con SQL Server 2008 R2 e un'altra con SQL Server 2012. Tuttavia, per Office 2013, PowerPivot per Excel viene fornito con Office e viene installato insieme a Excel. Anche se le versioni SQL Server 2008 R2 e SQL Server 2012 di PowerPivot per Excel 2010 non sono compatibili con Excel 2013, è comunque possibile installare PowerPivot per Excel 2010 nel computer client se si desidera un'esecuzione side-by-side di Excel 2010 ed Excel 2013. In altre parole, le due versioni di Excel possono coesistere, così come i componenti aggiuntivi PowerPivot corrispondenti.  
  
**Soluzione alternativa:** per usare PowerPivot per Excel 2013 è necessario abilitare il componente aggiuntivo COM. In Excel 2013 selezionare **File** | **Opzioni** | **Componenti aggiuntivi**. Nella casella di riepilogo a discesa **Gestisci** selezionare **Componenti aggiuntivi COM** e fare clic su **Vai**. In **Componenti aggiuntivi COM**selezionare **Microsoft Office PowerPivot for Excel 2013** e fare clic su **OK**.  
  
![Icona freccia usata con il collegamento Torna all'inizio](../release-notes/media/uparrow16x16.gif "Icona freccia usata con il collegamento Torna all'inizio")[Sommario](#bkmk_top)  
  
## <a name="bkmk_RS"></a>3.0 Reporting Services  
  
### <a name="31-install-and-configure-sharepoint-server-2013-prior-to-installing-reporting-services"></a>3.1 Installare e configurare SharePoint Server 2013 prima di installare Reporting Services  
**Problema:** completare le operazioni richieste seguenti **prima** di installare SQL Server Reporting Services (SSRS).  
  
1.  Eseguire l'Utilità preparazione prodotti SharePoint 2013.  
  
2.  Installare SharePoint Server 2013.  
  
3.  Eseguire la Configurazione guidata del prodotto SharePoint 2013 o completare un set equivalente di passaggi di configurazione per configurare la farm di SharePoint.  
  
**Soluzione alternativa:**  se è stata installata la modalità SharePoint di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] prima che la farm di SharePoint venisse configurata, la soluzione alternativa richiesta dipenderà dagli altri componenti installati.  
  
### <a name="32-power-view-in-sharepoint-server-2013-requires-microsoftanalysisservicesspclientdll"></a>3.2 Per Power View in SharePoint Server 2013 è richiesto il file Microsoft.AnalysisServices.SPClient.dll  
**Problema:** [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] non installa un componente obbligatorio, ovvero **Microsoft.AnalysisServices.SPClient.dll**. Se si installano SharePoint Server 2013 Preview e [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in modalità SharePoint ma non si scarica né si installa il pacchetto di installazione di PowerPivot per SharePoint 2013, **spPowerPivot.msi**, Power View non funzionerà e verranno mostrati i sintomi riportati di seguito.  
  
**Sintomi:** quando si tenta di creare un report Power View, viene visualizzato un messaggio di errore simile al seguente:  
  
-   "Impossibile creare una connessione all'origine dei dati...''  
  
Nei dettagli interni dell'errore sarà presente un messaggio simile al seguente:  
  
-   "Il valore 'SharePoint Principal' non è supportato per la proprietà della stringa di connessione 'User Identity'".  
  
**Soluzione alternativa:** installare il pacchetto di installazione di PowerPivot per SharePoint 2013 (**spPowerPivot.msi**) in SharePoint Server 2013. Il pacchetto di installazione è disponibile come parte del Feature Pack di [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] . Il Feature Pack può essere scaricato dall'Area Download [!INCLUDE[msCoName](../includes/msconame-md.md)] in corrispondenza di [SQL Server 2012 SP1 Feature Pack](http://go.microsoft.com/fwlink/p/?LinkID=268266).  
  
### <a name="33-power-view-sheets-in-a-powerpivot-workbook-are-deleted-after-a-scheduled-data-refresh"></a>3.3 I fogli di Power View in una cartella di lavoro di PowerPivot vengono eliminati dopo un aggiornamento dati pianificato  
**Problema**: nel componente aggiuntivo PowerPivot per SharePoint l'uso di **Scheduled Data Refresh** in una cartella di lavoro con Power View comporterà l'eliminazione di tutti i fogli di Power View.  
  
**Soluzione alternativa**: per utilizzare **Scheduled Data Refresh** con cartelle di lavoro di Power View, creare una cartella di lavoro di PowerPivot come modello di dati. Creare una cartella di lavoro separata con i fogli di Excel e di Power View tramite cui è possibile collegarsi alla cartella di lavoro di PowerPivot con il modello di dati. È consigliabile pianificare per l'aggiornamento dati solo la cartella di lavoro di PowerPivot con il modello di dati.  
  
## <a name="bkmk_DQS"></a>4.0 Data Quality Services  
  
### <a name="41-dqs-available-in-the-incorrect-edition-of-sql-server-2012"></a>4.1 DQS disponibile nell'edizione errata di SQL Server 2012  
**Problema:** nella versione [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] RTM la funzionalità Data Quality Services (DQS) è disponibile nelle edizioni di SQL Server diverse da Enterprise, Business Intelligence e Developer. Dopo aver installato SQL Server 2012 SP1, DQS non sarà disponibile in alcuna edizione, ad eccezione di Enterprise, Business Intelligence e Developer.  
  
**Soluzione alternativa**: se DQS viene utilizzato in un'edizione non supportata, eseguire l'aggiornamento a un'edizione supportata o rimuovere dalle applicazioni la dipendenza da questa funzionalità.  
  
![Icona freccia usata con il collegamento Torna all'inizio](../release-notes/media/uparrow16x16.gif "Icona freccia usata con il collegamento Torna all'inizio")[Sommario](#bkmk_top)  
  
## <a name="bkmk_Express"></a>5.0 SQL Server Express  
  
### <a name="51-full-version-of-sql-server-management-studio-available-in-sql-server-2012-express-sp1"></a>5.1 Versione completa di SQL Server Management Studio disponibile in SQL Server 2012 Express SP1  
Nella versione SQL Server 2012 Express Service Pack 1 (SP1) è inclusa la versione completa di SQL Server 2012 Management Studio (che in precedenza era disponibile solo nel DVD di SQL Server 2012), anziché SQL Server 2012 Management Studio Express. Per scaricare e installare SQL Server 2012 Express SP1, vedere la pagina relativa a [SQL Server 2012 Express Service Pack 1](http://go.microsoft.com/fwlink/p/?linkid=267905).  
  
![Icona freccia usata con il collegamento Torna all'inizio](../release-notes/media/uparrow16x16.gif "Icona freccia usata con il collegamento Torna all'inizio")[Sommario](#bkmk_top)  
  
## <a name="bkmk_CDC"></a>6.0 Servizio Change Data Capture e Designer per Oracle di Attunity  
  
### <a name="61-upgrading-the-cdc-service-and-designer"></a>6.1 Aggiornamento di CDC Service e Designer  
**Problema:** se Change Data Capture Designer per Oracle e Change Data Capture Service per Oracle di Attunity sono presenti nel computer quando si installa SQL Server 2012 SP1, questi componenti non vengono aggiornati dall'installazione di SP1.  
  
**Soluzione alternativa:** per aggiornare i componenti CDC alla versione più recente:  
  
1.  Scaricare i file con estensione msi per Change Data Capture Service per Oracle di Attunity dalla pagina di download di [SQL Server 2012 SP1 Feature Pack](http://go.microsoft.com/fwlink/p/?LinkID=268266).  
  
2.  Eseguire il file con estensione msi.  
  
![Icona freccia usata con il collegamento Torna all'inizio](../release-notes/media/uparrow16x16.gif "Icona freccia usata con il collegamento Torna all'inizio")[Sommario](#bkmk_top)  
  
## <a name="DACFx"></a>7.0 SQL Server Data-Tier Application Framework (DACFx)  
**Supporto dell'aggiornamento sul posto**  
  
Questa versione di Data-Tier Application Framework (DACFx) supporta l'aggiornamento sul posto delle versioni precedenti, pertanto non è necessario rimuovere le installazioni precedenti di DACFx prima di eseguire l'aggiornamento a questa versione. Le versioni future di DACFx sono disponibili [qui](https://msdn.microsoft.com/library/dn702988.aspx).  
  
**Supporto per Indice XML selettivo**  
  
In SQL Server 2012 SP1 è incluso il supporto per [Indice XML selettivo (SXI)](http://msdn.microsoft.com/en-us/598ecdcd-084b-4032-81b2-eed6ae9f5d44), una nuova funzionalità di SQL Server che fornisce una nuova modalità di indicizzazione della colonna XML con efficienza e prestazioni migliorate.  
  
DACFx supporta ora gli indici SXI in tutti gli strumenti client e scenari di applicazione livello dati. SXI è supportato solo nell'ultima versione di SSDT, non è supportato nelle versioni SSDT RTM e di settembre 2012.  
  
**Supporto per il formato dati BCP nativo**  
  
JSON è stato il formato dati utilizzato in precedenza per archiviare i dati della tabella in pacchetti DACPAC e BACPAC. Con questo aggiornamento, BCP nativo è ora il formato di persistenza dei dati. Grazie a questa modifica è possibile migliorare la compatibilità del tipo di dati di SQL Server a DACFx in cui sono inclusi il supporto per i tipi SQL_Variant, nonché prestazioni di distribuzione avanzate per database in larga scala.  
  
**Mantenimento dello stato del vincolo CHECK nella creazione/distribuzione del pacchetto**  
  
In precedenza, tramite DACFx non è stato possibile mantenere lo stato (WITH CHECK/NOCHECK) dei vincoli CHECK definiti nelle tabelle dello schema del database, né archiviare queste informazioni nei file DACPAC. Tramite questo comportamento è possibile la generazione di problemi relativi alla distribuzione del pacchetto qualora vengano violati i vincoli CHECK dai dati della tabella esistente. Con questo aggiornamento, tramite DACFx è ora possibile archiviare lo stato corrente dei vincoli CHECK nel file DACPAC quando estratti da un database e viene ripristinato in modo appropriato questo stato alla distribuzione del pacchetto.  
  
**Aggiornamenti a SqlPackage.exe (strumento della riga di comando di DACFx)**  
  
-   Estrarre DACPAC con dati. Viene creato un file di snapshot di database (con estensione dacpac) da un database SQL di Windows Azure o SQL Server attivo contenente dati da tabelle utente, oltre allo schema del database. Questi pacchetti possono essere pubblicati in un nuovo database SQL di Windows Azure o SQL Server esistente tramite l'azione Pubblica di SqlPackage.exe. I dati contenuti nel pacchetto sostituiscono quelli esistenti nel database di destinazione.  
  
-   Esportare BACPAC. Viene creato un file di backup logico (con estensione bacpac) di un database SQL di Windows Azure o SQL Server attivo contenente lo schema del database e i dati utente utilizzabili per eseguire la migrazione di un database da SQL Server locale al database SQL di Windows Azure. I database compatibili con Azure possono essere esportati e quindi importati in un secondo momento tra le versioni supportate di SQL Server.  
  
-   Importare BACPAC. Importare un file con estensione bacpac per creare un nuovo database o popolare un database SQL di Windows Azure o SQL Server vuoto.  
  
La documentazione completa di SqlPackage.exe su MSDN è disponibile [qui](http://msdn.microsoft.com/library/hh550080%28v=vs.103%29.aspx).  
  
**Compatibilità dei pacchetti**  
  
In questa versione sono disponibili diversi scenari di compatibilità di inoltro per pacchetti di applicazione livello dati.  
  
-   I pacchetti di applicazione livello dati creati da questa versione, non contenenti elementi SXI né dati della tabella, possono essere utilizzati dalle versioni precedenti di DACFx (SQL Server 2012 RTM, SQL Server 2012 CU1 e DACFx di settembre 2012).  
  
-   Tutti i pacchetti di applicazione livello dati creati dalle versioni precedenti di DACFx possono essere utilizzati da questa versione.  
  
## <a name="bkmk_known_issues_fixed"></a>8.0 Problemi noti risolti in questo Service Pack  
Per un elenco completo dei bug e dei problemi noti risolti in questo Service Pack, vedere [questo articolo della Knowledge Base](http://support.microsoft.com/kb/2674319).  
  
[Sommario](#bkmk_top)  
  
## <a name="see-also"></a>Vedere anche  
[Identificazione della versione e dell'edizione di SQL Server](http://support.microsoft.com/kb/321185)  
[Funzionalità supportate dalle edizioni di SQL Server 2014](http://msdn.microsoft.com/en-us/5da61ff5-12b9-48e6-b3c8-0dacca1751c4)  
  

