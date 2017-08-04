---
title: "Disponibilità elevata e ripristino di emergenza per Master Data Services | Documenti Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/28/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: 
author: sabotta
ms.author: carlasab
manager: craigg
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2afbf59101a0605dba2e79f09777160cb4de5cab
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---



# <a name="high-availability-and-disaster-recovery-for-master-data-services"></a>Disponibilità elevata e ripristino di emergenza per Master Data Services

**Riepilogo:** questo articolo illustra una soluzione per Master Data Service (MDS) ospitata nella configurazione di un gruppo di disponibilità AlwaysOn. L'articolo descrive come installare e configurare SQL 2016 Master Data Services in un gruppo di disponibilità (AG) AlwaysOn di SQL 2016. Lo scopo principale di questa soluzione consiste nel migliorare la disponibilità elevata e il recupero di emergenza dei dati di back-end di MDS ospitati in un database di SQL Server.

## <a name="introduction"></a>Introduzione


In questo articolo viene descritta una soluzione per Master Data Service (MDS) ospitata in una configurazione del gruppo di disponibilità AlwaysOn. L'articolo viene descritto come installare e configurare SQL 2016 MDS in un gruppo di disponibilità AlwaysOn di SQL 2016 (AG). Lo scopo principale di questa soluzione consiste nel migliorare la disponibilità elevata e il recupero di emergenza dei dati di back-end di MDS ospitati in un database di SQL Server.

Per implementare la soluzione, è necessario completare le seguenti attività illustrate in questo articolo.

