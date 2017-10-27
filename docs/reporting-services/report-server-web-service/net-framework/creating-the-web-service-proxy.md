---
title: Creazione di Proxy del servizio Web | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Report Server Web service, proxies
- proxies [Reporting Services]
- XML Web service [Reporting Services], proxies
- Web service [Reporting Services], proxies
- Web references [Reporting Services]
ms.assetid: b1217843-8d3d-49f3-a0d2-d35b0db5b2df
caps.latest.revision: 44
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 727d9ccd8cd1e40d89cfe74291edae92988b407c
ms.openlocfilehash: 1c39d81ec9a1d2cd24f01b9dccfed13e8560a770
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="creating-the-web-service-proxy"></a>Creazione del proxy del servizio Web
  Un client e un servizio Web possono comunicare utilizzando messaggi SOAP, che incapsulano i parametri di input e di output in formato XML. Una classe proxy esegue il mapping dei parametri agli elementi XML, quindi invia i messaggi SOAP in una rete. In questo modo, la classe proxy elimina l'esigenza di comunicare con il servizio Web a livello SOAP e consente di richiamare i metodi del servizio Web in qualsiasi ambiente di sviluppo che supporti i proxy del servizio Web e SOAP.  
  
 Esistono due modi per aggiungere una classe proxy al progetto di sviluppo utilizzando la [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]: con lo strumento WSDL nel [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]e aggiungendo un riferimento Web in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]. Nelle sezioni seguenti questo argomento viene illustrato in modo più dettagliato.  
  
