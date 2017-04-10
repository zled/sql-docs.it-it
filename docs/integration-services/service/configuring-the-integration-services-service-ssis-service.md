---
title: "Configurazione del servizio Integration Services (servizio SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "02/28/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server (starting with 2016)"
helpviewer_keywords: 
  - "servizio Integration Services, configurazione"
  - "file di configurazione [Integration Services]"
  - "servizio [Integration Services], configurazione"
  - "file di configurazione predefiniti"
ms.assetid: 36d78393-a54c-44b0-8709-7f003f44c27f
caps.latest.revision: 74
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 70
---
# Configurazione del servizio Integration Services (servizio SSIS)
    
> [!IMPORTANT]  
>  In questo argomento viene illustrato il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , un servizio Windows per la gestione dei pacchetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] supporta il servizio per la compatibilità con le versioni precedenti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. A partire da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], è possibile gestire oggetti come i pacchetti del server Integration Services.  
  
 Il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] si basa su un file di configurazione per le relative impostazioni. Per impostazione predefinita, il file di configurazione è denominato MsDtsSrvr.ini.xml e si trova nella cartella %Programmi%\Microsoft SQL Server\110\DTS\Binn.  
  
 In genere, non è necessario apportare modifiche a tale file, né modificarne il percorso predefinito. Sarà tuttavia necessario modificare il file di configurazione se i pacchetti sono archiviati in un'istanza denominata o remota del [!INCLUDE[ssDE](../../includes/ssde-md.md)] o in più istanze del [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Se si sposta il file di configurazione in un percorso diverso da quello predefinito, sarà necessario modificare la chiave del Registro di sistema tramite cui viene specificato il percorso del file.  
  
## Contenuto del file di configurazione  
 Durante l'installazione di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] viene creato e installato il file di configurazione per il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], che contiene le impostazioni seguenti:  
  
-   All'arresto del servizio ai pacchetti viene inviato un comando di arresto.  
  
-   Le cartelle radice da visualizzare per [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] nella finestra Esplora oggetti di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] sono le cartelle MSDB e File System.  
  
-   I pacchetti nel file system gestiti dal servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] si trovano in %Programmi%\Microsoft SQL Server\110\DTS\Packages.  
  
 In questo file di configurazione è inoltre specificato quale database msdb contiene i pacchetti che verranno gestiti dal servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Per impostazione predefinita, il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] è configurato per gestire i pacchetti archiviati nel database msdb dell'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] installata in contemporanea con [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Se contemporaneamente non viene installata alcuna istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)], il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] è configurato per gestire i pacchetti contenuti nel database msdb dell'istanza predefinita locale del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
### Esempio di file di configurazione predefinito  
 Nell'esempio seguente è riportato un file di configurazione predefinito in cui sono specificate le impostazioni seguenti:  
  
-   Arresto dei pacchetti in esecuzione quando viene arrestato il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
-   Le cartelle radice per l'archiviazione dei pacchetti in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sono le cartelle MSDB e File system.  
  
-   Il servizio gestisce i pacchetti archiviati nel database msdb dell'istanza predefinita locale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   I pacchetti archiviati nel file system nella cartella Pacchetti sono gestiti dal servizio.  
  
 **Esempio di un file di configurazione predefinito**  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<DtsServiceConfiguration xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <StopExecutingPackagesOnShutdown>true</StopExecutingPackagesOnShutdown>  
  <TopLevelFolders>  
    <Folder xsi:type="SqlServerFolder">  
      <Name>MSDB</Name>  
      <ServerName>.</ServerName>  
    </Folder>  
    <Folder xsi:type="FileSystemFolder">  
      <Name>File System</Name>  
      <StorePath>..\Packages</StorePath>  
    </Folder>  
  </TopLevelFolders>    
