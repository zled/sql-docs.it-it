---
title: Accedere agli elementi del server di report usando l'accesso con URL | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- referencing URL items for report server access
- URL access [Reporting Services], report servers
ms.assetid: a58b4ca6-129d-45e9-95c7-e9169fe5bba4
caps.latest.revision: "40"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 010d16c1114ea7b8d7a1c7c0274aba2ecd44b8d4
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="access-report-server-items-using-url-access"></a>Accesso agli elementi del server di report utilizzando l'accesso tramite URL
  Questo argomento descrive come accedere a tipi diversi di elementi del catalogo in un database del server di report o in un sito di SharePoint usando *rs:Command*=*Value*. In realtà non è necessario aggiungere questa stringa del parametro. Se la si omette, il tipo di elemento viene valutato dal server di report e il valore del parametro appropriato viene selezionato automaticamente. Tuttavia, l'uso della stringa *rs:Command*=*Valore* nell'URL migliora le prestazioni del server di report.  
  
 Si noti la sintassi del proxy `_vti_bin` negli esempi riportati di seguito. Per altre informazioni su come usare la sintassi del proxy, vedere [Riferimento ai parametri di accesso con URL](../reporting-services/url-access-parameter-reference.md).  
  
## <a name="access-a-report"></a>Accedere a report  
 Per visualizzare un report nel browser, usare il parametro *rs:Command*=*Render* . Esempio:  
  
 - **Nativo** `http://myrshost/reportserver?/Sales/YearlySalesByCategory&rs:Command=Render`  
 - **SharePoint** `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/YearlySalesByCategory&rs:Command=Render`  
  
> [!TIP]  
>  È importante che nell'URL sia inclusa la sintassi proxy `_vti_bin` per indirizzare la richiesta tramite SharePoint e il proxy HTTP di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Tramite il proxy viene aggiunto del contesto alla richiesta HTTP. Questo contesto è necessario per garantire l'esecuzione corretta del report per i server di report in modalità SharePoint.  
  
## <a name="access-a-resource"></a>Accedere a una risorsa  
 Per accedere a una risorsa, usare il parametro *rs:Command*=*GetResourceContents* . Se la risorsa è compatibile con il browser, come accade per un'immagine, viene aperta nel browser. In caso contrario, verrà chiesto di aprire oppure salvare il file o la risorsa su disco.  
  
 **Nativo** `http://myrshost/reportserver?/Sales/StorePicture&rs:Command=GetResourceContents`  
  
 **SharePoint** `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/StorePicture.jpg&rs:Command=GetResourceContents`  
  
## <a name="access-a-data-source"></a>Accedere a un'origine dati  
 Per accedere a un'origine dati, usare il parametro *rs:Command*=*GetDataSourceContents* . Se il browser supporta XML, la definizione dell'origine dati viene visualizzata se l'utente è autenticato con l'autorizzazione per la **lettura del contenuto** per l'origine dati. Esempio:  
  
 **Nativo** `http://myrshost/reportserver?/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`  
  
 **SharePoint** `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`  
  
 La struttura XML potrebbe essere simile a quella illustrata nell'esempio seguente:  
  
```  
<DataSourceDefinition>  
   <Extension>SQL</Extension>  
   <ConnectString>Provider=SQLOLEDB.1;Integrated Security=SSPI;Persist Security Info=False;Initial Catalog=AdventureWorks2012;Data Source=MYSERVER1;</ConnectString>  
   <CredentialRetrieval>Integrated</CredentialRetrieval>  
   <WindowsCredentials>False</WindowsCredentials>  
   <ImpersonateUser>False</ImpersonateUser>  
   <Prompt />  
   <Enabled>True</Enabled>  
</DataSourceDefinition>  
```  
  
 La stringa di connessione viene restituita in base all'impostazione **SecureConnectionLevel** nel server di report. Per altre informazioni sull'impostazione **SecureConnectionLevel** , vedere [Uso di metodi del servizio Web protetti](../reporting-services/report-server-web-service/net-framework/using-secure-web-service-methods.md).  
  
## <a name="access-the-contents-of-a-folder"></a>Accedere ai contenuti di una cartella  
 Per accedere ai contenuti di una cartella, usare il parametro *rs:Command*=*GetChildren* . Viene restituita una pagina generica di navigazione della cartella che contiene collegamenti alle sottocartelle, alle origini dati, alle risorse e ai report inclusi nella cartella richiesta. Esempio:  
  
 **Nativo** `http://myrshost/reportserver?/Sales&rs:Command=GetChildren`  
  
 **SharePoint** `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales&rs:Command=GetChildren`  
  
 L'interfaccia utente visualizzata è simile alla modalità di esplorazione delle directory utilizzata da [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Information Server (IIS). Sotto l'elenco della cartella viene visualizzato anche il numero di versione, incluso il numero di build, del server di report.  
  
## <a name="see-also"></a>Vedere anche  
 [Accesso con URL &#40;SSRS&#41;](../reporting-services/url-access-ssrs.md)   
 [Riferimento ai parametri di accesso con URL](../reporting-services/url-access-parameter-reference.md) 