## <a name="adding-the-proxy-using-the-wsdl-tool"></a>Aggiunta del proxy utilizzando lo strumento WSDL  
 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK include lo strumento WSDL (Web Services Description Language) (Wsdl.exe) che consente di generare un proxy del servizio Web per l'utilizzo nell'ambiente di sviluppo di [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Il modo più comune per creare un proxy client in linguaggi che supportano servizi Web (attualmente c# e [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) consiste nell'utilizzare lo strumento WSDL.  
  
 **Per aggiungere una classe proxy al progetto utilizzando Wsdl.exe**  
  
1.  Dal prompt dei comandi utilizzare Wsdl.exe per creare una classe proxy, specificando almeno l'URL del servizio Web ReportServer.  
  
     Nell'istruzione del prompt dei comandi seguente viene ad esempio specificato un URL per l'endpoint di gestione del servizio Web ReportServer:  
  
    ```  
    wsdl /language:CS /n:"Microsoft.SqlServer.ReportingServices2010" http://<Server Name>/reportserver/reportservice2010.asmx?wsdl  
    ```  
  
     Lo strumento WSDL accetta diversi argomenti del prompt dei comandi per la generazione di un proxy. Nell'esempio precedente sono specificati il linguaggio C# e uno spazio dei nomi suggerito da utilizzare nel proxy (per impedire il conflitto tra i nomi in caso di utilizzo di più di un endpoint servizio Web) e viene generato un file C# denominato ReportingService2010.cs. Se nell'esempio fosse stato specificato [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)], sarebbe stato generato un file proxy denominato ReportingService2010.vb. Questo file viene creato nella directory dalla quale si esegue il comando.  
  
2.  Compilare la classe proxy in un file di assembly (con estensione dll) e farvi riferimento nel progetto oppure aggiungere la classe come elemento del progetto.  
  
    > [!NOTE]  
    >  Quando si aggiunge manualmente una classe proxy al progetto, è necessario aggiungere un riferimento a System.Web.Services.dll. Se si aggiunge il proxy utilizzando un riferimento Web in Visual Studio .NET, il riferimento viene creato automaticamente. Per ulteriori informazioni, vedere "Aggiunta del proxy utilizzando un riferimento Web in Visual Studio" più avanti in questo argomento.  
  
     Dopo avere aggiunto la classe proxy come elemento nel progetto, il file associato viene visualizzato in Esplora soluzioni.  
  
3.  Per chiamare il servizio a livello di programmazione, creare un'istanza della classe proxy.  
  
     Nell'esempio di codice seguente viene illustrata la sintassi per la creazione di un'istanza della classe proxy <xref:ReportService2010.ReportingService2010> in un progetto.  
  
```vb  
Dim service As New ReportingService2010()  
```  
  
```csharp  
ReportingService2010 service = new ReportingService2010();  
  
```  
  
 Per ulteriori informazioni sullo strumento Wsdl.exe, inclusa la sintassi completa, vedere l'argomento relativo allo strumento WSDL nella documentazione di [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK. Per una spiegazione completa relativa ai proxy del servizio Web, vedere l'argomento relativo alla creazione di un proxy del servizio Web XML nella documentazione di [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK.  
  
## <a name="adding-the-proxy-using-a-web-reference-in-visual-studio"></a>Aggiunta del proxy utilizzando un riferimento Web in Visual Studio  
 Un riferimento Web consente l'utilizzo di uno o più servizi Web in un progetto. [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] consente agli utenti di aggiungere ai progetti riferimenti al servizio Web tramite alcuni semplici passaggi.  
  
 **Per aggiungere un riferimento Web a un progetto**  
  
1.  In **Esplora**, selezionare il progetto che verrà utilizzato il servizio Web.  
  
2.  Nel **progetto** menu, fare clic su **Aggiungi riferimento Web**.  
  
     Il **Aggiungi riferimento Web** verrà visualizzata la finestra di dialogo.  
  
3.  Nel **URL** immettere il percorso completo al servizio Web ReportServer.  
  
     Un URL semplificato per l'endpoint di esecuzione del report del servizio Web ReportServer potrebbe essere simile al seguente:  
  
    ```  
    http://<Server Name>/reportserver/reportexecution2005.asmx  
    ```  
  
     L'URL contiene il dominio nel quale viene distribuito il servizio Web ReportServer, il nome della cartella contenente il servizio e il nome del file di individuazione per il servizio. Per una descrizione completa dei diversi elementi di URL, vedere [l'accesso all'API SOAP](../../../reporting-services/report-server-web-service/accessing-the-soap-api.md).  
  
     Una descrizione delle proprietà e dei metodi forniti dal servizio Web viene visualizzata nel riquadro del visualizzatore a sinistra.  
  
    > [!NOTE]  
    >  Per ulteriori informazioni sugli elementi associati al servizio Web ReportServer, vedere [metodi del servizio Web ReportServer](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md).  
  
4.  Verificare che il progetto possa utilizzare il servizio Web ReportServer, nonché di disporre delle autorizzazioni appropriate per l'accesso al server di report.  
  
5.  Nel **nome riferimento Web** immettere un nome che verrà utilizzato nel codice per accedere a livello di programmazione il servizio Web ReportServer.  
  
6.  Selezionare il **Aggiungi riferimento** pulsante per creare un riferimento nell'applicazione per il servizio Web.  
  
     Il nuovo riferimento verrà visualizzato **Esplora** sotto il nodo Riferimenti Web per il progetto attivo, il nome specificato nella **nome riferimento Web** campo.  
  
7.  In **Esplora**, espandere la cartella riferimenti Web per osservare lo spazio dei nomi per le classi di riferimento Web disponibili per gli elementi del progetto.  
  
     Dopo aver aggiunto un riferimento Web al progetto, i file associati vengono visualizzati in una cartella all'interno della cartella riferimenti Web di **Esplora**.  
  
 Dopo avere aggiunto il riferimento Web, utilizzare la sintassi seguente per creare un'istanza della classe proxy:  
  
```vb  
Dim rs As New myNamespace.myReferenceName.ReportExecutionService()  
rs.Url = "http://<Server Name>/reportserver/reportexecution2005.asmx?wsdl"  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
```  
  
```csharp  
myNamespace.myReferenceName.ReportExecutionService rs = new myNamespace.myReferenceName.ReportExecutionService();  
rs.Url = "http://<Server Name>/reportserver/reportexecution2005.asmx?wsdl"  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
  
```  
  
 È inoltre possibile aggiungere un **utilizzando** (**importazione** in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) direttiva per il riferimento al servizio Web ReportServer. Quando si utilizza questa direttiva, non è necessario specificare il nome completo dei tipi nello spazio dei nomi. A tale scopo, aggiungere al file il codice seguente:  
  
```vb  
Import myNamespace.myReferenceName  
```  
  
```csharp  
using myNamespace.myReferenceName;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Servizio Web ReportServer](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Creazione di applicazioni mediante il servizio Web e .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Riferimento tecnico &#40; SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  

