---
title: Riferimento di configurazione (Master Data Services) Web | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- web configuration file [Master Data Services]
ms.assetid: b8cc9a35-97ab-4fe0-ab4b-c07f13d9793a
caps.latest.revision: 6
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1be0e90d7d2ba9b2751677015957ca249d91119e
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="web-configuration-reference-master-data-services"></a>Guida di riferimento alla configurazione Web (Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]utilizza un file Web. config per contenere le impostazioni di configurazione che consentono di Internet Information Services (IIS) di ospitare il [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] applicazione Web e il servizio Web. Questo file Web.config si trova nella cartella WebApplication nel percorso di installazione [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Per altre informazioni sul percorso e le autorizzazioni, vedere [Autorizzazioni per file e cartelle &#40;Master Data Services&#41;](../master-data-services/folder-and-file-permissions-master-data-services.md).  
  
## <a name="webconfig-elements"></a>Elementi di Web.Config  
 Il file Web. config contiene un oggetto personalizzato [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] elemento  **\<masterDataServices >**, oltre agli elementi di configurazione di Windows Communication Foundation (WCF), .NET Framework, ASP.NET e IIS standard. Nella tabella seguente vengono descritti gli elementi inclusi nel file Web.config.  
  
|Elemento di configurazione|Description|  
|---------------------------|-----------------|  
|**masterDataServices**|Elemento Custom. Connette il servizio Web [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] a un database di [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|  
|**connectionStrings**|Elemento ASP.NET. Per altre informazioni, vedere [Elemento connectionStrings (schema delle impostazioni ASP.NET)](http://go.microsoft.com/fwlink/?LinkId=178347) in MSDN Library.|  
|**system.web**|Elemento ASP.NET. Per altre informazioni, vedere [Elemento system.web (schema delle impostazioni ASP.NET)](http://go.microsoft.com/fwlink/?LinkId=178348) in MSDN Library.|  
|**startup**|Elemento .NET Framework. Per ulteriori informazioni, vedere [ \<avvio > elemento](http://go.microsoft.com/fwlink/?LinkId=178349) in MSDN Library.|  
|**runtime**|Elemento .NET Framework. Per ulteriori informazioni, vedere [ \<runtime > elemento](http://go.microsoft.com/fwlink/?LinkId=178350) in MSDN Library.|  
|**system.codedom**|Elemento .NET Framework. Per ulteriori informazioni, vedere [ \<System. CodeDom > elemento](http://go.microsoft.com/fwlink/?LinkId=178351) in MSDN Library.|  
|**system.web.extensions**|Elemento ASP.NET. Per altre informazioni, vedere [Elemento system.web.extensions (schema delle impostazioni ASP.NET)](http://go.microsoft.com/fwlink/?LinkId=178352) in MSDN Library.|  
|**system.webServer**|Gruppo di sezioni che contiene gli elementi IIS. Per altre informazioni, vedere [system.webServer Section Group \[IIS 7 Settings Schema\]](http://go.microsoft.com/fwlink/?LinkId=178353) (Gruppo di sezioni system.webServer (schema delle impostazioni IIS 7)) in MSDN Library.|  
|**system.serviceModel**|Elemento WCF. Per ulteriori informazioni, vedere [ \<System. ServiceModel >](http://go.microsoft.com/fwlink/?LinkId=178354) in MSDN Library.|  
|**system.diagnostics**|Elemento .NET Framework. Per ulteriori informazioni, vedere [ \<System. Diagnostics > elemento](http://go.microsoft.com/fwlink/?LinkId=178355) in MSDN Library.|  
|**appSettings**|Elemento ASP.NET. Per altre informazioni, vedere [Elemento appSettings (schema delle impostazioni generali)](http://go.microsoft.com/fwlink/?LinkId=178356) in MSDN Library.|  
  
## <a name="masterdataservices-element"></a>Elemento masterdataservices  
 Il  **\<masterDataServices >** elemento è un elemento personalizzato che viene utilizzato per connettere un [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] servizio Web un [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.  
  
### <a name="syntax"></a>Sintassi  
  
```  
<masterDataServices>  
   <instance virtualPath="path" siteName="name" connectionName="name" serviceName="name" />  
</masterDataServices>  
```  
  
### <a name="elements-and-attributes"></a>Elementi e attributi  
  
|Elemento|Description|  
|----------|-----------------|  
|**istanza**|Elemento figlio. Contiene gli attributi che specificano le informazioni per la stringa di connessione al database e al servizio Web.|  
|**virtualPath**|Attributo. Specifica il percorso virtuale del servizio e dell'applicazione Web di [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Corrisponde alla **percorso** attributo del  **\<applicazione >** elemento sotto il  **\<sito >** elemento nel file ApplicationHost. config di IIS.|  
|**siteName**|Attributo. Specifica il nome del sito che ospita il servizio e l'applicazione Web di [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Corrisponde alla **nome** attributo del  **\<sito >** elemento sotto  **\<siti >** nel file ApplicationHost. config di IIS.|  
|**connectionName**|Attributo. Specifica il nome della connessione da utilizzare. Corrisponde alla **nome** attributo del  **\<aggiungere >** elemento sotto il  **\<connectionStrings >** elemento nel file Web. config.|  
|**serviceName**|Attributo. Specifica il nome del servizio Web. Corrisponde alla **nome** attributo del  **\<servizio >** elemento sotto il  **\<services >** elemento nel file Web. config.|  
  
### <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un servizio denominato MDS1 nel sito di Contoso e nel percorso /MDS mediante una stringa di connessione specificata da MDSDB.  
  
```  
<masterDataServices>  
   <instance virtualPath="/MDS" siteName="Contoso" connectionName="MDSDB" serviceName="MDS1" />  
</masterDataServices>  
```  
  
  
