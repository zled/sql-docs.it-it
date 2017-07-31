---
title: Help Viewer e contenuto offline per SQL Server | Microsoft Docs
ms.custom: 
ms.date: 06/27/2017
ms.prod: sql-non-specified
ms.technology: server-general
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2014
- SQL Server 2016
- SQL Server 2017
ms.assetid: 51f8a08c-51d0-41d8-8bc5-1cb4d42622fb
caps.latest.revision: 8
author: sabotta
ms.author: carlasab
ms.translationtype: HT
ms.sourcegitcommit: aad94f116c1a8b668c9a218b32372424897a8b4a
ms.openlocfilehash: ca52d53cf25fa0ead6abd9b870f4d8dab424d11a
ms.contentlocale: it-it
ms.lasthandoff: 07/31/2017

---
# <a name="help-viewer-and-offline-content-for-sql-server"></a>Help Viewer e contenuto offline per SQL Server
  
  
  
Questo articolo descrive come installare Help Viewer e come visualizzare la documentazione di SQL Server offline. L'articolo è relativo alla documentazione per [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)], SQL Server 2016 e SQL Server 2017. 

## <a name="install-help-viewer"></a>Installare Help Viewer
La tabella seguente elenca gli strumenti che installano Help Viewer a seconda della versione di SQL Server in uso. Installare uno degli strumenti elencati per installare Help Viewer.


|**Versione di SQL Server**|**Strumenti che installano Help Viewer**|**Versione di Help Viewer installata**|
|---------|---------|---------|
|SQL Server 2017<br>SQL Server 2016     |   [Versione più recente di SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)<br><br>[Versione più recente di SQL Server Data Tools per Visual Studio 2015](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt)<br><br>Visual Studio 2017 (*supporta solo SQL Server 2016*)  |  v2.x       |
|SQL Server 2014    | SQL Server 2014 Management Studio<br><br>Versioni di Visual Studio precedenti a Visual Studio 2012        |  v1.x       |


> [!IMPORTANT]
> SQL Server 2016 installa Help Viewer 1.1, che non può essere usato per visualizzare la documentazione di SQL Server 2016 e 2017.
> <br>
> <br>
> SQL Server 2017 non installa Help Viewer.
> <br>
> <br>
> Per installare Help Viewer con Visual Studio 2017 fare clic sulla scheda **Singoli componenti** nel **programma di installazione di Visual Studio**, fare clic su **Help Viewer** nella categoria **Strumenti per il codice** e quindi fare clic su **Installa**. 
> <br>
> <br>
> È possibile visualizzare la Guida locale per [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] con Help Viewer 2.x solo quando si usa l'opzione **Installa contenuto da disco**. 


## <a name="sql-server-2016-sql-server-2017-offline-content"></a>Contenuto non in linea di SQL Server 2016 e SQL Server 2017  
 
