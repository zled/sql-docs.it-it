---
title: Visualizzatore della Guida per SQL Server | Microsoft Docs
ms.custom: 
ms.date: 02/15/2017
ms.prod: sql-non-specified
ms.technology: server-general
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2014
- SQL Server 2016
ms.assetid: 51f8a08c-51d0-41d8-8bc5-1cb4d42622fb
caps.latest.revision: 8
author: sabotta
ms.author: carlasab
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: fc2435ccea3b01328c3c4623e62fbf12ee53e400
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="help-viewer-for-sql-server"></a>Visualizzatore della Guida per SQL Server
  
  
  
Questo articolo contiene le procedure per installare la Guida locale e visualizzare la Guida locale online. L'articolo riguarda Microsoft Help Viewer 1.1 e 2.2 e include la documentazione per [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] e [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)]. 

>[!IMPORTANT]
>Il visualizzatore della Guida non supporta impostazioni del proxy né il formato ISO.  

>**F1 e Guida**
>>Quando si preme F1, l'argomento corrispondente viene visualizzato online. L'argomento non può essere visualizzato nella Guida locale.

## <a name="includesscurrentmdincludessscurrent-mdmd-and-help-viewer-22"></a>[!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)] e Help Viewer 2.2  
Help Viewer 2.2 è disponibile in [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)] Management Studio a partire dalla versione di anteprima di aprile 2016 (13.0.12500.29) e in Visual Studio 2015.  