</DtsServiceConfiguration>  
```  
  
## Modifica del file di configurazione  
 È possibile modificare il file di configurazione in modo da consentire l'esecuzione dei pacchetti anche quando il servizio viene arrestato, visualizzare cartelle radice aggiuntive in Esplora oggetti oppure specificare un'altra cartella o cartelle aggiuntive nel file system da gestire tramite il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. È possibile, ad esempio, creare cartelle radice aggiuntive di tipo **SqlServerFolder** per gestire i pacchetti nei database msdb di istanze aggiuntive del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
> [!NOTE]  
>  Alcuni caratteri non sono validi per i nomi delle cartelle. I caratteri validi per i nomi delle cartelle sono determinati dalla classe [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] **System.IO.Path** e dal campo **GetInvalidFilenameChars**. Il campo **GetInvalidFilenameChars** fornisce una matrice specifica della piattaforma che contiene i caratteri che non è possibile specificare negli argomenti delle stringhe dei percorsi passati ai membri della classe **Path**. Il set di caratteri non validi può variare in base al file system. Caratteri non validi sono in genere le virgolette ("), il carattere minore di (<) e la barra verticale (|).  
  
 Per gestire i pacchetti archiviati in un'istanza denominata o remota del [!INCLUDE[ssDE](../../includes/ssde-md.md)], è tuttavia necessario modificare il file di configurazione. Se non si aggiorna il file di configurazione, non sarà possibile usare **Esplora oggetti** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per visualizzare i pacchetti archiviati nel database msdb nell'istanza denominata o remota. Se si tenta di utilizzare **Esplora oggetti** per visualizzare questi pacchetti, verrà visualizzato il messaggio di errore seguente:  
  
 `Failed to retrieve data for this request. (Microsoft.SqlServer.SmoEnum)`  
  
 `The SQL Server specified in Integration Services service configuration is not present or is not available. This might occur when there is no default instance of SQL Server on the computer. For more information, see the topic "Configuring the Integration Services Service" in SQL Server 2008 Books Online.`  
  
 `Login Timeout Expired`  
  
 `An error has occurred while establishing a connection to the server. When connecting to SQL Server 2008, this failure may be caused by the fact that under the default settings SQL Server does not allow remote connections.`  
  
 `Named Pipes Provider: Could not open a connection to SQL Server [2]. (MsDtsSvr).`  
  
 Per modificare il file di configurazione per il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], usare un editor di testo.  
  
> [!IMPORTANT]  
>  Al termine della modifica del file di configurazione del servizio, è necessario riavviare il servizio in modo che utilizzi la configurazione aggiornata.  
  
### Esempio di file di configurazione modificato  
 Nell'esempio seguente viene illustrato un file di configurazione modificato per [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Questo file è per un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] denominata `InstanceName` su un server denominato `ServerName`.  
  
 **Esempio di un file di configurazione modificato per un'istanza denominata di SQL Server**  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<DtsServiceConfiguration xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <StopExecutingPackagesOnShutdown>true</StopExecutingPackagesOnShutdown>  
  <TopLevelFolders>  
    <Folder xsi:type="SqlServerFolder">  
      <Name>MSDB</Name>  
      <ServerName>ServerName\InstanceName</ServerName>  
    </Folder>  
    <Folder xsi:type="FileSystemFolder">  
      <Name>File System</Name>  
      <StorePath>..\Packages</StorePath>  
    </Folder>  
  </TopLevelFolders>    
</DtsServiceConfiguration>  
```  
  
## Modifica del percorso del file di configurazione  
 La chiave del Registro di sistema HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\SSIS\ServiceConfigFile specifica il percorso e il nome del file di configurazione usato dal servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Il valore predefinito della chiave del Registro di sistema è C:\Programmi\Microsoft SQL Server\110\DTS\Binn\ MsDtsSrvr.ini.xml. È possibile aggiornare il valore della chiave del Registro di sistema per utilizzare un nome e un percorso diversi per il file di configurazione.  
  
> [!CAUTION]  
>  La modifica non corretta del Registro di sistema può causare seri problemi che potrebbero richiedere la reinstallazione del sistema operativo. [!INCLUDE[msCoName](../../includes/msconame-md.md)] non può garantire che i problemi causati dalla modifica non corretta del Registro di sistema possano essere risolti. Prima di modificare il Registro di sistema, eseguire il backup dei dati importanti. Per informazioni sul backup, sul ripristino e sulla modifica del Registro di sistema, vedere l'articolo di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base relativo alla [descrizione del Registro di sistema di Microsoft Windows](http://support.microsoft.com/kb/256986).  
  
 Il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] carica il file di configurazione al momento dell'avvio. Qualsiasi modifica alla voce del Registro di sistema richiede il riavvio del servizio.  
  
  