**Per installare il contenuto non in linea**  
1. Aprire Help Viewer avviando SQL Server Management Studio o Visual Studio e scegliendo **Aggiungi e rimuovi contenuto della Guida** dal menu **?**.  
2. Fare clic sulla scheda **Gestisci contenuto**.  
3. Per installare la Guida da un'origine online, fare clic su **Online** nell'area **Origine dell'installazione**.  
![HelpViewer2_ManageContent_OnlineSource](../release-notes/media/helpviewer2-managecontent-onlinesource.png)  
7. Fare clic su **Aggiungi** accanto alla documentazione che si vuole installare e quindi su **Aggiorna**.  
![HelpViewer2_ManageContent_AddContent](../release-notes/media/helpviewer2-managecontent-addcontent.png)     
  
   >[!IMPORTANT] 
   >In SQL Server Management Studio e Visual Studio l'applicazione Visualizzatore della Guida potrebbe bloccarsi durante l'aggiunta della documentazione. Per risolvere il problema, eseguire le operazioni seguenti. Per altre informazioni su questo problema, vedere [Il visualizzatore della Guida di Visual Studio si blocca](https://msdn.microsoft.com/library/mt654096.aspx).  
   >>Aprire il file %LOCALAPPDATA%\Microsoft\HelpViewer2.2\HlpViewer_SSMS16_en-US.settings | HlpViewer_VisualStudio14_en-US.settings nel Blocco note e impostare una data futura nel codice seguente. Questo file è disponibile nel computer locale solo se è stato installato Visual Studio. 
   >>>Memorizzare nella cache LastRefreshed="12/31/2017 00:00:00"  
  
    La tabella del sommario nel riquadro a sinistra viene automaticamente aggiornata per includere la documentazione aggiunta.  
![HelpViewer2_withContentInstalled](../release-notes/media/helpviewer2-withcontentinstalled.png)

1. (Facoltativo) La casella **Percorso archivio locale** nella scheda **Gestisci contenuto** indica il percorso in cui è installata la documentazione nel computer locale. Per spostare la documentazione in un percorso diverso, fare clic su **Sposta**, immettere il percorso di una cartella nel campo **A** della finestra di dialogo **Sposta contenuto** e quindi fare clic su **OK**.

   ![HelpViewer2_Move Content Dialog](../release-notes/media/helpviewer2-move-content-dialog.png)

   Dopo aver spostato il contenuto, il nuovo percorso viene visualizzato in **Percorso archivio locale**.
      
   >[!IMPORTANT]
   > Se viene visualizzato un messaggio che indica che l'operazione di spostamento non è riuscita, chiudere la finestra di messaggio, chiudere il visualizzatore della Guida e quindi riaprirlo. Il nuovo percorso per il contenuto dovrebbe ora essere visualizzato in **Percorso archivio locale**.   
 
## <a name="includesssql14mdincludessssql14-mdmd-offline-content"></a>[!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] Contenuto non in linea 
 
  
**Per installare il contenuto non in linea**  
1. Passare al [sito di download](https://www.microsoft.com/en-us/download/details.aspx?id=42557) per il contenuto della Guida e fare clic su **Scarica**.  
2. Fare clic su **Salva** nella finestra di messaggio per salvare il file SQLServer2014Documentation_*.exe nel computer.  

 Per ambienti protetti da firewall e proxy, salvare il download in un'unità USB o in un altro supporto portatile che possa essere usato nell'ambiente.   

3. Fare doppio clic sul file EXE per decomprimere il file del contenuto della Guida e salvarlo in una cartella locale o condivisa.  
4. Aprire **Gestione librerie della Guida** avviando SQL Server Management Studio o Visual Studio e scegliendo **Gestione impostazioni della Guida** dal menu **?**.  
5. Fare clic su **Installa contenuto da disco** e passare alla cartella in cui è stato decompresso il file del contenuto della Guida.  
  
     Selezionare Installa contenuto da disco  |Passare al file del contenuto della Guida   
     ---------|---------  
     ![HelpLibraryManager_MainPage_InstallFromDisk](../release-notes/media/helplibrarymanager-mainpage-installfromdisk.png)    | ![HelpLibraryManager_InstallContentFromDisk_dialog1](../release-notes/media/helplibrarymanager-installcontentfromdisk-dialog1.png)          
  
     >[!IMPORTANT]
     > Per evitare di installare contenuto della Guida locale che includa solo un sommario parziale, usare l'opzione **Installa contenuto da disco** in **Gestione librerie della Guida**.  
     >>Se è stata usata l'opzione **Installa contenuto da disco** e il visualizzatore della Guida mostra un sommario parziale, vedere questo [post di blog](https://blogs.msdn.microsoft.com/womeninanalytics/2016/06/21/troubleshoot-local-help-for-sql-server-2014/) per i passaggi di risoluzione del problema. 

8. Selezionare il file HelpContentSetup.msha, fare clic su **Apri** e quindi su **Avanti**.  
9. Fare clic su **Aggiungi** accanto alla documentazione che si vuole installare e quindi su **Aggiorna**.  
  
   ![HelpLibraryManager_InstallContentFromDisk_dialog2](../release-notes/media/helplibrarymanager-installcontentfromdisk-dialog2.png)  
10. Fare clic su **Fine** e quindi fare clic su **Esci**.
11. Aprire di nuovo **Gestione librerie della Guida**, fare clic su **Scegliere di utilizzare la Guida online o locale** e quindi su **I want to use local help** (Guida locale).
12. Aprire Help Viewer per visualizzare il contenuto facendo clic su **Visualizza Guida** nel menu **?**. Il contenuto installato verrà elencato nel sommario, nel riquadro a sinistra.  
  
    ![HelpViewer1_withContentInstalled_ZoomedIn](../release-notes/media/helpviewer1-withcontentinstalled-zoomedin.png)  
  
## <a name="view-online-content-in-help-viewer"></a>Visualizzare il contenuto online in Help Viewer

In Help Viewer v2.x è possibile visualizzare il contenuto online eseguendo una delle operazioni seguenti.

- In SQL Server Management Studio fare clic su **Visualizza Guida** nel menu **?**. La documentazione viene visualizzata in un browser.
![HelpViewer2_SSMS_ChooseOnlineORLocalHelp](../release-notes/media/helpviewer2-ssms-chooseonlineorlocalhelp.png)

- In Visual Studio fare clic su **Imposta preferenza Guida** nel menu **?** e quindi fare clic su **Avvia nel browser**. Quando si sceglie **Visualizza Guida** dal menu **?**, la documentazione viene visualizzata in un browser.

![HelpViewer2_VisualStudio_ChooseOnlineORLocalHelp](../release-notes/media/helpviewer2-visualstudio-chooseonlineorlocalhelp.png)   

In Help Viewer v1.x è possibile visualizzare il contenuto online eseguendo una delle operazioni seguenti.
1. Aprire **Gestione librerie della Guida** scegliendo **Gestione impostazioni della Guida** dal menu **?**.  
2. Nella finestra di dialogo **Gestione librerie della Guida** fare clic su **Scegliere di utilizzare la Guida online o locale**.  
  
   ![HelpLibraryManager_MainPage_ChooseOnlineORLocal.png](../release-notes/media/helplibrarymanager-mainpage-chooseonlineorlocal.png.png)  
3. Fare clic su **I want to use online help** (Guida in linea), scegliere **OK** e fare clic su **Esci**.  

   ![HelpLibraryManager_ChooseOnlineORLocalHelp_OnlineHelpSelected_dialog](../release-notes/media/helplibrarymanager-chooseonlineorlocalhelp-onlinehelpselected-dialog.png)

## <a name="f1-help-and-other-tips"></a>F1 Guida e altri suggerimenti

Quando si preme F1, l'argomento corrispondente viene visualizzato online. L'argomento non può essere visualizzato nella Guida locale.

Help Viewer non supporta le impostazioni del proxy né il formato ISO. 


## <a name="additional-information"></a>Informazioni aggiuntive
[Visualizzatore della Guida Microsoft - Visual Studio 2015](https://msdn.microsoft.com/library/hh580782.aspx)

