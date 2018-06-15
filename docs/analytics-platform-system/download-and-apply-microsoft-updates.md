---
title: Scaricare gli aggiornamenti Microsoft - Analitica piattaforma sistema | Documenti Microsoft
description: In questo argomento viene illustrato come scaricare gli aggiornamenti dal catalogo di Microsoft Update per Windows Server Update Services (WSUS) e applicare gli aggiornamenti ai server accessorio Analitica Platform System. Microsoft Update installerà tutti gli aggiornamenti per Windows e SQL Server. Windows Server Update Services è installato nella macchina virtuale VMM del dispositivo.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: b98a2be90f222fc2c531c1f1983f8882bdab640e
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
ms.locfileid: "31539521"
---
# <a name="download-and-apply-microsoft-updates-for-analytics-platform-system"></a>Scaricare e applicare gli aggiornamenti di Microsoft per Analitica Platform System
In questo argomento viene illustrato come scaricare gli aggiornamenti dal catalogo di Microsoft Update per Windows Server Update Services (WSUS) e applicare gli aggiornamenti ai server accessorio Analitica Platform System. Microsoft Update installerà tutti gli aggiornamenti per Windows e SQL Server. Windows Server Update Services è installato nella macchina virtuale VMM del dispositivo.  
  
## <a name="TOP"></a>Prima di iniziare  
  
> [!WARNING]  
> Non tentare di applicare gli aggiornamenti, se all'applicazione o qualsiasi componente accessorio è inattivo o non riuscito su stato. In tal caso, contattare il supporto tecnico per assistenza.  
>   
> Non si applicano Microsoft Updates mentre il dispositivo è in uso. L'applicazione degli aggiornamenti potrebbe nodi dello strumento riavviare il computer. Gli aggiornamenti da applicare durante una finestra di manutenzione quando il dispositivo non è in uso.  
  
### <a name="prerequisites"></a>Prerequisiti  
Prima di eseguire questi passaggi, è necessario:  
  
