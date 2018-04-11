---
title: Configurare Windows Server Update Services (WSUS) (sistema di piattaforma Analitica)
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a10b2884-468e-41ef-bd59-8df894381254
caps.latest.revision: 41
ms.openlocfilehash: 31427bc55017cf9c069e8cd4a467dfdb9608ca3f
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/10/2018
---
# <a name="configure-windows-server-update-services-wsus"></a>Configurare Windows Server Update Services (WSUS)
Queste istruzioni consentono di eseguire i passaggi per utilizzare la procedura guidata configurazione di Windows Server Update Services (WSUS) per configurare WSUS per il sistema di piattaforma Analitica. È necessario configurare WSUS prima di poter applicare aggiornamenti software al dispositivo. WSUS è già installata nella macchina virtuale VMM del dispositivo.  
  
Per ulteriori informazioni sulla configurazione di WSUS, vedere il [Guida all'installazione di WSUS dettagliata](http://go.microsoft.com/fwlink/?LinkId=202417) nel sito Web WSUS. Dopo la configurazione di WSUS, vedere [scaricare e applicare gli aggiornamenti di Microsoft &#40;Analitica Platform System&#41; ](download-and-apply-microsoft-updates.md) per avviare un aggiornamento.  
  
> [!WARNING]  
> Se si verificano errori durante questo processo di configurazione, arrestare e contattare il supporto tecnico per assistenza. Non ignorare gli errori o continuare il processo dopo gli errori sono stati ricevuti.  
  
## <a name="before-you-begin"></a>Prima di iniziare  
Per configurare WSUS, è necessario:  
  
-   Avere le informazioni di accesso Analitica Platform System accessorio dominio amministratore account.  
  
-   Dispone un account di accesso di sistema della piattaforma Analitica con autorizzazioni di accesso di **Console di amministrazione** e visualizzare informazioni sullo stato del dispositivo.  
  
-   Conoscere l'indirizzo IP del server WSUS upstream se si intende sincronizzare gli aggiornamenti da un server WSUS upstream anziché la sincronizzazione degli aggiornamenti direttamente da Microsoft Update. Verificare che il server WSUS padre è impostato per consentire connessioni anonime e supporta SSL.  
  
-   Conoscere l'indirizzo IP del server proxy se il dispositivo verrà utilizzato un server proxy per accedere al server upstream o Microsoft Update.  
  
-   Nella maggior parte dei casi, è necessario accedere ai server di fuori dell'accessorio WSUS. Per supportare questo scenario di utilizzo Analitica piattaforma del sistema DNS possono essere configurati per supportare un server d'inoltro nome esterno che consentirà di host Analitica Platform System e macchine virtuali (VM) utilizzare i server DNS esterni per la risoluzione dei nomi di fuori del dispositivo. Per altre informazioni, vedere [utilizzare un server d'inoltro di DNS per risolvere nomi DNS Non accessorio &#40;Analitica Platform System&#41;](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md).  
  
## <a name="to-configure-windows-server-update-services-wsus"></a>Per configurare Windows Server Update Services (WSUS)  
  
1.  Accedere al **Console di amministrazione**. Nel **stato dello strumento** scheda, verificare che il **Cluster** e **rete** colonne mostrano verde (o **NA**) per tutti i nodi. Verificare gli indicatori di stato per tutti i nodi nel **stato dello strumento**.  
  
    -   È possibile proseguire con il colore verde o indicatori NA.  
  
    -   Restituire errori avviso (giallo) non critici. In alcuni casi i messaggi di avviso non verranno bloccata gli aggiornamenti. Se è presente un errore del volume disco non critiche che non è presente nell'unità C:\, è possibile procedere al passaggio successivo prima di risolvere l'errore del volume del disco.  
  
    -   Prima di continuare, è necessario risolvere la maggior parte degli indicatori rossi. Se sono presenti errori del disco, usare il **Console di amministrazione avvisi** pagina per verificare che il disco non più di un errore all'interno di ogni server o un array SAN. In caso di errore non più di un disco in ogni server o un array SAN, è possibile procedere al passaggio successivo prima di correggere gli errori del disco. Assicurarsi di contattare il supporto tecnico Microsoft per risolvere gli errori di disco appena possibile.  
  
2.  Accedere alla macchina virtuale VMM come un amministratore di dominio del dispositivo.  
  
3.  Avviare la configurazione guidata.  
  
    #### <a name="to-launch-the-configuration-wizard"></a>Per avviare la configurazione guidata  
  
    1.  Nel **Dashboard di Server Manager**via il **strumenti** menu, fare clic su **Windows Server Update Services**.  
  
    2.  Nel riquadro a sinistra del **Update Services** finestra, fare clic per espandere il server di gestione delle macchine virtuali nodo (***appliance_domain *-VMM**), quindi fare clic su **opzioni**.  
  
    3.  Nel **opzioni** riquadro, fare clic su **configurazione guidata del Server WSUS** per avviare la configurazione guidata.  
  
        ![Menu del Dashboard di Server Manager](./media/configure-windows-server-update-services-wsus/WSUS_Wiz0.png "WSUS_Wiz0")  
  
    4.  Se questa è la prima volta hanno la procedura guidata WSUS, potrebbe essere necessario configurare una directory per archiviare gli aggiornamenti. `C:\wsus` è un percorso appropriato; Tuttavia è possibile fornire un percorso diverso.  
  
        ![Percorso WSUS](./media/configure-windows-server-update-services-wsus/WSUS_Wiz1.png "WSUS_Wiz1")  
  
    5.  Esaminare il **prima di iniziare** elenco di elementi da completare prima di completare la procedura guidata.  
  
        ![WSUS prima di iniziare](./media/configure-windows-server-update-services-wsus/WSUS_Wiz2.png "WSUS_Wiz2")  
  
    6.  Nel **partecipa al programma Analisi utilizzo software di Microsoft Update** selezionare **Sì, desidero partecipare al programma Analisi utilizzo software di Microsoft Update**, quindi fare clic su **successivo**.  
  
        ![Programma Analisi utilizzo software WSUS](./media/configure-windows-server-update-services-wsus/WSUS_Wiz3.png "WSUS_Wiz3")  
  
    Verrà visualizzato il **scelta Server Upstream** pagina. Nella schermata seguente è il punto iniziale della configurazione guidata.  
  
    ![WSUS Upstream Server Sync](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4a.png "WSUS_Wiz4a")  
  
4.  Scegliere il server upstream.  
  
    Nel **scelta Server Upstream** pagina della configurazione guidata WSUS, selezionare la modalità in cui si connetteranno WSUS nel nodo di gestione delle macchine virtuali a un server upstream per ottenere gli aggiornamenti software. Sono disponibili due soluzioni per sincronizzare il server upstream con [Microsoft Update](http://go.microsoft.com/fwlink/?LinkId=133349) o sincronizzare gli aggiornamenti con un altro server di Windows Server Update Services.  
  
    #### <a name="to-update-by-using-microsoft-update"></a>Per l'aggiornamento tramite Microsoft Update  
  
    1.  Se si sceglie di eseguire la sincronizzazione con Microsoft Update, non è necessario apportare modifiche per il **scelta Server Upstream** pagina. Scegliere **Avanti**.  
  
        ![WSUS Upstream Server Sync](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4a.png "WSUS_Wiz4a")  
  
    #### <a name="to-update-from-another-wsus-server"></a>Per l'aggiornamento da un altro server WSUS  
  
    1.  Se si sceglie di eseguire la sincronizzazione con un'origine diversa da Microsoft Update (un server upstream), specificare il server (immettere l'indirizzo IP) e la porta su cui il server comunicherà con il server upstream.  
  
        ![WSUS-sincronizzazione Server a monte da WSUS](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4b.png "WSUS_Wiz4b")  
  
    2.  Per utilizzare Secure Sockets Layer (SSL), selezionare il **Usa SSL per la sincronizzazione delle informazioni di aggiornamento** casella di controllo. In questo caso i server utilizzeranno la porta 443 per la sincronizzazione.  
  
        ![WSUS-sincronizzazione Server a monte da WSUS SSL](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4c.png "WSUS_Wiz4c")  
  
    3.  Se si tratta di un server di replica, selezionare il **si tratta di una replica del server upstream** casella di controllo. È possibile selezionare sia **Usa SSL per la sincronizzazione delle informazioni sull'aggiornamento** e **si tratta di una replica del server upstream**.  
  
        ![WSUS Upstream Server Replica](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4d.png "WSUS_Wiz4d")  
  
    4.  A questo punto, si è finito di lavorare con configurazione del server upstream. Fare clic su **Avanti**, oppure selezionare **specificare un server proxy** nel riquadro di spostamento a sinistra.  
  
5.  Specificare il server proxy.  
  
    Se il server richiede un server proxy per accedere a Microsoft Update o un altro server upstream, è possibile configurare le impostazioni del server proxy. in caso contrario, fare clic su **Avanti**.  
  
    ![WSUS Proxy](./media/configure-windows-server-update-services-wsus/WSUS_Wiz5a.png "WSUS_Wiz5a")  
  
    #### <a name="to-configure-proxy-server-settings"></a>Per configurare le impostazioni di proxy server  
  
    1.  Nel **specificare il Server Proxy** pagina della procedura guidata configurazione, selezionare il **Usa un server proxy durante la sincronizzazione** casella di controllo e quindi digitare l'indirizzo IP del proxy server (non al nome) e il numero di porta (porta 80 per impostazione predefinita) nelle caselle corrispondenti.  
  
    2.  Se si desidera connettersi al server proxy utilizzando le credenziali utente specifico, selezionare il **Usa credenziali utente per connettersi al server proxy** casella di controllo e quindi digitare il nome utente, dominio e la password dell'utente nel corrispondente finestre. Se si desidera abilitare l'autenticazione di base per l'utente si connette al server proxy, selezionare il **Consenti autenticazione di base (password viene inviata come testo non crittografato)** casella di controllo.  
  
        ![WSUS-credenziali Proxy](./media/configure-windows-server-update-services-wsus/WSUS_Wiz5b.png "WSUS_Wiz5b")  
  
    3.  A questo punto, si è finito di lavorare con configurazione del server proxy. Fare clic su **Avanti** per passare alla pagina successiva, in cui è possibile iniziare a configurare il processo di sincronizzazione.  
  
6.  Avviare la connessione.  
  
    ![Connessione avvio Proxy WSUS](./media/configure-windows-server-update-services-wsus/WSUS_Wiz6.png "WSUS_Wiz6")  
  
    Fare clic su **-connessione avvio**.  
  
    Dopo la connessione ha avuto esito positivo, fare clic su **Avanti** per passare alla pagina successiva, in cui è possibile scegliere le lingue.  
  
7.  Scegliere le lingue.  
  
    Selezionare **Scarica aggiornamenti solo nelle lingue seguenti**.  
  
    Selezionare **inglese**, quindi fare clic su **Avanti**.  
  
    ![Scegliere le lingue](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChooseLanguages.png "SQL_Server_PDW_WSUSChooseLanguages")  
  
8.  Scegliere i prodotti.  
  
    > [!NOTE]  
    > Se si utilizza un Server Upstream, non sarà possibile scegliere i prodotti. Se questa opzione non è disponibile, ignorare questo passaggio.  
  
    Deselezionare tutti gli aggiornamenti selezionati.  
  
    Selezionare **SQL Server 2014**, **SQL Server 2016**, **Windows Server 2012 R2**, e **System Center 2012 R2 - Virtual Machine Manager**, e quindi fare clic su **Avanti**.  
  
9. Scegliere le classificazioni.  
  
    > [!NOTE]  
    > Se si utilizza un Server Upstream, non sarà possibile scegliere le classificazioni.  Se questa opzione non è disponibile, ignorare questo passaggio.  
  
    Deselezionare tutti gli aggiornamenti selezionati in precedenza.  
  
    Selezionare **gli aggiornamenti critici** e **gli aggiornamenti della sicurezza** per gli aggiornamenti che verranno sincronizzati per il dispositivo di sistema della piattaforma Analitica e quindi fare clic su **Avanti**.  
  
    ![Scegliere le classificazioni](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChooseClassifications.png "SQL_Server_PDW_WSUSChooseClassifications")  
  
10. Configurare la pianificazione della sincronizzazione.  
  
    Selezionare **sincronizzare manualmente**, quindi fare clic su **Avanti**.  
  
    ![Pianificazione della sincronizzazione set](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSSyncSchedule.png "SQL_Server_PDW_WSUSSyncSchedule")  
  
11. Avvia sincronizzazione iniziale.  
  
    Selezionare **Avvia sincronizzazione iniziale**, quindi fare clic su **Avanti**.  
  
12. Fine.  
  
    Fare clic su **Fine**.  
  
## <a name="bkmk_WSUSGroup"></a>Gruppo Server Appliance in WSUS  
Dopo la configurazione di WSUS per il sistema di piattaforma Analitica, il passaggio successivo è per raggruppare i server dello strumento. Aggiungendo tutti i server di dispositivo a un gruppo, WSUS sarà in grado di applicare gli aggiornamenti software a tutti i server nel dispositivo.  
  
> [!NOTE]  
> Il sistema WSUS è progettato per eseguire in modo asincrono. Avvio di attività non restituisce sempre un aggiornamento immediatamente. Di conseguenza, potrebbe essere necessario attendere fino a quando i computer saranno visibili nelle finestre di dialogo WSUS. In esecuzione la `setup.exe /action=ReportMicrosoftUpdateClientStatus /DomainAdminPassword="<password>"` comando descritto alla fine dell'argomento [scaricare e applicare gli aggiornamenti Microsoft &#40;Analitica Platform System&#41; ](download-and-apply-microsoft-updates.md) consentono di aggiornare le finestre di dialogo.  
  
#### <a name="to-group-the-appliance-servers"></a>Per raggruppare i server di dispositivo  
  
1.  Aprire la console di Windows Server Update Services, fare doppio clic su **tutti i computer** e quindi fare clic su **Aggiungi gruppo di Computer**.  
  
    ![Aggiungere un gruppo di computer. ] (./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSAddComputerGroup.png "SQL_Server_PDW_WSUSAddComputerGroup")  
  
2.  Immettere il nome "APS" per il gruppo di computer e quindi fare clic su **Aggiungi**.  
  
    ![Immettere nome per il nuovo gruppo di computer. ] (./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSSpecifyGroupName.png "SQL_Server_PDW_WSUSSpecifyGroupName")  
  
3.  Fare clic su **tutti i computer** nuovamente, modificare lo stato nel **stato** dal menu a discesa per **qualsiasi**e quindi fare clic su **aggiornamento**. Potrebbe essere necessario espandere **tutti i computer** , fare clic sul controllo struttura ad albero a sinistra per visualizzare il nuovo gruppo appena aggiunto.  
  
    ![Impostare lo stato su qualsiasi e fare clic su Aggiorna. ] (./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChangeStatusToAny.png "SQL_Server_PDW_WSUSChangeStatusToAny")  
  
4.  Selezionare tutti i computer che fanno parte del dispositivo, pulsante destro del mouse e quindi fare clic su **Modifica appartenenza**.  
  
    ![Modificare l'appartenenza per tutti i computer PDW. ] (./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChangeMembership.png "SQL_Server_PDW_WSUSChangeMembership")  
  
5.  Selezionare il nuovo gruppo di computer creato facendo clic sulla casella di controllo e quindi facendo clic su **OK**.  
  
    ![Set Computer Group Membership](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSSetComputerGroupMembership.png "SQL_Server_PDW_WSUSSetComputerGroupMembership")  
  
6.  Selezionare il nuovo gruppo di computer, modificare il relativo **stato** a **qualsiasi**e quindi fare clic su **aggiornamento**. Tutti i computer dovrebbero ora essere assegnati a questo gruppo ed elencati nel riquadro di destra. È in genere, è possibile continuare quando i nodi visualizzare avvisi, ad esempio **questo nodo non è stato segnalato ancora stato**.  
  
    ![Impostare lo stato su qualsiasi e fare clic su Aggiorna. ] (./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChangeStatusAnyRefresh.png "SQL_Server_PDW_WSUSChangeStatusAnyRefresh")  
  
