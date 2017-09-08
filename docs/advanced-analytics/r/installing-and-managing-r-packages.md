---
title: Installazione e gestione dei pacchetti R | Microsoft Docs
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- R
ms.assetid: 4d426cf6-a658-4d9d-bfca-4cdfc8f1567f
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ae30bfc42e42b69158dbba5a38b0bccbe93523b4
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="installing-and-managing-r-packages"></a>Installazione e gestione dei pacchetti R
 Qualsiasi soluzione R eseguita in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] deve usare pacchetti installati nella libreria R predefinita. In genere, le soluzioni R fanno riferimento alle librerie utente specificando un percorso di file nel codice R, ma questo non è consigliato per l'ambiente di produzione.

L'amministratore del database o un altro amministratore del server deve quindi garantire che tutti i pacchetti necessari siano installati nell'istanza di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Se non si hanno privilegi amministrativi nel computer che ospita l'istanza di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], è possibile fornire all'amministratore informazioni su come installare i pacchetti R e fornire l'accesso a un repository di pacchetti sicuro in cui è possibile ottenere i pacchetti richiesti dagli utenti. Questa sezione fornisce tali informazioni. 

> [!TIP]
> [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] fornisce nuove funzionalità per l'installazione e la gestione dei pacchetti R che offrono agli amministratori di database e ai data scientist libertà e controllo maggiori sull'utilizzo e sulla configurazione dei pacchetti. Per altre informazioni, vedere [R Package management for SQL Server](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md) (Gestione dei pacchetti R per SQL Server). 

## <a name="installed-packages"></a>Pacchetti installati
Quando si installa [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], vengono installati per impostazione predefinita i pacchetti R di **base**, ad esempio `stats` e `utils`, insieme al pacchetto **RevoScaleR** che supporta le connessioni a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 
> [!NOTE]  
>  Per un elenco dei pacchetti installati per impostazione predefinita, vedere [Packages Installed with Microsoft R Open](https://mran.microsoft.com/rro/installed/) (Pacchetti installati con Microsoft R Open).  

 Se è necessario un pacchetto aggiuntivo da CRAN o un altro repository, sarà necessario scaricare il pacchetto e installarlo nella workstation.  
  
 Se si vuole eseguire il nuovo pacchetto nel contesto del server, un amministratore dovrà installarlo anche nel server.   
   
## <a name="where-and-how-to-get-new-packages"></a>Dove e come ottenere nuovi pacchetti  
 Sono presenti più origini per i pacchetti R, le più note sono CRAN e Bioconductor. Il sito ufficiale per il linguaggio R ([https://www.r-project.org/](https://www.r-project.org/)) elenca molte di queste risorse. Molti pacchetti vengono pubblicati anche in GitHub, dove è possibile ottenere il codice sorgente. Tuttavia, si potrebbe avere accesso anche ai pacchetti R sviluppati da qualcuno nella propria azienda.  
  
 Indipendentemente dall'origine, i pacchetti devono essere offerti in un formato di file compresso da installare. Per usare il pacchetto con [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], assicurarsi inoltre di ottenere il file compresso nel formato binario di Windows. Alcuni pacchetti potrebbero non supportare questo formato. Per altre informazioni sui contenuti del formato di file ZIP e su come creare un pacchetto R, è consigliabile seguire questa esercitazione, che è possibile scaricare in formato PDF dal sito del progetto R: [Freidrich Leisch: Creating R Packages](http://cran.r-project.org/doc/contrib/Leisch-CreatingPackages.pdf) (Freidrich Leisch: Creazione di pacchetti R). 
  
 In generale, i pacchetti R possono essere installati facilmente dalla riga di comando senza scaricarli in anticipo, se il computer ha accesso a Internet.  Solitamente ciò non avviene con i server che eseguono [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].  Per installare un pacchetto R in un computer che **non** ha accesso a Internet, è necessario scaricare il pacchetto nel formato compresso corretto e quindi copiare i file compressi in una cartella accessibile dal computer. 
 
 Gli argomenti seguenti descrivono due metodi per l'installazione di pacchetti offline: 

+ [Creare un repository di pacchetti offline usando miniCRAN](../../advanced-analytics/r-services/create-a-local-package-repository-using-minicran.md)

  Descrive come usare il pacchetto R **miniCRAN** per creare un repository offline. Si tratta probabilmente del metodo più efficiente se è necessario installare i pacchetti in più server e gestire il repository da un'unica posizione. 
+ [Installare nuovi pacchetti R da Internet](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md)

  Include istruzioni per l'installazione di pacchetti offline copiando manualmente i file compressi.   

## <a name="permissions-required-for-installing-r-packages"></a>Autorizzazioni necessarie per l'installazione di pacchetti R  
  
Per installare un nuovo pacchetto R in un computer che esegue [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], è necessario avere diritti amministrativi per il computer.   

Se non si dispone di questi diritti, contattare l'amministratore e fornire le informazioni sul pacchetto da installare.  
  

Se si installa un nuovo pacchetto R in un computer in uso come workstation R e il computer **non** ha un'istanza di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] installata, per installare il pacchetto sono comunque necessari i diritti amministrativi per il computer. Dopo aver installato il pacchetto, è possibile eseguirlo in locale.  
 
> [!NOTE]
> In [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] sono stati aggiunti nuovi ruoli del database per supportare la definizione dell'ambito delle autorizzazioni per l'installazione dei pacchetti a livello di istanza e di database. Per altre informazioni, vedere [R Package management for SQL Server](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md) (Gestione dei pacchetti R per SQL Server).
 

### <a name="location-of-default-r-library-location-for-r-services"></a>Posizione della libreria R predefinita per R Services

Se [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] è stato installato utilizzando l'istanza predefinita, la libreria di pacchetti R usata dall'istanza si trova nella cartella dell'istanza di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Esempio: 

+ Istanza predefinita _MSSQLSERVER_
  `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`
+ Istanza denominata _MyNamedInstance_
  `C:\Program Files\Microsoft SQL Server\MSSQL13.MyNamedInstance\R_SERVICES\library` 


È possibile eseguire l'istruzione seguente per verificare la libreria predefinita per l'istanza corrente di R. 
~~~~
EXECUTE sp_execute_external_script  @language = N'R'
, @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
~~~~

Per altre informazioni, vedere [Determinare i pacchetti che vengono installati in SQL Server](../../advanced-analytics/r-services/determine-which-packages-are-installed-on-sql-server.md).

## <a name="managing-installed-packages"></a>Gestione dei pacchetti installati

[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] fornisce nuove funzionalità per l'installazione e la gestione dei pacchetti R che offrono agli amministratori di database e ai data scientist libertà e controllo maggiori sull'utilizzo e sulla configurazione dei pacchetti. Per altre informazioni, vedere [R Package management for SQL Server](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md) (Gestione dei pacchetti R per SQL Server). 

Se si ha SQL Server 2106 R Services, le nuove funzionalità di gestione dei pacchetti non sono al momento disponibili. Nel frattempo, sono disponibili le opzioni seguenti per determinare quali pacchetti sono installati nel computer [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Usare una di queste opzioni:

+ Visualizzare la libreria predefinita, se si hanno le autorizzazioni per la cartella.
+ Eseguire un comando da R per elencare i pacchetti nel percorso della libreria R_SERVICES
+ Usare una stored procedure come la seguente nell'istanza:
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
 [Gestione e monitoraggio di soluzioni R](../../advanced-analytics/r-services/managing-and-monitoring-r-solutions.md)  

