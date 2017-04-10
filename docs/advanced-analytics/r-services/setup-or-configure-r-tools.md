---
title: "Programma di installazione o configurare gli strumenti di R | Microsoft Docs"
ms.custom: ""
ms.date: "01/20/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c04ae30-d391-4369-9742-d2b275e14c0d
caps.latest.revision: 9
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 8
---
# Programma di installazione o configurare gli strumenti di R
  Microsoft R Server fornisce tutte le librerie base R, pacchetti R scala e standard R gli strumenti necessari per sviluppare e testare il codice R. Tuttavia, se si desidera utilizzare un ambiente di sviluppo R dedicato, esistono diversi disponibili, inclusi molti strumenti gratuiti.  
  
## <a name="basic-r-tools"></a>Strumenti di base R  
 Strumenti aggiuntivi non è necessario in un'installazione di Microsoft Server R, perché tutti R standard strumenti inclusi in un *installazione di base* r vengono installati per impostazione predefinita.

-   **RTerm**: uno strumento da riga di comando per l'esecuzione di script R 
  
-   **RGui.exe**: un semplice editor interattivo per R. Gli argomenti della riga di comando sono le stesse per RGui.exe e RTerm. 
  
-   **RScript**: uno strumento da riga di comando per l'esecuzione R script in modalità batch.  

Per impostazione predefinita, questi strumenti vengono installati nelle cartelle seguenti:
- SQL Server 2016: `C:\Program Files\Microsoft SQL Server\130\R_SERVER\bin\x64`  
- SQL Server vNext: `C:\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64`  

> [!TIP]  
>  Per ulteriore assistenza Documentazione per gli strumenti di R è disponibile nella cartella di installazione: `C:\Program Files\Microsoft SQL Server\R_SERVER\doc` e `C:\Program Files\Microsoft SQL Server\R_SERVER\doc\manual`.  
>   
>  O, semplicemente aprire **RGui**, fare clic su **Guida**, e selezionare una delle opzioni.  

## <a name="microsoft-r-client"></a>Microsoft R Client

Microsoft R è un download gratuito che consente di sviluppare soluzioni R che possono essere facilmente eseguite in Microsoft R Server o nei servizi di SQL Server R.

In genere si installa un ambiente di sviluppo R diverso, ad esempio R Tools per Visual Studio o RStudio e quindi specificare che il Client di R Microsoft utilizzato come l'eseguibile di R. Ciò consente l'accesso completo al pacchetto RevoScaleR e altre funzionalità di Microsoft Server R.

È inoltre possibile utilizzare strumenti noti quali RGui e RTerm di eseguire script o scrivere ed eseguire codice R ad hoc.

[Installare il Client Microsoft R](https://msdn.microsoft.com/microsoft-r/r-client-install)
  
##  <a name="a-namebkmkrtoolsa-r-tools-for-visual-studio"></a> R Tools per Visual Studio  

 Per motivi di praticità nell'uso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, si consiglia di utilizzare [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] come ambiente di sviluppo. [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] è un componente aggiuntivo gratuito per Visual Studio che funziona in tutte le edizioni di Visual Studio. Visual Studio fornisce inoltre supporto per l'integrazione di Python e F #.  

Per ulteriori informazioni, vedere [VisualStudio.com](https://www.visualstudio.com/vs/rtvs/).

 In questa sezione viene descritto come installare [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] utilizzando il libero Community Edition di Visual Studio.  
  
#### <a name="install-visual-studio"></a>Installare Visual Studio  
  
1.  La Community edition gratuita di Visual Studio è disponibile per il download da questa pagina: [Visual Studio Community](http://visualstudio.com/products/visual-studio-community-vs.aspx)  
  
2.  Al termine del download, fare clic su **eseguire** e selezionare i componenti da installare.  
  
     Se si esegue un'installazione personalizzata, si noti che sono necessari i componenti di Microsoft Web Developer.  
  
3.  Scegliere il **Generale** impostazione per il momento. Quando si installa [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)], sarà necessario toption per un layout personalizzato per lo sviluppo di R.  

#### <a name="add-the-r-tools"></a>Aggiungere gli strumenti di R

Dopo l'installazione di Visual Studio, sono disponibili per R, Python e molte altre lingue tramite le estensioni di **Opzioni** menu.

4. Fare clic su strumenti dalla barra dei menu e quindi selezionare **estensioni e aggiornamenti**.

5. Verso la fine dell'installazione, strumenti di R consentirà di rilevare le versioni del runtime di R sono disponibili nel computer e chiedere se si desidera modificare l'ambiente di sviluppo per utilizzare il runtime R per Microsoft R Server o il runtime R per Microsoft R Client.

Se il programma di installazione non viene rilevato il runtime R Server si desidera utilizzare, è possibile modificarlo manualmente in qualsiasi momento utilizzando il **Opzioni** menu. Per ulteriori informazioni, vedere [configurare l'IDE](https://msdn.microsoft.com/microsoft-r/r-client-get-started#step-2-configure-your-ide).

## <a name="rstudio"></a>RStudio

Se si preferisce utilizzare RStudio, eseguire questi passaggi aggiuntivi per utilizzare le librerie RevoScaleR:
- Installare Microsoft R Server o Client di Microsoft R per ottenere i pacchetti necessari e le librerie.
- Aggiornare il percorso di R per utilizzare il runtime R appropriato.

Per ulteriori informazioni, vedere [configurare l'IDE](https://msdn.microsoft.com/microsoft-r/r-client-get-started#step-2-configure-your-ide).


## <a name="see-also"></a>Vedere anche  
 [Creare un Server di R autonomo](../../advanced-analytics/r-services/create-a-standalone-r-server.md)   
 [Introduzione a Server Microsoft R &#40; Autonomo &#41;](../../advanced-analytics/r-services/getting-started-with-microsoft-r-server-standalone.md)  
  
  