-   Configurare WSUS del dispositivo seguendo le istruzioni in [configurare Windows Server Update Services &#40;WSUS&#41; &#40;Analitica Platform System&#41;](configure-windows-server-update-services-wsus.md).  
  
-   Conoscenza delle informazioni di accesso account amministratore di dominio dell'infrastruttura.  
  
-   Disporre di un account di accesso con le autorizzazioni per accedere alla Console di Amministrazione sistema piattaforma Analitica e visualizzare informazioni sullo stato del dispositivo.  
  
-   Nella maggior parte dei casi, è necessario accedere ai server di fuori dell'accessorio WSUS. Per supportare questo scenario di utilizzo Analitica piattaforma del sistema DNS possono essere configurati per supportare un server d'inoltro nome esterno che consentirà di host Analitica Platform System e macchine virtuali (VM) utilizzare i server DNS esterni per la risoluzione dei nomi di fuori del dispositivo. Per altre informazioni, vedere [utilizzare un server d'inoltro di DNS per risolvere nomi DNS Non accessorio &#40;Analitica Platform System&#41;](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md).  
  
## <a name="bkmk_ImportUpdates"></a>Per scaricare e applicare aggiornamenti Microsoft  
  
#### <a name="verify-the-appliance-state-indicators"></a>Verificare gli indicatori di stato del dispositivo  
  
1.  Aprire la Console di amministrazione e passare alla pagina di stato dello strumento. Per altre informazioni, vedere [monitorare il dispositivo tramite la Console di amministrazione &#40;Analitica Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
2.  Verificare gli indicatori di stato per tutti i nodi allo stato del dispositivo.  
  
    -   È possibile proseguire con il colore verde o indicatori NA.  
  
    -   Restituire errori avviso (giallo) non critici. In alcuni casi i messaggi di avviso non verranno bloccata gli aggiornamenti. Se è presente un errore del volume disco non critiche che non è presente nell'unità C:\, è possibile procedere al passaggio successivo prima di risolvere l'errore del volume del disco.  
  
    -   Prima di continuare, è necessario risolvere la maggior parte degli indicatori rossi. Se sono presenti errori del disco, è possibile utilizzare la pagina degli avvisi di Console di amministrazione per verificare di non più di un errore di disco all'interno di ogni server o un array SAN. In caso di errore non più di un disco in ogni server o un array SAN, è possibile procedere al passaggio successivo prima di correggere gli errori del disco. Assicurarsi di contattare il supporto tecnico Microsoft per risolvere gli errori di disco appena possibile.  
  
#### <a name="synchronize-the-wsus-server"></a>Sincronizzare il server WSUS  
  
1.  Accedere alla macchina virtuale VMM come amministratore di dominio.  
  
2.  Nel **Dashboard di Server Manager**via il **strumenti** menu, fare clic su **Windows Server Update Services** (**wsus.msc**).  
  
3.  Nella Console di amministrazione di WSUS, fare clic su **sincronizzazioni**.  
  
4.  Se la sincronizzazione non è in esecuzione, fare clic su **Sincronizza** nel riquadro di destra. Nel riquadro inferiore, saranno presenti uno stato di sincronizzazione. Attendere la sincronizzazione è stata completata.  
  
#### <a name="approve-microsoft-updates-in-wsus"></a>Approvare gli aggiornamenti Microsoft in WSUS  
  
1.  Nel riquadro a sinistra della console di Windows Server Update Services, fare clic su **tutti gli aggiornamenti**.  
  
2.  Nel **tutti gli aggiornamenti** riquadro, fare clic su di **approvazione** dal menu a discesa, impostare **approvazione** a **tutti tranne i rifiutati**. Fare clic su di **stato** dal menu a discesa, impostare **stato** a **qualsiasi**. Fare clic su **Aggiorna**.  
  
    Fare doppio clic su di **titolo** colonna e selezionare **lo stato del File** per verificare lo stato del file dopo il completamento del download.  
  
    È inoltre possibile selezionare **gli aggiornamenti critici** o **gli aggiornamenti della sicurezza** in sinistro riquadro e visualizzare gli aggiornamenti disponibili per queste categorie.  
  
    ![Selezionare tutti gli aggiornamenti e impostare lo stato su qualsiasi. ] (./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUSSelectAllUpdates.png "SQL_Server_PDW_WSUSSelectAllUpdates")  
  
3.  Selezionare tutti gli aggiornamenti e quindi fare clic su di **Approva** collegamento nel riquadro di destra.  
  
    È possibile anche fare doppio clic sugli aggiornamenti selezionati e quindi fare clic su **Approva**. Può essere richiesto di accettare il "Software condizioni di licenza Microsoft". In questo caso, fare clic su **accetto** nella finestra per continuare.  
  
    ![Selezionare tutti gli aggiornamenti applicabili e fare clic su Approva. ] (./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUSSelectApprove.png "SQL_Server_PDW_WSUSSelectApprove")  
  
4.  Selezionare il gruppo di server appliance creato nella [configurare Windows Server Update Services &#40;WSUS&#41; &#40;Analitica Platform System&#41;](configure-windows-server-update-services-wsus.md).  
  
5.  Fare clic su **approvati per l'installazione**, quindi fare clic su **OK**.  
  
    ![Approvare gli aggiornamenti per il gruppo di computer. ] (./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUSSelectApprovalType.png "SQL_Server_PDW_WSUSSelectApprovalType")  
  
6.  Nel **stato approvazione** della finestra di dialogo quando il processo di approvazione è stato completato, fare clic su **Chiudi**.  
  
    ![Chiudi finestra quando gli aggiornamenti vengono approvati. ] (./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUSCloseApprovalProgressWindow.png "SQL_Server_PDW_WSUSCloseApprovalProgressWindow")  
  
#### <a name="verify-that-the-updates-are-in-wsus"></a>Verificare che siano gli aggiornamenti di WSUS  
  
-  Verificare lo stato del file di tutti gli aggiornamenti. Ogni file deve avere un'icona di freccia verde a sinistra del titolo. Indica che il file è pronto per l'installazione.  
  
    ![Lo stato del file ha esito positivo](./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUS_File_Status.png "SQL_Server_PDW_WSUS_File_Status")  
  
    Prima di installare gli aggiornamenti, assicurarsi che siano tutti scaricati e resi disponibili nella console di WSUS.  
  
#### <a name="to-verify-that-all-updates-are-downloaded"></a>Per verificare che tutti gli aggiornamenti vengono scaricati  
  
-  Controllare il **stato Download** degli aggiornamenti nella console di WSUS come illustrato nella schermata seguente. Verificare che **aggiornamenti che richiedono file** è 0 per verificare che tutti gli aggiornamenti vengono scaricati. Se questo numero è maggiore di zero, si potrebbe essere necessario tornare indietro e approvare aggiornamenti aggiuntivi.  
  
    ![Verificare che tutti gli aggiornamenti vengono scaricati. ] (./media/download-and-apply-microsoft-updates/SQL_Server_PDS_WSUS_VerifyDownloadUpdateJPG.png "SQL_Server_PDS_WSUS_VerifyDownloadUpdateJPG")  
  
#### <a name="apply-microsoft-updates"></a>Applicare aggiornamenti Microsoft  
  
1.  Prima di iniziare, aprire il [monitorare il dispositivo tramite la Console di amministrazione &#40;Analitica Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md), fare clic sui **stato dello strumento** scheda e verificare che il  **Cluster** e **rete** colonne Mostra verde (o NA) per tutti i nodi. Se in una di queste colonne sono presenti eventuali avvisi, il dispositivo potrebbe non essere in grado di installare correttamente gli aggiornamenti. Risolvere tutti gli avvisi esistenti nel **Cluster** e **rete** colonne prima di procedere.  
  
2.  Eseguire l'accesso di *< nome_dominio > * * *-HST01** nodo come amministratore di dominio dell'infrastruttura.  
  
3.  Per applicare tutti gli aggiornamenti approvati per Windows Server Update Services, eseguire il programma di aggiornamento. Vedere [eseguire il programma di aggiornamento](#RunUpdateWizard) sotto per le istruzioni.  
  
#### <a name="verify-the-updates-on-all-nodes"></a>Verificare gli aggiornamenti in tutti i nodi  
  
1.  Dal nodo di VMM, avviare la Console di amministrazione di WSUS. Questa applicazione è reperibile nella **avviare**, **strumenti di amministrazione**, **Windows Server Update Services**.  
  
2.  Espandere **computer**.  
  
3.  Espandere **tutti i computer**.  
  
4.  Selezionare il gruppo di server appliance creato nella [configurare Windows Server Update Services &#40;WSUS&#41; &#40;Analitica Platform System&#41;](configure-windows-server-update-services-wsus.md).  
  
5.  Nel **stato** menu a discesa, seleziona **qualsiasi** e fare clic su **aggiornamento**.  
  
6.  Espandere **servizi di aggiornamento**, *<appliance name>*- VMM, **aggiornamenti**, **tutti gli aggiornamenti**, dove *<appliance name>* è il nome del dispositivo.  
  
7.  Nel **tutti gli aggiornamenti** finestra set **approvazione** a **tutti tranne i rifiutati**.  
  
8.  Nel **tutti gli aggiornamenti** finestra impostare **stato** a **non riusciti o necessari**.  
  
9. Fare clic su **Aggiorna**.  
  
10. Se **aggiornamenti necessari** è maggiore di zero, contattare il supporto tecnico per assistenza.  
  
#### <a name="ensure-there-are-no-critical-alerts-in-the-sql-server-pdw-admin-console"></a>Verificare che non siano presenti avvisi critici nella Console di amministrazione di SQL Server PDW  
  
1.  Aprire la Console di amministrazione, fare clic sulla scheda stato dello strumento. Vedere [monitorare il dispositivo tramite la Console di amministrazione &#40;Analitica Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md).  
  
2.  Verificare che il **Cluster** e **rete** colonne Mostra verde (o NA) per tutti i nodi. Se in una di queste colonne sono presenti eventuali avvisi, il dispositivo potrebbe non essere in grado di installare correttamente gli aggiornamenti. Contattare il supporto tecnico se esistono eventuali avvisi critici.  
  
## <a name="RunUpdateWizard"></a>Eseguire il programma di aggiornamento  
Seguire queste istruzioni per eseguire il programma di aggiornamento del sistema della piattaforma Analitica.  
  
> [!NOTE]  
> Il sistema WSUS è progettato per eseguire in modo asincrono potrebbe richiedere del tempo per applicare completamente tutti gli aggiornamenti. Avvio di un aggiornamento consente di pianificare un aggiornamento, ma non garantisce l'attività di aggiornamento immediato.  
  
1.  Assicurarsi di essere connessi a nodo HST01 come amministratore di dominio dell'infrastruttura.  
  
2.  Aprire una finestra del prompt dei comandi e immettere i comandi seguenti. Sostituire *<parameter>* con le informazioni designate.  
  
**Per eseguire l'aggiornamento di Microsoft:**  
  
```  
C:\pdwinst\media\setup.exe /action="MicrosoftUpdate" /DomainAdminPassword="<password>"  
```  
  
**Per segnalare lo stato di Microsoft Update:**  
  
```  
C:\pdwinst\media\setup.exe /action="ReportMicrosoftUpdateClientStatus" /DomainAdminPassword="<password>"  
```  
  
## <a name="see-also"></a>Vedere anche  
[Disinstallazione di aggiornamenti Microsoft &#40;Analitica Platform System&#41;](uninstall-microsoft-updates.md)  
[Applicare aggiornamenti rapidi di sistema della piattaforma Analitica &#40;Analitica Platform System&#41;](apply-analytics-platform-system-hotfixes.md)  
[Disinstallare Analitica piattaforma sistema hotfix &#40;Analitica Platform System&#41;](uninstall-analytics-platform-system-hotfixes.md)  
[Manutenzione del software &#40;Analitica Platform System&#41;](software-servicing.md)  
  
