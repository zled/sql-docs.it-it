---
title: Distribuzione di un'estensione per il recapito | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], deploying
- Extension element
- deploying [Reporting Services], extensions
ms.assetid: 4436ce48-397d-42c7-9b5d-2a267e2a1b2c
caps.latest.revision: 43
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 94b299f3bc3de16469034683df95976cfcf5510e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063063"
---
# <a name="deploying-a-delivery-extension"></a>Distribuzione di un'estensione per il recapito
  Le estensioni per il recapito forniscono le informazioni di configurazione in un file di configurazione XML. Il file XML è conforme all'elemento XML Schema definito per le estensioni per il recapito. Le estensioni per il recapito forniscono l'infrastruttura per l'impostazione e la modifica del file di configurazione.  
  
 Se un'estensione per il recapito viene sostituita o aggiornata, tutte le sottoscrizioni che fanno riferimento all'estensione per il recapito rimangono valide.  
  
 Dopo avere scritto e compilato l'estensione per il recapito [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] in una libreria [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], è necessario copiarla nella directory appropriata e aggiungere una voce al file di configurazione [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] appropriato, in modo che il server di report possa individuarla.  
  
## <a name="configuration-file-extension-element"></a>Elemento Extension del file di configurazione  
 Le estensioni per il recapito distribuite nel server di report devono essere immesse come elementi `Extension` nel file di configurazione. Il file di configurazione per il server di report è RSReportServer.config.  
  
 Nella tabella riportata di seguito vengono descritti gli attributi dell'elemento `Extension` per le estensioni per il recapito.  
  
|attribute|Description|  
|---------------|-----------------|  
|`Name`|Nome univoco per l'estensione, ad esempio "Posta elettronica server di report" per l'estensione per il recapito tramite posta elettronica o "Condivisione file server di report" per l'estensione per il recapito tramite condivisione. La lunghezza massima consentita per l'attributo `Name` è di 255 caratteri. Il nome deve essere univoco tra tutte le voci all'interno di `Extension` elemento di un file di configurazione. Se è presente un nome duplicato, il server di report restituirà un errore.|  
|`Type`|Elenco delimitato da virgole che include lo spazio dei nomi completo insieme al nome dell'assembly.|  
|`Visible`|Il valore `false` indica che l'estensione per il recapito non deve essere visibile nelle interfacce utente. Se l'attributo non è incluso, il valore predefinito è `true`.|  
  
 Per altre informazioni sul file RSReportServer.config, vedere [File di configurazione di Reporting Services](../../report-server/reporting-services-configuration-files.md).  
  
## <a name="deploying-the-extension-to-the-report-server"></a>Distribuzione dell'estensione nel server di report  
 Il server di report utilizza estensioni per il recapito per l'elaborazione e il recapito di notifiche o report. È necessario distribuire l'assembly di estensioni per il recapito in un server di report come assembly privato. È inoltre necessario creare una voce nel file di configurazione del server di report, ovvero RSReportServer.config.  
  
#### <a name="to-deploy-a-deliver-extension-assembly-to-a-report-server"></a>Per distribuire un assembly di estensioni per il recapito in un server di report  
  
1.  Copiare l'assembly dal percorso di gestione temporanea nella directory bin del server di report in cui si desidera utilizzare l'estensione per il recapito. Il percorso predefinito della directory bin server di report è %ProgramFiles%\Microsoft SQL Server\MSRS10_50. \<InstanceName > Services\ReportServer\bin.  
  
    > [!IMPORTANT]  
    >  Se si tenta di sovrascrivere un assembly di estensioni per il recapito esistente, è necessario arrestare il servizio del server di report prima di copiare l'assembly aggiornato. Riavviare il servizio dopo il completamento della copia dell'assembly.  
  
2.  Dopo aver copiato il file di assembly, aprire il file RSReportServer.config Il file RSReportServer. config si trova in %ProgramFiles%\Microsoft SQL Server\MSRS10_50. \<InstanceName > Services\ReportServer. directory. È necessario immettere una voce nel file di configurazione per il file di assembly di estensioni per il recapito. È possibile aprire il file di configurazione con [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] o con un semplice editor di testo, ad esempio Blocco note.  
  
3.  Individuare il `Delivery` elemento nel file RSReportServer. config. È necessario immettere una voce per l'estensione per il recapito appena creata nel percorso seguente:  
  
    ```  
    <Extensions>  
       <Delivery>  
          <Your extension configuration information goes here>  
       </Delivery>  
    </Extensions>  
    ```  
  
4.  Aggiungere una voce per l'estensione per il recapito. La voce deve includere un elemento `Extension` con valori per `Name` e `Type` e può essere simile a quanto riportato di seguito:  
  
    ```  
    <Extension Name="My Delivery Extension Name" Type="CompanyName.ExtensionName.MyDeliveryExtensionClass, AssemblyName" />  
    ```  
  
     Il valore per `Name` è il nome univoco dell'estensione per il recapito. Il valore per `Type` è un elenco delimitato da virgole che include una voce per lo spazio dei nomi completo della classe che implementa l'interfaccia <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension>, seguita dal nome dell'assembly, senza l'estensione dll. Per impostazione predefinita, le estensioni per il recapito sono visibili. Per nascondere un'estensione dalle interfacce utente, come Gestione report, aggiungere un attributo `Visible` all'elemento `Extension` e impostarlo su `false`.  
  
