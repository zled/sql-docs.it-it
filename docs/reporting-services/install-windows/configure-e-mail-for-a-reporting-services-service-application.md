---
title: Configurare la posta elettronica per l'applicazione di servizio di Reporting Services | Documenti Microsoft
ms.custom: 
ms.date: 05/10/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 38fc34a6-aae7-4dde-9ad2-f1eee0c42a9f
caps.latest.revision: 13
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 23cf66b01385b3c0f3e9ddc6ff24ea578cf5eec3
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="configure-e-mail-for-a-reporting-services-service-application"></a>Configurare le impostazioni di posta elettronica per l'applicazione di servizio Reporting Services

[!INCLUDE[ssrs-appliesto-sql2016-xpreview](../../includes/ssrs-appliesto-sql2016-xpreview.md)][!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)]

[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] gli avvisi dati consentono di inviare avvisi come messaggi di posta elettronica. Per inviare messaggi di posta elettronica potrebbe essere necessario configurare l'applicazione di servizio [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , nonché modificare l'estensione per il recapito tramite posta elettronica per l'applicazione di servizio. Le impostazioni della posta elettronica sono anche richieste se si prevede di utilizzare l'estensione per il recapito tramite posta elettronica per la funzionalità di sottoscrizione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  

> [!NOTE]
> Integrazione con SharePoint di Reporting Services non è più disponibile dopo SQL Server 2016.
  
### <a name="to-configure-e-mail-for-the-shared-service"></a>Per configurare le impostazioni di posta elettronica per il servizio condiviso  
  
1.  In Amministrazione centrale SharePoint, fare clic su **Gestione dell'applicazione**.  
  
2.  Nel gruppo **Applicazioni di servizio** fare clic su **Gestisci applicazioni di servizio**.  
  
3.  Nell'elenco **Nome** fare clic sul nome dell'applicazione di servizio [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
4.  Fare clic su **Impostazioni posta elettronica** nella pagina **Gestione applicazione di Reporting Services** .  
  
5.  Selezionare **Utilizza server SMTP**.  
  
6.  Nella casella **Server SMTP in uscita** digitare il nome di un server SMTP.  
  
7.  Nella casella **Indirizzo mittente** digitare un indirizzo di posta elettronica.  
  
     Questo indirizzo è il mittente di tutti i messaggi di posta elettronica di avviso.  
  
     L'account dell'utente specificato in **Indirizzo mittente** deve essere un account gestito specificato quando il pool di applicazioni è stato configurato per l'applicazione di servizio [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Se si dispone delle autorizzazioni, è possibile visualizzare un elenco di account gestiti esistenti nella pagina Account di servizio in Amministrazione centrale SharePoint.  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="ntlm-authentication"></a>Autenticazione NTLM  
  
1.  Se il proprio ambiente di posta elettronica richiede l'autenticazione NTLM e non consente l'accesso anonimo, è necessario modificare la configurazione dell'estensione per il recapito tramite posta elettronica per le applicazioni di servizio di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Ad esempio, se viene visualizzato il messaggio seguente per **Ultimi risultati** nella pagina **Gestisci sottoscrizioni** page:subscriptions.  
  
    -   Errore durante l'invio della posta: Il server SMTP richiede una connessione protetta oppure il client non è stato autenticato. Risposta del server: 5.7.1 Client non autenticato. La posta non verrà inviata nuovamente.  
  
     Modificare **SMTPAuthenticate** per utilizzare un valore "2". Non è possibile modificare questo valore dall'interfaccia utente. Nell'esempio di script PowerShell seguente, viene aggiornata la configurazione per l'estensione per il recapito tramite posta elettronica del server di report per l'applicazione di servizio denominata “SSRS_TESTAPPLICATION”. Alcuni dei nodi elencati nello script possono anche essere impostati dall'interfaccia utente, ad esempio l'indirizzo “Da”.  
  
    ```  
    $app=get-sprsserviceapplication |where {$_.name -like "SSRS_TESTAPPLICATION *"}  
    $emailCfg = Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml   
    $emailXml = [xml]$emailCfg   
    $emailXml.SelectSingleNode("//SMTPServer").InnerText = “your email server name"  
    $emailXml.SelectSingleNode("//SendUsing").InnerText = "2"  
    $emailXml.SelectSingleNode("//SMTPAuthenticate").InnerText = "2"  
    $emailXml.SelectSingleNode("//From").InnerText = “your FROM email address”  
    Set-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" -ExtensionConfiguration $emailXml.OuterXml  
    ```  
  
2.  Se è necessario verificare il nome dell'applicazione di servizio, eseguire **Get-SPRSServiceApplication cmdlet**.  
  
    ```  
    get-sprsserviceapplication  
    ```  
  
3.  Nell'esempio seguente, vengono restituiti i valori correnti dell'estensione per il recapito tramite posta elettronica per l'applicazione di servizio denominata “SSRS_TESTAPPLICATION”.  
  
    ```  
    $app=get-sprsserviceapplication |where {$_.name -like "SSRSTEST_APPLICATION*"}  
    Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml  
    ```  
  
4.  Nell'esempio seguente, viene creato un nuovo file denominato “emailconfig.txt” con i valori correnti dell'estensione per il recapito tramite posta elettronica per l'applicazione di servizio denominata “SSRS_TESTAPPLICATION”  
  
    ```  
    $app=get-sprsserviceapplication |where {$_.name -like "SSRS_TESTAPPLICATION*"}  
    Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml | out-file c:\emailconfig.txt  
    ```  
  
  
Ulteriori domande? [Provare a porre il forum di Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