> [![Download di SSMS](../release-notes/media/download.png)](https://msdn.microsoft.com/library/mt238290.aspx) **[Scaricare la versione più recente di SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx)**  

**Per installare la Guida locale in modo da usarla con Help Viewer 2.2**  
1. Aprire Help Viewer 2.2 avviando SQL Server Management Studio o Visual Studio e scegliendo **Aggiungi e rimuovi contenuto della Guida** dal menu **?**.  
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
  
**Per visualizzare la Guida locale o la Guida online in SQL Server Management Studio**  
* Per visualizzare la Guida locale, scegliere **Aggiungi e rimuovi contenuto della Guida** dal menu **?** e quindi fare clic sulla scheda **Help Viewer - Home page** per visualizzare la documentazione.  
    >[!NOTE]
    >Il testo **Help Viewer - Home page** cambia in base all'argomento selezionato nel sommario.   
* Per visualizzare la Guida online, scegliere **Visualizza Guida** dal menu **?**. La documentazione viene visualizzata in un browser.  
![HelpViewer2_SSMS_ChooseOnlineORLocalHelp](../release-notes/media/helpviewer2-ssms-chooseonlineorlocalhelp.png)  
  
  
**Per visualizzare la Guida locale o la Guida online in Visual Studio**  
* Scegliere **Imposta preferenza Guida** dal menu **?** e quindi eseguire una delle operazioni seguenti.  
   * Fare clic su **Avvia nel browser** per visualizzare la Guida online. Quando si sceglie **Visualizza Guida** dal menu **?**, la documentazione viene visualizzata in un browser.  
   * Fare clic su **Avvia in Help Viewer** per visualizzare la Guida locale. Quando si sceglie **Visualizza Guida** dal menu **?**, la documentazione viene visualizzata nel visualizzatore della Guida.  
     
     ![HelpViewer2_VisualStudio_ChooseOnlineORLocalHelp](../release-notes/media/helpviewer2-visualstudio-chooseonlineorlocalhelp.png)  
  
  
## <a name="includesssql14mdincludessssql14-mdmd-and-help-viewer-11"></a>[!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] e Help Viewer 1.1  
 Help Viewer 1.1 è disponibile in [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] Management Studio e nelle versioni di Visual Studio precedenti a Visual Studio 2012.   
 
>[!NOTE]
> È anche possibile visualizzare la Guida locale per [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] usando Help Viewer 2.2 solo quando si usa l'opzione **Installa contenuto da disco**. Help Viewer 2.2 è disponibile in [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)] Management Studio a partire dalla versione di anteprima di aprile 2016 (13.0.12500.29) e in Visual Studio 2015. 
   
**Per installare la Guida locale in modo da usarla con Help Viewer 1.1**  
1. Passare al [sito di download](https://www.microsoft.com/en-us/download/details.aspx?id=42557) per il contenuto della Guida e fare clic su **Scarica**.  
2. Fare clic su **Salva** nella finestra di messaggio per salvare il file SQLServer2014Documentation_*.exe nel computer.  
   >[!NOTE]
   >Per ambienti protetti da firewall e proxy, salvare il download in un'unità USB o in un altro supporto portatile che possa essere usato nell'ambiente.   
3. Fare doppio clic sul file EXE per decomprimere il file del contenuto della Guida e salvarlo in una cartella locale o condivisa.  
4. Aprire **Gestione librerie della Guida** avviando SQL Server Management Studio o Visual Studio e scegliendo **Gestione impostazioni della Guida** dal menu **?**.  
7. Fare clic su **Installa contenuto da disco** e passare alla cartella in cui è stato decompresso il file del contenuto della Guida.  
  
Selezionare Installa contenuto da disco  |Passare al file del contenuto della Guida   
---------|---------  
![HelpLibraryManager_MainPage_InstallFromDisk](../release-notes/media/helplibrarymanager-mainpage-installfromdisk.png)    | ![HelpLibraryManager_InstallContentFromDisk_dialog1](../release-notes/media/helplibrarymanager-installcontentfromdisk-dialog1.png)          
  
>[!IMPORTANT]
> Per evitare di installare contenuto della Guida locale che includa solo un sommario parziale, usare l'opzione **Installa contenuto da disco** in **Gestione librerie della Guida**.  
>>Se è stata usata l'opzione **Installa contenuto da disco** e il visualizzatore della Guida mostra un sommario parziale, vedere questo [post di blog](https://blogs.msdn.microsoft.com/womeninanalytics/2016/06/21/troubleshoot-local-help-for-sql-server-2014/) per i passaggi di risoluzione del problema. 

8. Selezionare il file HelpContentSetup.msha, fare clic su **Apri** e quindi su **Avanti**.  
9. Fare clic su **Aggiungi** accanto alla documentazione che si vuole installare e quindi su **Aggiorna**.  
  
   ![HelpLibraryManager_InstallContentFromDisk_dialog2](../release-notes/media/helplibrarymanager-installcontentfromdisk-dialog2.png)  
10. Fare clic su **Fine**, fare clic su **Esci** e quindi aprire il visualizzatore della Guida per visualizzare il contenuto scegliendo **Visualizza Guida** dal menu **?**. Il contenuto installato verrà elencato nel sommario, nel riquadro a sinistra.  
  
    ![HelpViewer1_withContentInstalled_ZoomedIn](../release-notes/media/helpviewer1-withcontentinstalled-zoomedin.png)  
  
**Per visualizzare la Guida locale o la Guida online**  
1. Aprire **Gestione librerie della Guida** scegliendo **Gestione impostazioni della Guida** dal menu **?**.  
2. Nella finestra di dialogo **Gestione librerie della Guida** fare clic su **Scegliere di utilizzare la Guida online o locale**.  
  
   ![HelpLibraryManager_MainPage_ChooseOnlineORLocal.png](../release-notes/media/helplibrarymanager-mainpage-chooseonlineorlocal.png.png)  
3. Eseguire una delle operazioni seguenti, fare clic su **OK** e quindi su **Esci**.  
   * Fare clic sull'opzione per l'uso della Guida online**** .  
   * Fare clic sull'opzione per l'uso della Guida locale**** .  
  
   ![HelpLibraryManager_ChooseOnlineORLocalHelp_OnlineHelpSelected_dialog](../release-notes/media/helplibrarymanager-chooseonlineorlocalhelp-onlinehelpselected-dialog.png)  
  
Se è stato specificato di usare la Guida online, quando si sceglie **Visualizza Guida** dal menu **?** il browser viene avviato e visualizza l'articolo [Documentazione online di SQL Server 2014](https://msdn.microsoft.com/library/ms130214(v=sql.120).aspx) su MSDN. Se si è specificato di usare la Guida locale, quando si fa clic su **Visualizza Guida** viene avviato il visualizzatore della Guida.  

## <a name="additional-information"></a>Informazioni aggiuntive
[Visualizzatore della Guida Microsoft - Visual Studio 2015](https://msdn.microsoft.com/library/hh580782.aspx)