5.  Aggiungere infine un gruppo di codice per l'assembly personalizzato che conceda l'autorizzazione `FullTrust` per l'estensione per il recapito. Questo scopo, aggiungere il gruppo di codice al file rssrvpolicy config si trova per impostazione predefinita in %ProgramFiles%\Microsoft SQL Server\MSRS10_50. \<InstanceName > Services\ReportServer. Il gruppo di codice può essere simile a quanto riportato di seguito:  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my delivery extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.<InstanceName>\Reporting Services\ReportServer\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
     L'appartenenza URL è solo una delle numerose condizioni di appartenenza che è possibile scegliere per l'estensione per il recapito. Per altre informazioni sulla sicurezza dall'accesso di codice in [!INCLUDE[ssRS](../../../includes/ssrs-md.md)], vedere [Sviluppo sicuro &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md)  
  
## <a name="deploying-the-extension-to-report-manager"></a>Distribuzione dell'estensione in Gestione report  
 Se l'estensione per il recapito implementa l'interfaccia <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl>, può essere utilizzata con la pagina di sottoscrizione di Gestione report. Per rendere disponibile l'interfaccia utente di sottoscrizione, è necessario distribuire l'estensione in Gestione report.  
  
#### <a name="to-deploy-a-deliver-extension-assembly-to-report-manager"></a>Per distribuire un assembly di estensioni per il recapito in Gestione report  
  
1.  Copiare l'assembly dal percorso di gestione temporanea nella directory bin di Gestione report. Il percorso predefinito della directory bin di gestione Report è %ProgramFiles%\Microsoft SQL Server\MSRS10_50. \<InstanceName > services\reportmanager\bin.  
  
2.  Dopo aver copiato il file di assembly, aprire il file RSReportServer.config Il file RSReportServer. config si trova in %ProgramFiles%\Microsoft SQL Server\MSRS10_50. \<InstanceName > Services\ReportServer. directory. È necessario immettere una voce nel file di configurazione per il file di assembly di estensioni per il recapito. È possibile aprire il file di configurazione con un semplice editor di testo, ad esempio Blocco note o Visual Studio .NET.  
  
3.  Individuare il `DeliveryUI` elemento nel file RSReportServer. config. È necessario immettere una voce per l'estensione per il recapito appena creata nel percorso seguente:  
  
    ```  
    <Extensions>  
       <DeliveryUI>  
          <Your extension configuration information goes here>  
       </DeliveryUI>  
    </Extensions>  
    ```  
  
4.  Aggiungere una voce per l'estensione per il recapito. La voce deve includere un elemento `Extension` con valori per `Name` e `Type` e può essere simile a quanto riportato di seguito:  
  
    ```  
    <Extension Name="My Delivery Extension Name" Type="CompanyName.ExtensionName.MyDeliveryUIExtensionClass, AssemblyName" />  
    ```  
  
     Il valore per `Name` è il nome univoco dell'estensione per il recapito. Il valore per `Type` è un elenco delimitato da virgole che include una voce per lo spazio dei nomi completo della classe che implementa l'interfaccia <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl>, seguita dal nome dell'assembly, senza l'estensione dll.  
  
    > [!IMPORTANT]  
    >  Il valore dell'attributo `Name` deve essere identico per le voci dei file di configurazione del server di report e di Gestione report. Se non sono identici, la configurazione del server non è valida.  
  
     Aggiungere infine un gruppo di codice per l'assembly personalizzato che conceda l'autorizzazione `FullTrust` per l'estensione per il recapito. Questo scopo, aggiungere il gruppo di codice al file Rsmgrpolicy config che si trova per impostazione predefinita in C:\Program Files\Microsoft SQL Server\MSRS10_50. \<InstanceName > Services\ReportManager. Il gruppo di codice può essere simile a quanto riportato di seguito:  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my delivery UI extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.<InstanceName>\Reporting Services\ReportManager\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
     L'appartenenza URL è solo una delle numerose condizioni di appartenenza che è possibile scegliere per l'estensione per il recapito. Per altre informazioni sulla sicurezza dall'accesso di codice in [!INCLUDE[ssRS](../../../includes/ssrs-md.md)], vedere [Sviluppo sicuro &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md)  
  
## <a name="verifying-the-deployment"></a>Verifica della distribuzione  
 È possibile verificare se l'estensione per il recapito è stata distribuita correttamente nel server di report tramite il metodo <xref:ReportService2010.ReportingService2010.ListExtensions%2A> del servizio Web. È inoltre possibile aprire Gestione report e verificare che l'estensione sia inclusa nell'elenco delle estensioni per il recapito disponibili per una sottoscrizione. Per ulteriori informazioni su gestione Report e le sottoscrizioni, vedere [sottoscrizioni e recapito &#40;Reporting Services&#41;](../../subscriptions/subscriptions-and-delivery-reporting-services.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di un'estensione per il recapito](implementing-a-delivery-extension.md)   
 [Libreria di estensioni di Reporting Services](../reporting-services-extension-library.md)  
  
  