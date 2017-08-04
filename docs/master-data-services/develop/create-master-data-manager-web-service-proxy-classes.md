---
title: Creare le classi Proxy servizio Web gestione dati Master | Documenti Microsoft
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 8bdab026-a0c0-41f3-9d36-f3919c23247f
caps.latest.revision: 8
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: a45cd15ced90aef95feb03f8fbaafd5aa70cb746
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="create-master-data-manager-web-service-proxy-classes"></a>Creare le classi proxy del servizio Web Gestione dati master
  Il servizio Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] consente di utilizzare a livello di codice le caratteristiche di [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] da qualsiasi computer che può accedere al sito Web di [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]. Prima di iniziare a scrivere il codice per accedere al servizio Web, è necessario generare le classi proxy. La classe proxy principale utilizzata per eseguire le operazioni del servizio Web è la classe <xref:Microsoft.MasterDataServices.ServiceClient>, che implementa l'interfaccia <xref:Microsoft.MasterDataServices.IService>.  
  
## <a name="enable-web-service-metadata-publishing"></a>Abilitare la pubblicazione dei metadati del servizio Web  
 Prima di generare le classi proxy, è necessario abilitare la pubblicazione dei metadati del servizio Web. A tale scopo, effettuare le operazioni seguenti:  
  
1.  Aprire il [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] file Web. config in un editor di testo. Il file Web.config si trova nella cartella WebApplication del percorso di installazione di [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].  
  
2.  Trovare il **mdsWsHttpBehavior** sezione nel  **\<serviceBehaviors >**. Per il  **\<serviceMetadata >** elemento, impostare **httpGetEnabled** a **true**.  
  
    > [!NOTE]  
    >  Se si desidera abilitare i servizi Web tramite Secure Sockets Layer (SSL), impostare **httpsGetEnabled** a **true** nel **mdsWsHttpBehavior** sezione del file Web. config. È inoltre necessario modificare **mdsWsHTTPBinding** in modo che sia configurato per SSL, nonché e impostare come commento la sezione non SSL.  
  
3.  Salvare le modifiche apportate al file.  
  
4.  Testare la pubblicazione dei metadati passando all'URL del servizio, ad esempio: `http://yourserver/MDS/service/service.svc`. Se la pubblicazione dei metadati è abilitata, viene visualizzata una pagina che inizia con   
    "È stato creato un servizio".  
  
## <a name="creating-proxy-classes-by-using-visual-studio"></a>Creazione di classi proxy tramite Visual Studio  
 Se si dispone di Visual Studio 2010 installato, il modo più semplice per generare classi proxy consiste nell'aggiungere un **riferimento al servizio** al progetto. L'indirizzo del riferimento al servizio è l'URL dell'applicazione Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] aggiunto a /service/service.svc, Esempio: `http://yourserver/MDS/service/service.svc`. Per ulteriori informazioni, vedere [procedura: aggiungere, aggiornare o rimuovere un riferimento al servizio](http://go.microsoft.com/fwlink/?LinkId=221167).  
  
## <a name="creating-proxy-classes-by-using-svcutilexe"></a>Creazione di classi proxy tramite Svcutil.exe  
 È necessario disporre [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] o [!INCLUDE[msCoName](../../includes/msconame-md.md)] per utilizzare Svcutil.exe nel computer è installato Windows SDK. Se si utilizza [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], per eseguire il comando sarà necessario utilizzare il prompt dei comandi di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Per ulteriori informazioni, vedere [strumento ServiceModel Metadata Utility Tool (Svcutil.exe)](http://go.microsoft.com/fwlink/?LinkId=165027) e [la generazione di un Client WCF dai metadati del servizio](http://go.microsoft.com/fwlink/?LinkId=164821).  
  
 Per creare un set di classi proxy in C# tramite Svcutil.exe, utilizzare un comando analogo al seguente:  
  
```  
svcutil.exe http://<server_name:port>/<virtual_path>/Service/Service.svc   
/out:<proxy_name>.cs /messageContract /tcv:Version35   
/noconfig /ct:System.Collections.ObjectModel.Collection`1   
/namespace:*,Microsoft.MasterDataServices  
```  
  
 Dove:  
  
-   *ServerName*:*porta* sono il nome del computer e il numero di computer che ospita porta [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].  
  
-   *virtual_path* è il percorso virtuale della [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] in Internet Information Services (IIS).  
  
-   *proxy_name* è il nome del file proxy generato.  
  
## <a name="see-also"></a>Vedere anche  
 [Operazioni del servizio Web per categoria &#40; Master Data Services &#41;](../../master-data-services/develop/categorized-web-service-operations-master-data-services.md)  
  
  
