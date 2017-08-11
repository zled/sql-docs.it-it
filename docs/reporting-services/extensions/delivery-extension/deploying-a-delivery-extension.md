---
title: Distribuzione di un'estensione di recapito | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
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
- delivery extensions [Reporting Services], deploying
- Extension element
- deploying [Reporting Services], extensions
ms.assetid: 4436ce48-397d-42c7-9b5d-2a267e2a1b2c
caps.latest.revision: 45
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: d072577828375a08c133bb1a68d93e652e5cf168
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="deploying-a-delivery-extension"></a>Distribuzione di un'estensione per il recapito
  Le estensioni per il recapito forniscono le informazioni di configurazione in un file di configurazione XML. Il file XML è conforme all'elemento XML Schema definito per le estensioni per il recapito. Le estensioni per il recapito forniscono l'infrastruttura per l'impostazione e la modifica del file di configurazione.  
  
 Se un'estensione per il recapito viene sostituita o aggiornata, tutte le sottoscrizioni che fanno riferimento all'estensione per il recapito rimangono valide.  
  
 Dopo avere scritto e compilato il [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] estensione per il recapito in un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] libreria, è necessario copiare l'estensione alla directory appropriata e aggiungere una voce appropriata [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] file di configurazione in modo il server di report può individuarlo.  
  
## <a name="configuration-file-extension-element"></a>Elemento Extension del file di configurazione  
 Estensioni per il recapito distribuite nel server di report devono essere immesse come **estensione** elementi nel file di configurazione. Il file di configurazione per il server di report è RSReportServer.config.  
  
 Nella tabella seguente vengono descritti gli attributi per il **estensione** elemento per estensioni per il recapito.  
  
|Attribute|Descrizione|  
|---------------|-----------------|  
|**Nome**|Nome univoco per l'estensione, ad esempio "Posta elettronica server di report" per l'estensione per il recapito tramite posta elettronica o "Condivisione file server di report" per l'estensione per il recapito tramite condivisione. La lunghezza massima consentita per l'attributo **Name** è 255 caratteri. Il nome deve essere univoco tra tutte le voci dell'elemento **Extension** di un file di configurazione. Se è presente un nome duplicato, il server di report restituirà un errore.|  
|**Tipo**|Elenco delimitato da virgole che include lo spazio dei nomi completo insieme al nome dell'assembly.|  
|**Visible**|Il valore **false** indica che l'estensione per il recapito non deve essere visibile nelle interfacce utente. Se l'attributo non è incluso, il valore predefinito è **true**.|  
  
 Per ulteriori informazioni sul file RSReportServer. config, vedere [del file di configurazione di Reporting Services](../../../reporting-services/report-server/reporting-services-configuration-files.md).  
  
## <a name="deploying-the-extension-to-the-report-server"></a>Distribuzione dell'estensione nel server di report  
 Il server di report utilizza estensioni per il recapito per l'elaborazione e il recapito di notifiche o report. È necessario distribuire l'assembly di estensioni per il recapito in un server di report come assembly privato. È inoltre necessario creare una voce nel file di configurazione del server di report, ovvero RSReportServer.config.  
  
#### <a name="to-deploy-a-deliver-extension-assembly-to-a-report-server"></a>Per distribuire un assembly di estensioni per il recapito in un server di report  
  
1.  Copiare l'assembly dal percorso di gestione temporanea nella directory bin del server di report in cui si desidera utilizzare l'estensione per il recapito. Il percorso predefinito della directory bin del server di report è %ProgramFiles%\Microsoft SQL Server\MSRS13. \<InstanceName > Services\ReportServer\bin.  
  
    > [!IMPORTANT]  
    >  Se si tenta di sovrascrivere un assembly di estensioni per il recapito esistente, è necessario arrestare il servizio del server di report prima di copiare l'assembly aggiornato. Riavviare il servizio dopo il completamento della copia dell'assembly.  
  
2.  Dopo aver copiato il file di assembly, aprire il file RSReportServer.config. Il file RSReportServer. config si trova in %ProgramFiles%\Microsoft SQL Server\MSRS13. \<InstanceName > Services\ReportServer. directory. È necessario immettere una voce nel file di configurazione per il file di assembly di estensioni per il recapito. È possibile aprire il file di configurazione con [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] o un editor di testo semplice, ad esempio Blocco note.  
  
3.  Individuare il **recapito** elemento nel file RSReportServer. config. È necessario immettere una voce per l'estensione per il recapito appena creata nel percorso seguente:  
  
    ```  
    <Extensions>  
       <Delivery>  
          <Your extension configuration information goes here>  
       </Delivery>  
    </Extensions>  
    ```  
  
4.  Aggiungere una voce per l'estensione per il recapito. La voce deve includere un **estensione** elemento con i valori per **nome** e **tipo**e potrebbe essere simile al seguente:  
  
    ```  
    <Extension Name="My Delivery Extension Name" Type="CompanyName.ExtensionName.MyDeliveryExtensionClass, AssemblyName" />  
    ```  
  
     Il valore per **nome** è il nome univoco dell'estensione per il recapito. Il valore per **tipo** è un elenco delimitato da virgole che include una voce per lo spazio dei nomi completo della classe che implementa il <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> interfaccia, seguito dal nome dell'assembly (senza l'estensione del file con estensione dll). Per impostazione predefinita, le estensioni per il recapito sono visibili. Per nascondere un'estensione dalle interfacce utente, ad esempio il portale web, aggiungere un **Visible** attributo la **estensione** elemento e impostarlo su **false**.  
  
5.  Infine, aggiungere un gruppo di codice per l'assembly personalizzato che conceda **FullTrust** l'autorizzazione per l'estensione per il recapito. Questo scopo, aggiungere il gruppo di codice per il file rssrvpolicy. config si trova per impostazione predefinita in %ProgramFiles%\Microsoft SQL Server\MSRS13. \<InstanceName > Services\ReportServer. Il gruppo di codice può essere simile a quanto riportato di seguito:  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my delivery extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS13.<InstanceName>\Reporting Services\ReportServer\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
     L'appartenenza URL è solo una delle numerose condizioni di appartenenza che è possibile scegliere per l'estensione per il recapito. Per ulteriori informazioni sulla sicurezza di accesso di codice in [!INCLUDE[ssRS](../../../includes/ssrs-md.md)], vedere.[ Proteggere Development &#40; Reporting Services &#41;](../../../reporting-services/extensions/secure-development/secure-development-reporting-services.md)  
   
## <a name="verifying-the-deployment"></a>Verifica della distribuzione  
 È possibile verificare se l'estensione per il recapito è stata distribuita correttamente nel server di report tramite il metodo <xref:ReportService2010.ReportingService2010.ListExtensions%2A> del servizio Web. È anche possibile aprire il portale web e verificare che l'estensione sia inclusa nell'elenco di estensioni per il recapito disponibili per una sottoscrizione. Per ulteriori informazioni sul portale web e le sottoscrizioni, vedere [sottoscrizioni e recapito &#40; Reporting Services &#41; ](../../../reporting-services/subscriptions/subscriptions-and-delivery-reporting-services.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di un'estensione di recapito](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Libreria di estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  

