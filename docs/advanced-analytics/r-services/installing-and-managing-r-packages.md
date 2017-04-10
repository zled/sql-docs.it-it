---
title: "Installazione e gestione dei pacchetti R | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "R"
ms.assetid: 4d426cf6-a658-4d9d-bfca-4cdfc8f1567f
caps.latest.revision: 11
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 11
---
# Installazione e gestione dei pacchetti R
 Soluzioni R che viene eseguito in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] devono usare i pacchetti vengono installati nella libreria predefinita R. In genere soluzioni R farà riferimento a librerie utente specificando un percorso di file nel codice R, ma questa non è consigliata per la produzione.

Pertanto, è l'attività di amministratore del database o un altro amministratore nel server per garantire che tutti i pacchetti necessari siano installati nel [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] istanza. Se si dispone di privilegi amministrativi nel computer che ospita il [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]  istanza, è possibile fornire le informazioni su come installare pacchetti R amministratore e fornire l'accesso a un repository di pacchetti sicuro in cui è possibile ottenere i pacchetti richiesti dagli utenti. In questa sezione fornisce tali informazioni. 

> [!TIP]
> [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] fornisce nuove funzionalità per l'installazione e la gestione dei pacchetti R che forniscono l'amministratore del database e la maggiore libertà di data scientist e controllo sull'utilizzo del pacchetto e programma di installazione. Per ulteriori informazioni, vedere [gestione dei pacchetti R per SQL Server](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md). 

