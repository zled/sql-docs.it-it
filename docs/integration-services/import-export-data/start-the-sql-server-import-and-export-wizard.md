---
title: Avviare SQL Server importazione / esportazione guidata | Documenti Microsoft
ms.custom: 
ms.date: 06/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Import and Export Wizard
- starting SQL Server Import and Export Wizard
- Import and Export Wizard
- starting Import and Export Wizard
ms.assetid: 5fc4f6d1-1f6f-444e-9aeb-827f85e1c405
caps.latest.revision: 130
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 4fd91a36594a8d0d50e3f4eb8490497d6fe0e172
ms.contentlocale: it-it
ms.lasthandoff: 09/27/2017

---
# <a name="start-the-sql-server-import-and-export-wizard"></a>Avviare l'Importazione/Esportazione guidata SQL Server

 > Per contenuti relativi a versioni precedenti di SQL Server, vedere [eseguire SQL Server di importazione / esportazione guidata](https://msdn.microsoft.com/en-US/library/ms140052(SQL.120).aspx).

Avviare il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] importazione / esportazione guidata in uno dei metodi descritti in questo argomento per importare i dati ed esportare dati da qualsiasi origine dati supportata.

> [!IMPORTANT]
> Questo argomento descrive solo come **avviare** la procedura guidata. Se si sta cercando un altro elemento, vedere [correlati e i contenuti](#related).

È possibile avviare la procedura guidata:
-   Dal [menu Start](#startStart).
-   Dal [prompt dei comandi](#startCmd). 
-   Da [SQL Server Management Studio (SSMS)](#startSSMS).
-   Da [Visual Studio con SQL Server Data Tools (SSDT)](#startVS).

## <a name="prerequisite---is-the-wizard-installed-on-your-computer"></a>Prerequisito: È la procedura guidata installata nel computer?
Se si vuole eseguire la procedura guidata, ma [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è disponibile nel computer, è possibile installare l'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installando SQL Server Data Tools (SSDT). Per altre informazioni, vedere [Scaricare SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx).

> [!NOTE]
> Per utilizzare la versione a 64 bit di SQL Server di importazione / esportazione guidata, è necessario installare SQL Server. SQL Server Data Tools (SSDT) e SQL Server Management Studio (SSMS) sono applicazioni a 32 bit e installare solo i file a 32 bit, inclusa la versione a 32 bit della procedura guidata.

## <a name="startStart"></a> menu Start  
### <a name="start-the-sql-server-import-and-export-wizard-from-the-start-menu"></a>Avviare SQL Server di importazione / esportazione guidata dal menu Start
1.  Nel **avviare** menu, individuare ed espandere **Microsoft SQL Server 2016**.
3.  Fare clic su una delle opzioni seguenti.
  
    -   **Import. ed esport. dati di SQL Server 2016 (64 bit)**
          
    -   **Import. ed esport. dati di SQL Server 2016 (32 bit)**  
  
    Eseguire la versione a 64 bit della procedura guidata a meno che l'origine dati non richieda un provider di dati a 32 bit.
 
    ![Avviare la procedura guidata da Start](../../integration-services/import-export-data/media/start-wizard-start.jpg)
  
## <a name="startCmd"></a> Command prompt
### <a name="start-the-sql-server-import-and-export-wizard-from-the-command-prompt"></a>Avviare SQL Server di importazione / esportazione guidata dal prompt dei comandi  
In una finestra del prompt dei comandi eseguire **DTSWizard.exe** da una delle posizioni seguenti.  
  
-   **C:\Programmi\Microsoft SQL Server\130\DTS\Binn** per la versione a 64 bit.  
  
-   **C:\Programmi (x86)\Microsoft SQL Server\130\DTS\Binn** per la versione a 32 bit.  
  
Eseguire la versione a 64 bit della procedura guidata a meno che l'origine dati non richieda un provider di dati a 32 bit.

![Avviare la procedura guidata dal prompt dei comandi](../../integration-services/import-export-data/media/start-wizard-cmd.jpg)  
  
## <a name="startSSMS"></a> SQL Server Management Studio (SSMS)
### <a name="start-the-sql-server-import-and-export-wizard-from-sql-server-management-studio-ssms"></a>Avviare SQL Server importazione / esportazione guidata SQL Server Management Studio (SSMS)    
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]connettersi a un'istanza del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)].
    
2.  Espandere **Database**.
3.  Fare clic con il pulsante destro del mouse su un database.
4.  Scegliere **Attività**.
5.  Fare clic su una delle opzioni seguenti.
  
    -   **Importare dati**
      
    -   **Esportare dati**  

    ![Avviare la procedura guidata da SQL Server Management Studio](../../integration-services/import-export-data/media/start-wizard-ssms.jpg) 

Se SQL Server non è installato o è installato senza SQL Server Management Studio, vedere [Scaricare SQL Server Management Studio (SSMS)](../../ssms/download-sql-server-management-studio-ssms.md).
  
## <a name="startVS"></a>Visual Studio
### <a name="start-the-sql-server-import-and-export-wizard-from-visual-studio-with-sql-server-data-tools-ssdt"></a>Avviare il Server importazione / esportazione guidata SQL da Visual Studio con SQL Server Data Tools (SSDT) 
 In Visual Studio con [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], eseguire una delle operazioni seguenti se è aperto un progetto di Integration Services. 
  
-   Scegliere **Importazione ed esportazione guidata di SSIS** dal menu **Progetto**. 

    ![Avviare la procedura guidata da un progetto](../../integration-services/import-export-data/media/start-wizard-project.jpg) 
    
    \- oppure
    
-   In Esplora soluzioni fare clic con il pulsante destro del mouse sulla cartella **Pacchetti SSIS** e quindi scegliere **Importazione ed esportazione guidata di SSIS**.

    ![Avviare la procedura guidata da un pacchetto](../../integration-services/import-export-data/media/start-wizard-packages.jpg)

Se Visual Studio non è installato o è installato senza SQL Server Data Tools, vedere [Scaricare SQL Server Data Tools (SSDT)](../../ssdt/download-sql-server-data-tools-ssdt.md).

## <a name="get-the-wizard"></a>Ottenere la procedura guidata
Se si vuole eseguire la procedura guidata, ma [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è disponibile nel computer, è possibile installare l'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installando SQL Server Data Tools (SSDT). Per altre informazioni, vedere [Scaricare SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx).

## <a name="get-help-while-the-wizard-is-running"></a>Visualizzare la Guida durante l'esecuzione della procedura guidata
> [!TIP]
> Premere il tasto F1 da qualsiasi pagina o finestra di dialogo della procedura guidata per visualizzare la documentazione relativa alla pagina corrente.   

 ## <a name="whats-next"></a>Operazioni successive  
 La prima pagina visualizzata all'avvio della procedura guidata è **Importazione/Esportazione guidata SQL Server**. Non è necessario eseguire alcuna operazione in questa pagina. Per altre informazioni, vedere [Importazione/Esportazione guidata SQL Server](../../integration-services/import-export-data/welcome-to-sql-server-import-and-export-wizard.md).  
  
## <a name="related"></a>Contenuto e le attività correlate  
 Ecco alcune semplici attività.
-   **Vedere un esempio semplice di funzionamento della procedura guidata.**

    -   **Se si preferisce visualizzare schermate.** Esaminiamo questo semplice esempio end-to-end in una singola pagina - [iniziare con questo semplice esempio di importazione / esportazione guidata](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md).

    -   **Se si preferisce guardare un video.** Guardare questo video di quattro minuti dal YouTube che illustra la procedura guidata e viene spiegato chiaramente in modo semplice e come esportare i dati in Excel - [utilizzando SQL Server di importazione / esportazione guidata per l'esportazione in Excel](https://go.microsoft.com/fwlink/?linkid=829049).

-   **Ulteriori informazioni sul funzionamento della procedura guidata.**

    -   **Ulteriori informazioni sulla procedura guidata.** Per una panoramica della procedura guidata, vedere [Importare ed esportare dati con l'Importazione/Esportazione guidata SQL Server](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).

    -   **Informazioni sui passaggi della procedura guidata.** Se si sta cercando informazioni sui passaggi della procedura guidata, vedere [i passaggi in SQL Server importazione / esportazione guidata](../../integration-services/import-export-data/steps-in-the-sql-server-import-and-export-wizard.md). È inoltre disponibile una pagina separata della documentazione per ogni pagina della procedura guidata.

    -   **Informazioni su come connettersi a origini dati e destinazioni.** Se si sta cercando informazioni su come connettersi ai dati, selezionare la pagina desiderata dall'elenco, [connessione a origini dati con SQL Server di importazione / esportazione guidata](../../integration-services/import-export-data/connect-to-data-sources-with-the-sql-server-import-and-export-wizard.md). È una pagina separata della documentazione per ognuna delle diverse origini dati di uso comune.



