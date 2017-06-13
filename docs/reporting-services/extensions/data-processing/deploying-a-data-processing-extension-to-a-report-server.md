---
title: 'Procedura: distribuire un&quot;estensione per l&quot;elaborazione dati in un Server di Report | Documenti Microsoft'
ms.custom: 
ms.date: 03/06/2017
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
- data processing extensions [Reporting Services], deploying
- assemblies [Reporting Services], data processing extension deployments
ms.assetid: e00dface-70f8-434b-9763-8ebee18737d2
caps.latest.revision: 45
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: ed23ebf2bd6cbecbd028488c5188368e1a076d46
ms.contentlocale: it-it
ms.lasthandoff: 06/13/2017

---
# <a name="deploying-a-data-processing-extension-to-a-report-server"></a>Distribuzione di un'estensione di elaborazione dei dati in un Server di Report
  I server di report utilizzano le estensioni per l'elaborazione dati per il recupero e l'elaborazione di dati nei report visualizzabili. È necessario distribuire l'assembly dell'estensione per l'elaborazione dati in un server di report come assembly privato. È inoltre necessario creare una voce nel file di configurazione del server di report, ovvero RSReportServer.config.  
  
## <a name="procedures"></a>Procedure  
  
#### <a name="to-deploy-a-data-processing-extension-assembly"></a>Per distribuire un assembly dell'estensione per l'elaborazione dati  
  
1.  Copiare l'assembly dal percorso di gestione temporanea nella directory bin del server di report in cui si desidera utilizzare l'estensione per l'elaborazione dati. Il percorso predefinito della directory bin del server di report è %ProgramFiles%\Microsoft SQL Server\MSRS10_50. \< *Nome istanza*> Services\ReportServer\bin..  
  
    > [!NOTE]  
    >  Con questo passaggio viene evitato l'aggiornamento a un'istanza di SQL Server più recente. Per ulteriori informazioni, vedere [Upgrade and Migrate Reporting Services](../../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).  
  
2.  Dopo aver copiato il file di assembly, aprire il file RSReportServer.config che si trova nella directory ReportServer. È necessario immettere una voce nel file di configurazione per il file di assembly dell'estensione per l'elaborazione dati. È possibile aprire il file di configurazione con Visual Studio o di un semplice editor di testo, ad esempio Blocco note.  
  
3.  Individuare l'elemento **Data** nel file RSReportServer.config. È necessario immettere una voce per l'estensione per l'elaborazione dati appena creata nel percorso seguente:  
  
    ```  
    <Extensions>  
       <Data>  
          <Your extension configuration information goes here>  
       </Data>  
    </Extensions>  
    ```  
  
4.  Aggiungere una voce per l'estensione per l'elaborazione dati. La voce deve includere un **estensione** elemento con i valori per **nome** e **tipo** e potrebbe essere simile al seguente:  
  
    ```  
    <Extension Name="ExtensionName" Type="CompanyName.ExtensionName.MyConnectionClass, MyExtensionAssembly" />  
    ```  
  
     Il valore per **nome** è il nome univoco dell'estensione per l'elaborazione dati. Il valore per **tipo** è un elenco delimitato da virgole che include una voce per lo spazio dei nomi completo della classe che implementa il <xref:Microsoft.ReportingServices.Interfaces.IExtension> e <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> interfacce, seguite dal nome dell'assembly (senza l'estensione del file con estensione dll). Per impostazione predefinita, le estensioni per l'elaborazione dati sono visibili. Per nascondere un'estensione dalle interfacce utente, come Gestione report, aggiungere un attributo **Visible** all'elemento **Extension** e impostarlo su **false**.  
  
5.  Aggiungere un gruppo di codice per l'assembly personalizzato che conceda **FullTrust** dell'autorizzazione per l'estensione. Questo scopo, aggiungere il gruppo di codice per il file rssrvpolicy. config si trova per impostazione predefinita in %ProgramFiles%\Microsoft SQL Server\\< MSRS10_50.\< *Nome istanza*> Services\ReportServer.. Il gruppo di codice può essere simile a quanto riportato di seguito:  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my data processing extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.<Instance Name>\Reporting Services\ReportServer\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 L'appartenenza URL è solo una delle diverse condizioni di appartenenza selezionabili per l'estensione per l'elaborazione dati. Per ulteriori informazioni sulla sicurezza di accesso di codice in [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], vedere [sviluppo protetto &#40; Reporting Services &#41; ](../../../reporting-services/extensions/secure-development/secure-development-reporting-services.md).  
  
## <a name="verifying-the-deployment"></a>Verifica della distribuzione  
 È possibile verificare se l'estensione per l'elaborazione dati è stata distribuita correttamente nel server di report tramite il metodo <xref:ReportService2010.ReportingService2010.ListExtensions%2A> del servizio Web. È inoltre possibile aprire Gestione report e verificare che l'estensione sia inclusa nell'elenco delle origini dati disponibili. Per altre informazioni su Gestione report e sulle origini dati, vedere [Creare, modificare ed eliminare origini dati condivise &#40;SSRS&#41;](../../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione di un'estensione per l'elaborazione dati](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md)   
 [Estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Implementazione di un'estensione per l'elaborazione dati](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Libreria di estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