1.  [Installare e di Windows Server Failover cluster (WSFC)](#windows-server-failover-cluster-wsfc).

2.  [Impostare i gruppo di disponibilità AlwaysOn](#sql-server-alwayson-availability-group).

3.  [Configurazione di MDS per l'esecuzione in un nodo WSFC](#configure-mds-to-run-on-an-wsfc-node).

Le sezioni precedenti introdurrà brevemente le tecnologie, seguite le istruzioni visualizzate. Per informazioni dettagliate sulle tecnologie, esaminare i documenti collegati a ciascuna sezione.

Questa soluzione descritta in questo articolo si basa su SQL Server AlwaysOn AG, in cui ogni database dispone di più repliche sincrone o asincrone. Solo una replica accetta la transazione (accetta le richieste utente). Questa è la replica primaria.

Ogni replica dispone di archiviazione, pertanto non è l'archiviazione condivisa non centralizzato in questa soluzione. Quando si verifica un errore software o un errore hardware che interessano la replica primaria, la replica primaria può eseguire il failover su una replica sincrona o asincrona che uno automaticamente o manualmente in base alla configurazione e situazioni. In questo modo si garantisce la disponibilità elevata del database con minime interruzioni per gli utenti.

Repliche asincrone sono in genere ospitate in un data center remoto del centro dati di replica primaria. In caso di scenari di emergenza, la replica primaria può eseguire il failover a un altro data center. In questo modo si garantisce il ripristino di emergenza del database.

A scopo dimostrativo, la soluzione descritta in questo articolo utilizza le seguenti versioni del software. Le versioni precedenti dovrebbero funzionare gli stessi, con differenze minime potenzialmente.

-   Windows Server 2012 R2 con cluster di Failover di Server

-   SQL Server 2016 con funzionalità di Master Data Services

Inoltre, la soluzione utilizza due macchine virtuali, **MDS HA1** e **MDS HA2**, per ospitare due repliche. Come è supportato dal gruppo di disponibilità AlwaysOn di SQL Server, MDS non limita il numero di repliche è possibile utilizzare.

In questo articolo si presuppone la presenza della knowledge base su Windows Server, il Cluster di Failover di Windows Server, SQL Server AlwaysOn e SQL Server MDS.

## <a name="what-is-not-covered"></a>Cosa non è coperto

Questo documento non includono le seguenti operazioni:

-   Come rendere IIS, il server web che ospita il Master dell'interfaccia utente, recuperabile dopo un'emergenza e a disponibilità elevata del servizio dati. MDS non impone alcun requisito specifico in IIS, in modo che le tecniche standard per impostare IIS a disponibilità elevata e bilanciamento del carico possono lavorare qui anche.

-   Come utilizzare il cluster di failover (FCI) AlwaysOn di SQL Server per supportare la disponibilità elevata (HA) nel back-end MDS. Il clustering di failover di SQL Server è una soluzione a disponibilità elevata diversa è ufficialmente supportato da SQL Server, e funziona con MDS.

-   Come utilizzare una soluzione ibrida di cluster di failover di SQL Server (FCI) e gruppo di disponibilità AlwaysOn per il supporto a disponibilità elevata nel back-end MDS. La soluzione ibrida funziona con MDS.

## <a name="design-consideration"></a>Considerazioni sulla progettazione

Figura 1 mostra una configurazione tipica utilizzata principalmente in gruppo di disponibilità AlwaysOn. In data center principale, esistono due repliche con una relazione di commit sincrono ed entrambe le repliche dispongono del privilegio di voto. Questa opzione viene usata principalmente per migliorare la disponibilità elevata nel caso in cui la replica primaria ha esito negativo.

In Data Center, ripristino di emergenza è una replica secondaria con una relazione con commit asincrono con la replica primaria. Questo centro dati è in genere in un'area geografica diversa da data center principale. La replica secondaria non dispone dei privilegi di voto.

Questa configurazione viene utilizzata per ottenere il ripristino nel caso in cui il data center principale in caso di emergenza, ad esempio un incendio, terremoti e così via. La configurazione si ottiene entrambi a disponibilità elevata e ripristino di emergenza con il costo relativamente basso.

![Configurazione tipica per il gruppo di disponibilità AlwaysOn](media/Fig1_TypicalConfig.png)

Figura 1. Una configurazione tipica il gruppo di disponibilità AlwaysOn

Se non è necessario prendere in considerazione il ripristino di emergenza, non occorre disporre di una replica in un secondo data center. Se è necessario migliorare la disponibilità elevata, è possibile che altre repliche sincrone nella stessa data center principale con.

Pertanto, è importante prendere in considerazione i requisiti e gli scenari e scegliere il numero di repliche sincrone e asincrone è necessario, e data center è necessario inserirli in.

## <a name="windows-server-failover-cluster-wsfc"></a>Windows Server Failover Clustering (WSFC)

Questa sezione descrive le attività seguenti.

1.  [Installare la funzionalità Cluster di Failover Windows](#install-failover-cluster-feature).

2.  [Creare un Cluster di Failover di Windows Server](#create-a-windows-server-failover-cluster).

Come illustrato nella figura 1 nella sezione precedente, la soluzione descritta in questo articolo include Windows Server Failover Cluster (WSFC). È necessario configurare WSFC perché SQL AlwaysOn dipende WFSC per il failover e il rilevamento degli errori.

WSFC è una funzionalità per migliorare la disponibilità elevata di applicazioni e servizi. È costituito da un gruppo di istanze di server indipendenti windows con il servizio Cluster di Failover Microsoft in esecuzione nelle istanze in questione. Le istanze del server windows (o nodi come vengono talvolta chiamati) sono connessi in modo che possano comunicare tra loro e il rilevamento degli errori è possibile. WSFC forniscono errore funzionalità di rilevamento e il failover. Se un nodo o un servizio del cluster, quindi è stato rilevato l'errore e un altro nodo automaticamente o manualmente inizia a fornire i servizi ospitati su tale nodo. Di conseguenza, gli utenti solo verificano interruzioni minime nei servizi e la disponibilità del servizio è stata migliorata.  

### <a name="prerequisites"></a>Prerequisiti

Il sistema operativo Windows Server è installato in tutte le istanze e tutti gli aggiornamenti sono corretti.

>[!NOTE] 
>È **consigliabile** installare la stessa versione di Windows e la stessa funzionalità impostate in tutte le istanze per evitare potenziali problemi di incompatibilità.

### <a name="install-failover-cluster-feature"></a>Installare la funzionalità Cluster di Failover

Completare i passaggi seguenti per ogni istanza del Server di Windows installare la funzionalità WSFC in ogni istanza. Sono necessarie autorizzazioni di amministratore.

1.  Aprire **Server Manager** in Windows Server e fare clic su **Aggiungi ruoli e funzionalità** nel riquadro di destra. Verrà avviata la **Aggiunta guidata ruoli e funzionalità**.

2.  Fare clic su **Avanti** fino al **funzionalità** pagina.

3.  Selezionare il **Clustering di Failover** casella di controllo, quindi fare clic su **Avanti** per completare l'installazione. Vedere la figura 2.

    Se viene chiesto di confermare il **aggiungere le funzionalità necessarie per il clustering di Failover**, fare clic su **Aggiungi funzionalità**. Vedere la figura 3.

    ![Aggiunta guidata ruoli e funzionalità, il Clustering di Failover](media/Fig2_SelectFeatures.png)

    Figura 2

    ![Aggiunta guidata ruoli e funzionalità, necessarie per il cluster di failover](media/Fig3_RequiredFeaturesFailover.png)

    Figura 3

4.  Nel **conferma** pagina, fare clic su **installare** per installare il funzionalità clustering di failover.

5.  Nel **risultato** pagina, assicurarsi che tutto ciò che è stato installato senza errori e avvisi.

### <a name="create-a-windows-server-failover-cluster"></a>Creare un cluster di failover di Windows Server

Dopo che tutte le istanze è installata la funzionalità WSFC, è possibile configurare WSFC. È necessario solo eseguire questa operazione in un nodo.

1.  Aprire **Server Manager** in Windows Server e fare clic su **gestione Cluster di Failover** sul **strumento** menu nell'angolo superiore destro per avviare la gestione.

2.  In **gestione Cluster di Failover**, fare clic su **convalida configurazione** nel riquadro di destra. Vedere la figura 4.

    ![Gestione Cluster di failover, convalidare la configurazione](media/Fig4_ValidateConfig.png)

    Figura 4

3.  Nel **convalidare una configurazione** **guidata**, fare clic su **Avanti**.

4.  Nel **selezionare Server o un Cluster** finestra di dialogo, aggiungere i nomi dei server che ospiterà SQL Server, quindi fare clic su **Avanti**. Vedere la figura 5.

    In questo esempio è stato aggiunto due istanze, MDS HA1 e HA2 di MDS.

    ![La convalida guidata configurazione, selezionare Server o una pagina di Cluster](media/Fig5_AddServer.png)

    Figura 5

5.  Nel **opzioni di Testing** pagina, fare clic su **eseguire tutti i test**e quindi fare clic su **Avanti**.

6.  Fare clic su **Avanti** per completare la convalida.

    Il **Validating** pagina vengono visualizzati lo stato di avanzamento e **riepilogo** pagina Mostra il riepilogo di convalida. Vedere figure 6 e 7.

7.  Nel **riepilogo** pagina, controllare gli eventuali messaggi di avviso o errore.

    Gli errori devono essere corretti. Tuttavia, gli avvisi non sia un problema. Un messaggio di avviso significa che "l'elemento testato potrebbe soddisfare il requisito, ma ci sono che controllare". Ad esempio, figura 7 è illustrato un "latenza di accesso al disco convalidare" avviso, che può essere dovuto al disco occupato in altre attività temporaneamente e può essere ignorato. È consigliabile controllare la documentazione online per ogni avviso e il messaggio di errore per ulteriori dettagli. Vedere la figura 7.
 
    ![Convalida configurazione guidata, pagina convalida in corso](media/Fig6_ValidationTests.png)

    Figura 6

    ![Convalida guidata configurazione, pagina Riepilogo](media/Fig7_ValidationSummary.png)

    Figura 7

8.  Nel **riepilogo** pagina, verificare che il **crea il cluster ora utilizzando i nodi convalidati** casella di controllo è selezionata e quindi fare clic su **fine** per avviare il **crea Cluster** **guidata**.

9.  Nel **crea Cluster** **guidata**, fare clic su **Avanti**.

10. Nel **punto di accesso per l'amministrazione del Cluster** pagina, immettere il nome del cluster WSFC e quindi fare clic su **Avanti**. In questo esempio, utilizziamo "MDS-a disponibilità elevata" come nome del cluster. Vedere la figura 8.

    ![Immettere il nome del Cluster](media/Fig8_EnterClusterName.png)

    Figura 8

11. Continuare a fare clic su **Avanti** per completare la creazione del cluster. Il **riepilogo di Cluster MDS-a disponibilità elevata** sezione sono visualizzate le informazioni del cluster. Vedere la figura 9.

    ![Visualizza informazioni di riepilogo per il Cluster](media/Fig9_ClusterSummary.png)

    Figura 9

    Se è necessario aggiungere un nodo in un secondo momento, fare clic su **aggiunta del nodo** azione nel riquadro di destra in **gestione Cluster di Failover**.

Note:

-   La funzionalità WSFC potrebbe non essere disponibile in tutte le edizioni di Windows Server. Assicurarsi che questa funzionalità è disponibile l'edizione.

-   Verificare di che disporre delle autorizzazioni appropriate per configurare WSFC in active directory. Se sono presenti eventuali problemi, vedere [Guida dettagliata al Cluster di Failover: configurare l'account in Active Directory](https://technet.microsoft.com/library/cc731002(v=ws.10).aspx).

Per ulteriori informazioni su WSFC, vedere [i cluster di Failover](https://technet.microsoft.com/library/cc732488(v=ws.10).aspx).

## <a name="sql-server-alwayson-availability-group"></a>Gruppo di disponibilità AlwaysOn di SQL Server

Questa sezione descrive le attività seguenti.

1.  [Gruppo di disponibilità AlwaysOn di abilitare SQL Server](#enable-sql-server-alwayson-availability-group-on-every-sql-server-instance).

2.  [Creare un gruppo di disponibilità](#create-an-availability-group).

3.  [Convalidare e testare il gruppo di disponibilità](#validation-and-test-the-availability-group).

Soluzioni AlwaysOn di SQLServer forniscono elevato disponibilità e ripristino di emergenza per i database di SQL Server. AlwaysOn dispone di due possibili soluzioni.
Entrambi si avvalgono di WSFC.

-   Gruppi di disponibilità AlwaysOn (gruppo di disponibilità)

-   Istanze del Cluster di Failover AlwaysOn (FCI).

Gruppo di disponibilità consente di migliorare la disponibilità elevata a livello di database. Il gruppo di disponibilità (un set di database utente) e il relativo nome di rete virtuale sono registrati come risorse di WSFC.

È possibile migliorare la disponibilità elevata a livello di istanza FCI. Servizio SQL Server e i servizi correlati sono registrati come risorse di WSFC. Inoltre, la soluzione di infrastruttura di classificazione file richiede l'archiviazione su disco condiviso simmetrica, ad esempio SAN o SMB condivisioni file che devono essere disponibili a tutti i nodi nel cluster WFC.


### <a name="prerequisites"></a>Prerequisiti

-   Installare SQL Server in tutti i nodi. Per altre informazioni, vedere [Installare SQL Server 2016](https://docs.microsoft.com/sql/database-engine/install-windows/install-sql-server).

-   (Scelta consigliata) Installare la versione esatta stesso set di funzionalità di SQL Server in ogni nodo. In particolare, deve essere installato MDS.

-   (Scelta consigliata) Utilizzare la stessa configurazione per tutte le istanze di SQL Server. In particolare, le stesse regole di confronto di server deve essere configurato in tutte le istanze di SQL Server.

-   (Scelta consigliata) Utilizzare lo stesso account di servizio per eseguire tutte le istanze di SQL Server. In caso contrario, è necessario concedere l'autorizzazione per ogni istanza di SQL Server per assicurarsi che le istanze di SQL Server possono comunicare tra loro.

-   Verificare che l'impostazione di Windows firewall consenta le istanze di SQL Server comunicare tra loro.

### <a name="enable-sql-server-alwayson-availability-group-on-every-sql-server-instance"></a>Abilita SQL Server AlwaysOn gruppo di disponibilità in ogni istanza SQL Server

1.  Nel **Gestione configurazione SQL Server** fare clic su **servizio SQL Server** nel riquadro sinistro, destro **SQL Server** nel riquadro destro e quindi fare clic su **proprietà**. Vedere la figura 10.

    ![Finestra proprietà di SQL Server](media/Fig10_SQLServerProperties.png)

    Figura 10

2.  Nel **SQL Server (MSSQLSERVER)** **proprietà** la finestra di dialogo, fare clic sul **disponibilità elevata AlwaysOn** scheda e quindi selezionare il **Abilita gruppi di disponibilità AlwaysOn** casella di controllo. Quando è visualizzato un valore di **nome cluster di failover Windows** casella di testo, fare clic su **OK** per continuare. Vedere la figura 11.

    ![Abilitare l'opzione di gruppi di disponibilità AlwaysOn](media/Fig11_EnableAlwaysOn.png)

    Figura 11

3.  Quando viene visualizzata una pagina di avviso, fare clic su **OK** per continuare. Vedere la figura 12.

    ![Confermare per arrestare e riavviare servizio](media/Fig12_WarningServiceStopStart.png)

    Figura 12

4.  Fare clic su **riavviare**, riavviare il **SQL Server** service e rendere effettiva questa modifica. Vedere la figura 10.

>[!NOTE] 
>È possibile modificare l'account del servizio in esecuzione il servizio SQL Server utilizzando il **Gestione configurazione SQL Server**. Fare clic su di **accesso** nella scheda il **SQL Server (MSSQLSERVER)** **proprietà** la finestra di dialogo. Vedere la figura 11.

### <a name="create-an-availability-group"></a>Creare un gruppo di disponibilità

Dopo aver abilitata la funzionalità AlwaysOn in tutte le istanze di SQL Server, si crea un nuovo gruppo di disponibilità che contiene il database MDS in un nodo.

Gruppo di disponibilità può essere creato solo sui database esistenti. Pertanto, entrambi creare un database MDS in un nodo, o creare un database temporaneo e quindi eliminare il database temporaneo. In questo esempio, si crea un database emptyMDS e crea un gruppo di disponibilità in questo database MDS.

1.  Avviare **SQL Server Management Studio** (**SSMS**) in un nodo e connettersi all'istanza di SQL Server locale con le credenziali appropriate.

2.  In SQL Server Management Studio, aprire un **nuova query** finestra ed eseguire lo script seguente per creare un database vuoto. Sostituire c:\\temporanea con il percorso che si desidera utilizzare per eseguire un backup completo.

    ```
    CREATE DATABASE MDS\_Sample
    GO
    BACKUP DATABASE MDS\_Sample TO DISK='C:\\temp'
    GO
    ```

    >[!NOTE] 
    >Un backup completo del database è necessario per la creazione del gruppo di disponibilità in questo database.

3.  Nel **Esplora oggetti**, espandere il **disponibilità elevata AlwaysOn** cartella e fare clic su **Creazione guidata nuovo gruppo di disponibilità** per avviare il **Creazione guidata nuovo gruppo di disponibilità**. Vedere la figura 13.

    ![Procedura guidata avviare di nuovo gruppo di disponibilità](media/Fig13_AvailabilityGroupsFolder.png)

    Figura 13

4.  Nel **nuovo gruppo di disponibilità** procedura guidata, fare clic su **Avanti** per visualizzare il **specificare il nome** pagina. Digitare un nome per il gruppo di disponibilità e quindi fare clic su **Avanti**. Vedere la figura 14.

    ![Immettere il nome del gruppo di disponibilità](media/Fig14_AvailabilityGroupName.png)

    Nella figura 14

5.  Fare clic sul database appena creato nel **seleziona Database** pagina e quindi fare clic su **Avanti**. Vedere la figura 15.

    ![Selezionare il database](media/Fig15_AvailabilityGroupSelectDatabase.png)

    Figura 15

6.  Nel **specifica repliche** pagina, aggiungere un'altra replica facendo **Aggiungi Replica**. Questa pagina elenca già le istanze di SQL Server corrente, locale come replica. Vedere la figura 16.

7.  Nel **Connetti al Server** finestra di dialogo, aggiungere le credenziali appropriate e scegliere **Connetti**.

    ![Connettersi a un'istanza di SQL Server](media/Fig16_AddReplicaConnectServer.png)

    Figura 16

    Verrà visualizzata nell'elenco di due repliche. Ripetere questo passaggio per aggiungere altri nodi come repliche. Vedere la figura 17.

    ![Visualizza elenco di repliche](media/Fig17_AvailabilityGroupSQLReplicas.png)

    Figura 17

    Per ogni replica, configurare le impostazioni seguenti **Commit sincrono**, **il Failover automatico**, e **secondario leggibile** impostazioni. Vedere la figura
17.

    **Commit sincrono**: in questo modo si garantisce che se una transazione viene eseguito il commit nella replica primaria di un database, quindi la transazione viene eseguito il commit anche tutte le altre repliche sincrone. Non garantisce questo commit asincrono e potrebbe rimanere indietro rispetto alla replica primaria.

    In genere, è consigliabile abilitare commit sincrono solo quando i due nodi sono nello stesso data center. Se sono in data center diversi, con commit sincrono può rallentare le prestazioni del database.

    Se questa casella di controllo non è selezionata, viene utilizzato con commit asincrono.

    **Il Failover automatico:** quando la replica primaria è inattivo, il gruppo di disponibilità esegue automaticamente il failover alla replica secondaria quando viene selezionato il failover automatico. Può essere abilitata solo sulle repliche con commit sincrono.

    **Secondario leggibile:** per impostazione predefinita, gli utenti non possono connettersi a tutte le repliche secondarie. Ciò consentirà agli utenti di connettersi alla replica secondaria con accesso in sola lettura.

8.  Nel **specifica repliche** pagina, fare clic su di **Listener** scheda e di eseguire le operazioni seguenti. Vedere la figura 18.

    A.  Fare clic su **creare un listener del gruppo di disponibilità** per configurare un listener del gruppo di disponibilità per la connessione al database MDS.

    B.  Immettere un **nome DNS listener**, ad esempio MDSSQLServer.

    c.  Immettere la porta SQL predefinita 1433, nel **porta** casella di testo.

    d.  Immettere DHCP nel **modalità di rete** casella di testo e quindi fare clic su **Avanti** per continuare.

    >[!NOTE] 
    >Facoltativamente, è possibile scegliere "Indirizzo IP statico" come il **modalità di rete** e immettere un indirizzo IP statico. È inoltre possibile immettere una porta diversa dalla 1433. 

    ![Configurare il Listener](media/Fig18_AvailabilityGroupCreateListener.png)

    Figura 18

9.  Nel **seleziona sincronizzazione dati** pagina, fare clic su **completo**e specificare una condivisione di rete che possono accedere tutti i nodi. Per continuare, fare clic su **Avanti** . Vedere la figura 19.

    Questa condivisione di rete verrà utilizzata per archiviare il backup di database per creare le repliche secondarie. Se non è disponibile per l'organizzazione, scegliere un altro preferenza di sincronizzazione dei dati. Fare riferimento a [gruppo di disponibilità AlwaysOn di SQL Server 2016](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/always-on-availability-groups-sql-server) su come utilizzare altre opzioni per creare le repliche secondarie. Nella figura 17 Elenca anche altre opzioni.

    ![Configurare la sincronizzazione dei dati](media/Fig19_AvailabilityGroupDataSync.png)

    Figura 19 

10. Nel **convalida** pagina, assicurarsi che tutte le convalide sono state passate correttamente e correggere eventuali errori. Per continuare, fare clic su **Avanti** .

11. Nel **riepilogo** pagina, esaminare tutte le impostazioni di configurazione e fare clic su **fine**. Questo verrà creato il gruppo di disponibilità e configurarlo.

12. Nel **risultato** pagina, verificare che tutti i passaggi necessari sono stati completati.

### <a name="validation-and-test-the-availability-group"></a>Convalida e Test del gruppo di disponibilità

1.  Aprire SQL Server Management Studio e connettersi al nome DNS del listener appena creato nel [creare un gruppo di disponibilità](#create-an-availability-group) sezione. In questo esempio è MDSSQLServer.

2.  In **Esplora oggetti**, espandere il **disponibilità elevata AlwaysOn** cartella, fare clic destro del gruppo di disponibilità appena creato nel [creare un gruppo di disponibilità](#create-an-availability-group) sezione e quindi fare clic su **Mostra Dashboard**. Vedere la figura 20. Viene visualizzato lo stato del nuovo gruppo di disponibilità e delle relative repliche.

    ![Visualizzare il dashboard](media/Fig20_ShowDashboard.png)

    Figura 20 

3.  Fare clic su **Failover** per eseguire il failover di una replica sincrona e una replica asincrona. Si tratta di verificare che il failover avviene correttamente senza problemi.

 L'installazione di AlwaysOn è stata completata.

Per ulteriori informazioni sul gruppo di disponibilità AlwaysOn, vedere [gruppo di disponibilità AlwaysOn di SQL Server 2016](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/always-on-availability-groups-sql-server).

## <a name="configure-mds-to-run-on-an-wsfc-node"></a>Configurazione di MDS per l'esecuzione su un nodo WSFC

Questa soluzione presentata in questo articolo richiede solo il database back-end MDS in esecuzione su WSFC. Altre parti di MDS, ad esempio applicazioni web e Gestione configurazione di MDS, è possibile eseguire nel nodo wsfc o all'esterno di WSFC, purché MDS può connettersi al gruppo di disponibilità.

1.  Aprire **servizio configurazione Gestione di dati Master** in un nodo, fare clic su **configurazione Database**e quindi fare clic su **Create Database** per avviare il **procedura guidata Crea Database**.

2.  Nel **Server di Database** , digitare il nome DNS del listener gruppo di disponibilità nel **istanza di SQL Server** casella di testo, fare clic su **Test connessione**e quindi fare clic su **Avanti**. La figura 21.

    ![Configurare il server di database con listener gruppo di disponibilità](media/Fig21_MDSDatabaseServerListener.png)

    Figura 21

3.  Nel **Database** , digitare il nome del database in cui è stato creato nel [creare un gruppo di disponibilità](#create-an-availability-group) sezione e quindi fare clic su **Avanti**. Vedere la figura 22.

    ![Creare e configurare il database](media/Fig22_MDSCreateDatabase.png)

    Figura 22

4.  Completare il **creare Database** **guidata**. Per ulteriori informazioni, vedere [configurazione e installazione di Master Data Services](https://docs.microsoft.com/sql/master-data-services/master-data-services-installation-and-configuration).

5.  Fare clic su **applicazioni Web** in **servizio configurazione Gestione di dati Master** per configurare l'applicazione Web e quindi fare clic su **applica** per applicare le impostazioni in MDS. Vedere la figura 23. Per ulteriori informazioni, vedere [configurazione e installazione di Master Data Services](https://docs.microsoft.com/sql/master-data-services/master-data-services-installation-and-configuration).

    ![Configurare l'applicazione Web](media/Fig23_MDSWebApplication.png)

    Nella figura 23

    Il programma di installazione MDS viene completata. È possibile ripetere i passaggi sopra descritti per configurare MDS affinché venga eseguito in tutti i nodi. Il database back-end è lo stesso per il gruppo di disponibilità stesso.

6.  Se in precedenza è stato creato un database temporaneo (vedere [creare un gruppo di disponibilità](#create-an-availability-group) sezione) per creare gruppo di disponibilità AlwaysOn, è necessario eliminare il database temporaneo

    Per ulteriori informazioni su Master Data Services, fare riferimento a [Master Data Services](https://docs.microsoft.com/sql/master-data-services/master-data-services-overview-mds).

## <a name="conclusion"></a>Conclusioni

In questo white paper, è stato descritto come installare e configurare il database back-end di Master Data Services nella parte superiore di gruppo di disponibilità AlwaysOn di SQL Server. Questa configurazione fornisce disponibilità elevata e ripristino di emergenza nel database back-end di Master Data Services. Per implementare questa configurazione, è necessario installare e configurare Windows Server Failover Cluster, SQL Server gruppo di disponibilità AlwaysOn e di Master Data Services.

## <a name="feedback"></a>Commenti e suggerimenti

Il documento è risultato utile? Per commenti e suggerimenti, fare clic su **commenti** nella parte superiore dell'articolo. 

Commenti e suggerimenti ci aiuteranno a migliorare la qualità della documentazione pubblicata. 


