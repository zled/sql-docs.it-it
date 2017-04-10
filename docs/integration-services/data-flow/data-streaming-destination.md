---
title: "Destinazione flusso di dati | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 640e6a19-49ae-4ee8-ac07-008370158f0e
caps.latest.revision: 10
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 10
---
# Destinazione flusso di dati
  **Destinazione flusso di dati** è un componente di destinazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (SSIS) che consente al **provider OLE DB per SSIS** di usare l'output di un pacchetto SSIS come set di risultati tabulare. È possibile creare un server collegato che usa il provider OLE DB per SSIS e quindi eseguire una query SQL su tale server per visualizzare i dati restituiti dal pacchetto SSIS.  
  
 La query dell'esempio seguente restituisce l'output dal pacchetto Package.dtsx nel progetto SSISPackagePublishing nella cartella di Power BI del catalogo SSIS. La query usa il server collegato denominato [Server collegato predefinito per Integration Services] che a sua volta usa il nuovo provider OLE DB per SSIS. La query include il nome della cartella, il nome del progetto e il nome del pacchetto nel catalogo SSIS. Il provider OLE DB per SSIS esegue il pacchetto specificato nella query e restituisce il set di risultati tabulare.  
  
```  
SELECT * FROM OPENQUERY([Default Linked Server for Integration Services], N'Folder=Power BI;Project=SSISPackagePublishing;Package=Package.dtsx')  
  
```  
  
## Componenti di pubblicazione del feed di dati  
 I componenti di pubblicazione del feed di dati includono il provider OLE DB per SSIS, Destinazione flusso di dati e Pubblicazione guidata di pacchetti SSIS. La procedura guidata consente di pubblicare un pacchetto SSIS come vista SQL in un'istanza del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . La procedura agevola la creazione di un server collegato che usa il provider OLE DB per SSIS e di una vista SQL che rappresenta la query sul server collegato. La vista consente di visualizzare i risultati della query dal pacchetto SSIS come set di dati tabulari.  
  
 Per verificare l'installazione del provider SSISOLEDB, in SQL Server Management Studio espandere **Oggetti server**, **Server collegati**, **Provider**e quindi accertarsi che il provider **SSISOLEDB** sia visibile. Fare doppio clic su **SSISOLEDB**, abilitare l'opzione **Consenti in-process** se non è abilitata e quindi fare clic su **OK**.  
  
## Pubblicare un pacchetto SSIS come vista SQL  
 La procedura seguente descrive i passaggi per la pubblicazione di un pacchetto SSIS come vista SQL.  
  
1.  Creare un pacchetto SSIS con il componente **Destinazione flusso di dati** e distribuire il pacchetto nel catalogo SSIS.  
  
2.  Avviare la **Pubblicazione guidata di pacchetti SSIS** eseguendo ISDataFeedPublishingWizard.exe da C:\Programmi\Microsoft SQL Server\130\DTS\Binn o Pubblicazione guidata feed di dati dal menu Start.  
  
     La procedura guidata crea un server collegato usando il provider OLE DB per SSIS (SSISOLEDB) e quindi crea una vista SQL costituita da una query su tale server. La query include il nome della cartella, il nome del progetto e il nome del pacchetto nel catalogo SSIS.  
  
3.  Eseguire la vista SQL in SQL Server Management Studio ed esaminare i risultati dal pacchetto SSIS. La vista invia la query al provider OLE DB per SSIS usando il server collegato che è stato creato. Il provider OLE DB per SSIS esegue il pacchetto specificato nella query e restituisce il set di risultati tabulare alla query.  
  
> [!IMPORTANT]  
>  Per informazioni dettagliate, vedere [Procedura dettagliata: Pubblicare un pacchetto SSIS come vista SQL](../../integration-services/data-flow/walkthrough-publish-an-ssis-package-as-a-sql-view.md).  
  
## Esporre i dati di output da un pacchetto SSIS come feed OData usando l'Interfaccia di amministrazione di Power BI  
 Con l'Interfaccia di amministrazione di Power BI, gli amministratori IT possono esporre i dati provenienti da origini dati locali come feed OData. Per impostazione predefinita, l'interfaccia di amministrazione consente di registrare solo origini dati SQL Server. Tuttavia, è possibile registrare pacchetti SSIS come origini dati con il portale usando il componente **Destinazione flusso di dati** e il **Provider Microsoft OLE DB per SQL Server Integration Services (SSISOLEDB)** ed esporre i dati del risultato dal pacchetto SSIS come feed OData.  
  
 L'interfaccia di amministrazione consente di pubblicare viste in un database SQL Server. Di conseguenza, si può usare la Pubblicazione guidata del pacchetto SSIS per pubblicare un pacchetto SSIS come vista SQL. A questo punto, selezionare la vista da includere nel feed OData nell'Interfaccia di amministrazione di Power BI. Un amministratore dei dati può usare il feed dal pacchetto SSIS con il componente aggiuntivo Power Query per Excel.  
  
 Per una procedura dettagliata, vedere la pagina relativa alla [pubblicazione di pacchetti SSIS come origini di feed OData](http://go.microsoft.com/fwlink/?LinkID=317367).  
  
## Contenuto della sezione  
  
-   [Procedura dettagliata: Pubblicare un pacchetto SSIS come vista SQL](../../integration-services/data-flow/walkthrough-publish-an-ssis-package-as-a-sql-view.md)  
  
-   [Configurare Destinazione flusso di dati](../../integration-services/data-flow/configure-data-streaming-destination.md)  
  
## Vedere anche  
 [pubblicazione di pacchetti SSIS come origini di feed OData](http://go.microsoft.com/fwlink/?LinkID=317367)  
  
  