## <a name="installed-packages"></a>Pacchetti installati
Quando si installa  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)],  per impostazione predefinita il R **base** pacchetti sono installati, ad esempio `stats` e `utils`, insieme con il **RevoScaleR** pacchetto che supporta le connessioni a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 
> [!NOTE]  
>  Per un elenco dei pacchetti installati per impostazione predefinita, vedere [pacchetti installati con Microsoft R Open](https://mran.microsoft.com/rro/installed/).  

 Se è necessario un pacchetto aggiuntivo da CRAN o un altro repository, è necessario scaricare il pacchetto e installarlo nella workstation.  
  
 Se è necessario eseguire il nuovo pacchetto nel contesto del server, un amministratore necessario installarlo nel server nonché.   
   
## <a name="where-and-how-to-get-new-packages"></a>Dove e come ottenere nuovi pacchetti  
 Sono presenti più origini per i pacchetti R, le più note sono CRAN e Bioconductor. Il sito ufficiale per il linguaggio R ([https://www.r-project.org/](https://www.r-project.org/)) sono elencate molte di queste risorse. Molti pacchetti vengono pubblicati anche in GitHub, dove è possibile ottenere il codice sorgente. Tuttavia, si potrebbe avere accesso anche ai pacchetti R sviluppati da qualcuno nella propria azienda.  
  
 Indipendentemente dall'origine, i pacchetti devono essere offerti in un formato di file compresso da installare. Inoltre, utilizzare il pacchetto con [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], assicurarsi di ottenere il file compresso nel formato binario di Windows. (Alcuni pacchetti potrebbero non supporta questo formato). Per ulteriori informazioni sul contenuto del formato di file zip e come creare un pacchetto R, si consiglia di questa esercitazione, che è possibile scaricare in formato PDF dal sito del progetto R: [Freidrich Leisch: creazione di pacchetti R](http://cran.r-project.org/doc/contrib/Leisch-CreatingPackages.pdf). 
  
 In generale, pacchetti R possono essere installati facilmente dalla riga di comando senza scaricarli in anticipo, se il computer ha accesso a Internet.  In genere questo non avviene con i server che eseguono [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] .  Pertanto, per installare un pacchetto R in un computer che esegue **non** avere accesso a Internet, è necessario scaricare il pacchetto in un formato compresso anticipo e quindi copiare i file compressi in una cartella accessibile dal computer. 
 
 Gli argomenti seguenti vengono descritti due metodi per l'installazione di pacchetti non in linea: 

+ [Creare un Repository di pacchetti non in linea tramite miniCRAN](../../advanced-analytics/r-services/create-a-local-package-repository-using-minicran.md)

  Viene descritto come utilizzare il pacchetto R **miniCRAN** per creare un archivio non in linea. Ciò è probabilmente il metodo più efficiente se è necessario installare i pacchetti a più server e gestire il repository da un'unica posizione. 
+ [Installare i nuovi pacchetti R da Internet](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md)

  Include istruzioni per l'installazione di pacchetti non in linea copiando manualmente i file compressi.   

## <a name="permissions-required-for-installing-r-packages"></a>Autorizzazioni necessarie per l'installazione di pacchetti R  
  
Per installare un nuovo pacchetto R in un computer che esegue [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], è necessario disporre dei diritti amministrativi per il computer.   

Se non si dispone di questi diritti, contattare l'amministratore e fornire le informazioni sul pacchetto da installare.  
  

Se si sta installando un nuovo pacchetto R in un computer in uso come workstation R e il computer esegue **non** dispone di un'istanza di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] installato, è comunque necessario diritti amministrativi per il computer per installare il pacchetto. Dopo aver installato il pacchetto, è possibile eseguirlo in locale.  
 
> [!NOTE]
> In [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)], nuovi ruoli del database sono stati aggiunti per supportare l'ambito di autorizzazioni per l'installazione del pacchetto a un livello di istanza e database. Per ulteriori informazioni, vedere [gestione dei pacchetti R per SQL Server](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md).
 

### <a name="location-of-default-r-library-location-for-r-services"></a>Posizione del percorso di libreria predefinito R per i servizi di R

Se è stato installato  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] utilizzando l'istanza predefinita, la libreria di pacchetto R usata dall'istanza si trova sotto il [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] cartella dell'istanza. Esempio: 

+ Istanza predefinita _MSSQLSERVER_
  `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`
+ Istanza denominata _Istanzadenominatautente_
  `C:\Program Files\Microsoft SQL Server\MSSQL13.MyNamedInstance\R_SERVICES\library` 


È possibile eseguire l'istruzione seguente per verificare la libreria predefinita per l'istanza corrente di R. 
~~~~
EXECUTE sp_execute_external_script  @language = N'R'
, @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
~~~~

Per ulteriori informazioni, vedere [determinare quali pacchetti vengono installati nei Server SQL](../../advanced-analytics/r-services/determine-which-packages-are-installed-on-sql-server.md).

## <a name="managing-installed-packages"></a>La gestione dei pacchetti installati

[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] fornisce nuove funzionalità per l'installazione e la gestione dei pacchetti R che forniscono l'amministratore del database e la maggiore libertà di data scientist e controllo sull'utilizzo del pacchetto e programma di installazione. Per ulteriori informazioni, vedere [gestione dei pacchetti R per SQL Server](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md). 

Se si utilizza SQL Server 2106 R servizi, le nuove funzionalità di gestione di pacchetti non disponibili in questo momento. Nel frattempo, si dispone di queste opzioni per determinare quali pacchetti vengono installati le [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] computer, utilizzare una delle seguenti opzioni:

+ Consente di visualizzare la libreria predefinita, se si dispone delle autorizzazioni per la cartella.
+ Eseguire un comando dal comando R per elencare i pacchetti nel percorso di libreria R_SERVICES
+ Nell'istanza, utilizzare una stored procedure, ad esempio le operazioni seguenti:
   ```SQL
   EXECUTE sp_execute_external_script  @language=N'R'  
        ,@script = N'str(OutputDataSet);  
        packagematrix <- installed.packages();  
        NameOnly <- packagematrix[,1];  
        OutputDataSet <- as.data.frame(NameOnly);'  
        ,@input_data_1 = N'SELECT 1 as col'  
        WITH RESULT SETS ((PackageName nvarchar(250) ))   
   ```


 ## <a name="see-also"></a>Vedere anche  
 [La gestione e monitoraggio soluzioni R](../../advanced-analytics/r-services/managing-and-monitoring-r-solutions.md)  