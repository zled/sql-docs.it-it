---
title: "Installare pacchetti R aggiuntivi su SQL Server | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "11/08/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 21456462-e58a-44c3-9d3a-68b4263575d7
caps.latest.revision: 16
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 16
---
# Installare pacchetti R aggiuntivi su SQL Server
In questo argomento viene descritto come installare i nuovi pacchetti R a un'istanza di [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] in un computer che dispone dell'accesso a Internet.

## <a name="1-locate-the-windows-binaries-in-zip-file-format"></a>1. Individuare i file binari di Windows nel formato file ZIP

Pacchetti R sono supportati su molte piattaforme. È necessario assicurarsi che il pacchetto che si desidera installare ha un formato binario per la piattaforma Windows. In caso contrario il pacchetto scaricato non funzionerà.

Ad esempio, per ottenere il pacchetto [FISHalyseR](http://bioconductor.org/packages/release/bioc/html/FISHalyseR.html) da Bioconductor:  
  
1.  Nell'elenco **Archivi dei pacchetti** , individuare la versione **binaria di Windows** .  
  
2.  Fare clic con il pulsante destro del mouse sul link al file ZIP, quindi selezionare  **Salva oggetto con nome**.  
  
3.  Passare alla cartella locale in cui vengono archiviati i pacchetti compressi, quindi fare clic su **Salva**.  
  
 Questo processo crea una copia locale del pacchetto. È quindi possibile installare il pacchetto o copiare il pacchetto compresso in un server che non dispone di accesso a Internet.  
  
  
## <a name="2-open-the-default-r-package-library-for-sql-server-r-services"></a>2. Aprire la raccolta di pacchetto predefinito R per i servizi di SQL Server R 

Passare alla cartella sul server in cui i pacchetti R associati a [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] sono stati installati. È importante installare pacchetti della libreria predefinita che viene associato all'istanza corrente. 

Per istruzioni su come individuare questa libreria, vedere [installazione e la gestione di pacchetti R](../../advanced-analytics/r-services/installing-and-managing-r-packages.md).

   Per ogni istanza in cui verrà eseguito un pacchetto, è necessario installare una copia separata dei pacchetti. Attualmente i pacchetti non possono essere condivisi tra più istanze.
     
  
## <a name="3-open-an-administrative-command-prompt"></a>3. Aprire un prompt dei comandi amministrativo 

Aprire R come amministratore.  È possibile farlo utilizzando il comando di Windows p, ropt, oppure utilizzando una delle utilità R.
  
### <a name="using-the-windows-command-prompt"></a>Uso del prompt dei comandi di Windows 

1. Aprire un prompt dei comandi di Windows come amministratore e passare alla directory in cui si trovano i file RTerm.Exe o RGui.exe.  
  
    In un'installazione predefinita, si tratta della directory **\bin** di R. Ad esempio, in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], gli strumenti R si trovano qui: 

    **Istanza predefinita**

     `C:\Program Files\MSSQL13.MSSQLSERVER\R_SERVICES\bin` 
 
     **Istanza denominata**
   
     `C:\Program files\MSSQL13.<instanceName>\R_SERVICES\bin\x64`  
  
2. Eseguire **R.exe**.  
  
### <a name="using-the-r-commandline-utilities"></a>Uso delle utilità della riga di comando di R 
  
1. Usare Esplora risorse per passare alla directory contenente gli strumenti di R.  
  
2. Fare doppio clic su **RGui.exe** o **RTerm.exe**, e selezionare **Esegui come amministratore**.  
## <a name="4-install-the-package"></a>4. Installare il pacchetto

Il comando per installare il pacchetto R dipende da se si desidera ottenere il pacchetto da Internet o da un file ZIP locale.  
  
### <a name="install-package-from-internet"></a>Installazione del pacchetto da Internet  
  
1.  In generale, utilizzare il comando seguente per installare un nuovo pacchetto da CRAN o uno dei siti mirror.  
  
    ```  
    install.packages("target_package_name")  
    ```
    
    Si noti che le virgolette doppie sono sempre obbligatorie per il nome del pacchetto.

2.  Per specificare la libreria in cui deve essere installato il pacchetto, utilizzare un comando simile al seguente per impostare il percorso della libreria:
    
    ```  
    lib.SQL <- "C:\\Program Files\\Microsoft SQL Server\\MSSQL13.MSSQLSERVER\\R_SERVICES\\library"    
    ```

    Si noti che per [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], attualmente è consentita libreria un solo pacchetto. Non installare i pacchetti in una raccolta di utenti o non sarà in grado di eseguire il pacchetto da [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].   
     
3.  Dopo aver definito il percorso di libreria, l'istruzione seguente installa il pacchetto più diffusi e1070 nella libreria del pacchetto utilizzata dai servizi di R.  
  
    ```  
    install.packages("e1071", lib = lib.SQL)  
    ```  
  
4.  Verrà richiesto un sito mirror da cui ottenere il pacchetto. Selezionare qualsiasi sito mirror utile per il percorso.  
  
    Per un elenco dei mirror CRAN correnti, vedere [questo sito](https://cran.r-project.org/mirrors.html).  
  
    > [!TIP]  
    >  Per evitare di selezionare un sito mirror ogni volta che si aggiunge un nuovo pacchetto, è possibile configurare l'ambiente di sviluppo di R in modo che usi sempre lo stesso repository.  
    >   
    >  Per eseguire questa operazione, modificare il file con estensione Rprofile delle impostazioni globali di R, quindi aggiungere la riga seguente:  
    >   
    >  `options(repos=structure(c(CRAN="<mirror site URL>")))`  
    >   
    >  Per informazioni dettagliate sulle preferenze e sugli altri file caricati all'avvio del runtime di R, eseguire questo comando in una console di R:  
    >   
    >  `?Startup`  
  
5.  Se il pacchetto di destinazione dipende da pacchetti aggiuntivi, il programma di installazione di R scaricherà automaticamente le dipendenze e le installerà.  
  
### <a name="manual-package-installation-or-installing-on-computer-with-no-internet-access"></a>Installazione manuale del pacchetto o l'installazione in computer senza accesso a Internet 

1. Se il pacchetto che si prevede di installare le dipendenze, ottenere i pacchetti richiesti anticipo e aggiungerle alla cartella con altri pacchetti di gestire i file compressi.

    > [!TIP]
    > 
    > Si consiglia di configurare un repository locale usando [miniCRAN](https://mran.revolutionanalytics.com/package/miniCRAN/) se è necessario supportare l'installazione offline frequenti dei pacchetti R.  
  
2.  Nel prompt dei comandi di R, digitare il comando seguente per specificare il percorso e il nome del pacchetto da installare:  
   
    ```  
    install.packages("C:\\Temp\\Downloaded packages\\mynewpackage.zip", repos=NULL)  
    ``` 
     
    Questo comando consente di estrarre il pacchetto R dal file ZIP locale, presupponendo che è stata salvata la copia nella directory `C:\Temp\Downloaded packages`, e installa il pacchetto (con le relative dipendenze) nella libreria R nel computer locale.  
  
3.  Se è stato modificato in precedenza nell'ambiente R nel computer, è necessario assicurarsi che la variabile di ambiente R `.libPath` utilizza solo un percorso, che fa riferimento alla cartella R_SERVICES per l'istanza.  
  
> [!NOTE]
> Se è stato installato Microsoft R Server (autonomo) oltre a servizi di SQL Server R, il computer avrà un'installazione separata di R con gli strumenti di R e librerie. I pacchetti vengono installati nella libreria R_SERVER vengono utilizzati solo da Microsoft R Server e non è accessibile [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
> 
>  Assicurarsi di utilizzare la libreria R_SERVICES durante l'installazione di pacchetti che si desidera utilizzare in SQL Server.

  
## <a name="see-also"></a>Vedere anche  
 [Impostare i servizi di SQL Server R &#40; nel Database &#41;](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)  
  
  