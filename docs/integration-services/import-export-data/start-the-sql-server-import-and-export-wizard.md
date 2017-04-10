---
title: "Avviare l&#39;Importazione/Esportazione guidata SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Importazione/Esportazione guidata SQL Server"
  - "avvio di Importazione/Esportazione guidata SQL Server"
  - "importazione ed esportazione guidate"
  - "avvio di importazione ed esportazione guidate"
ms.assetid: 5fc4f6d1-1f6f-444e-9aeb-827f85e1c405
caps.latest.revision: 130
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 112
---
# Avviare l&#39;Importazione/Esportazione guidata SQL Server
È possibile avviare l'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nei modi seguenti.
-   Dal [menu Start](#startStart) o dal [prompt dei comandi](#startCmd), per importare o esportare in una qualsiasi origine dati supportata.
-   Da [SQL Server Management Studio (SSMS)](#startSSMS), per importare o esportare da SQL Server.
-   Da [Visual Studio con SQL Server Data Tools (SSDT)](#startVS), se è aperto un progetto di SQL Server Integration Services.

Questo argomento descrive solo come **avviare** la procedura guidata.
-   Per una panoramica della procedura guidata, vedere [Importare ed esportare dati con l'Importazione/Esportazione guidata SQL Server](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).
-   Per informazioni sui passaggi della procedura guidata, selezionare la pagina desiderata nel menu di navigazione del contenuto. Per ogni pagina della procedura guidata è disponibile una pagina di documentazione separata. In alternativa, premere il tasto F1 da qualsiasi pagina o finestra di dialogo della procedura guidata per visualizzare la documentazione relativa alla pagina corrente.

**Ottenere la procedura guidata.** Se si vuole eseguire la procedura guidata, ma [!INCLUDE[msCoName] (../Token/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è disponibile nel computer, è possibile installare l'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installando SQL Server Data Tools (SSDT). Per altre informazioni, vedere [Scaricare SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx).  

## <a name="a-namestartstarta-start-the-wizard-from-the-start-menu"></a><a name="startStart"></a> Avviare la procedura guidata dal menu Start  
1.  Scegliere **Tutte le app** dal menu **Start**.
2.  Trovare ed espandere **Microsoft SQL Server 2016**.
3.  Fare clic su una delle opzioni seguenti.
  
    -   **Import. ed esport. dati di SQL Server 2016 (64 bit)**
          
    -   **Import. ed esport. dati di SQL Server 2016 (32 bit)**  
  
Eseguire la versione a 64 bit della procedura guidata a meno che l'origine dati non richieda un provider di dati a 32 bit.
 
![Avviare la procedura guidata da Start](../../integration-services/import-export-data/media/start-wizard-start.jpg)
  
## <a name="a-namestartcmda-start-the-wizard-from-the-command-prompt"></a><a name="startCmd"></a> Avviare la procedura guidata dal prompt dei comandi  
In una finestra del prompt dei comandi eseguire **DTSWizard.exe** da una delle posizioni seguenti.  
  
-   **C:\Programmi\Microsoft SQL Server\130\DTS\Binn** per la versione a 64 bit.  
  
-   **C:\Programmi (x86)\Microsoft SQL Server\130\DTS\Binn** per la versione a 32 bit.  
  
Eseguire la versione a 64 bit della procedura guidata a meno che l'origine dati non richieda un provider di dati a 32 bit.

![Avviare la procedura guidata dal prompt dei comandi](../../integration-services/import-export-data/media/start-wizard-cmd.jpg)  
  
## <a name="a-namestartssmsa-start-the-wizard-from-sql-server-management-studio-ssms"></a><a name="startSSMS"></a> Avviare la procedura guidata da SQL Server Management Studio (SSMS)  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
2.  Espandere **Database**.
3.  Fare clic con il pulsante destro del mouse su un database.
4.  Scegliere **Attività**.
5.  Fare clic su una delle opzioni seguenti.
  
    -   **Importare dati**
      
    -   **Esportare dati**  

![Avviare la procedura guidata da SQL Server Management Studio](../../integration-services/import-export-data/media/start-wizard-ssms.jpg) 

Se SQL Server non è installato o è installato senza SQL Server Management Studio, vedere [Scaricare SQL Server Management Studio (SSMS)](https://msdn.microsoft.com/library/mt238290.aspx).
    
## <a name="a-namestartvsa-start-the-wizard-from-visual-studio-with-sql-server-data-tools-ssdt"></a><a name="startVS"></a> Avviare la procedura guidata da Visual Studio con SQL Server Data Tools (SSDT)  
 In Visual Studio con [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], eseguire una delle operazioni seguenti se è aperto un progetto di Integration Services.  
  
-   Scegliere **Importazione ed esportazione guidata di SSIS** dal menu **Progetto**. 

    ![Avviare la procedura guidata da un progetto](../../integration-services/import-export-data/media/start-wizard-project.jpg) 
    
    \- oppure
    
-   In Esplora soluzioni fare clic con il pulsante destro del mouse sulla cartella **Pacchetti SSIS** e quindi scegliere **Importazione ed esportazione guidata di SSIS**.

    ![Avviare la procedura guidata da un pacchetto](../../integration-services/import-export-data/media/start-wizard-packages.jpg)

Se Visual Studio non è installato o è installato senza SQL Server Data Tools, vedere [Scaricare SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx). 

## <a name="get-help-while-the-wizard-is-running"></a>Visualizzare la Guida durante l'esecuzione della procedura guidata
> [!TIP] Premere il tasto F1 da qualsiasi pagina o finestra di dialogo della procedura guidata per visualizzare la documentazione relativa alla pagina corrente.   

 ## <a name="whats-next"></a>Operazioni successive  
 La prima pagina visualizzata all'avvio della procedura guidata è **Importazione/Esportazione guidata SQL Server**. Non è necessario eseguire alcuna operazione in questa pagina. Per altre informazioni, vedere [Importazione/Esportazione guidata SQL Server](../../integration-services/import-export-data/welcome-to-sql-server-import-and-export-wizard.md).  
  
  