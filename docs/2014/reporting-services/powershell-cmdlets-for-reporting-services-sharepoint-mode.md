---
title: Cmdlet di PowerShell per Reporting Services SharePoint Mode | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7835bc97-2827-4215-b0dd-52f692ce5e02
caps.latest.revision: 30
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 29a9177685d94be437574e90a44a46a2391bcba7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37311363"
---
# <a name="powershell-cmdlets-for-reporting-services-sharepoint-mode"></a>Cmdlet di PowerShell per la modalità SharePoint di Reporting Services
  Quando si installa la modalità SharePoint di [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , i cmdlet di PowerShell sono installati per supportare i server di report in modalità SharePoint. I cmdlets riguardano tre categorie di funzionalità.  
  
-   Installazione del [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] proxy e del servizio condiviso di SharePoint.  
  
-   Il provisioning e la gestione di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service di applicazioni e dei proxy associati.  
  
-   Gestione delle funzionalità di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , ad esempio estensioni e chiavi di crittografia.  
  
||  
|-|  
|[!INCLUDE[applies](../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in modalità SharePoint|  
  
 **In questo argomento sono contenute le sezioni seguenti:**  
  
-   [Riepilogo dei cmdlet](#bkmk_cmdlet_sum)  
  
-   [Cmdlet del servizio condiviso e del proxy](#bkmk_sharedservice_cmdlets)  
  
-   [Cmdlet dell'applicazione di servizio e del proxy](#bkmk_serviceapp_cmdlets)  
  
-   [Cmdlet correlati alle funzionalità personalizzate di Reporting Services](#bkmk_ssrsfeatures_cmdlets)  
  
-   [Esempi di base](#bkmk_basic_samples)  
  
-   [Esempi dettagliati](#bkmk_detailedsamples)  
  
    -   [Creare un proxy e un'applicazione di servizio Reporting Services](#bkmk_example_create_service_application)  
  
    -   [Rivedere e aggiornare un'estensione di recapito di Reporting Services](#bkmk_example_delivery_extension)  
  
    -   [Ottenere e impostare le proprietà del database dell'applicazione Reporting Service, ad esempio timeout database](#bkmk_example_db_properties)  
  
    -   [Elenco di estensioni per i dati reporting services – modalità SharePoint](#bkmk_example_list_data_extensions)  
  
    -   [Modificare ed elencare i proprietari di sottoscrizioni](#bkmk_change_subscription_owner)  
  
##  <a name="bkmk_cmdlet_sum"></a> Riepilogo dei cmdlet  
 Per eseguire i cmdlet è necessario aprire la shell di gestione SharePoint. È anche possibile usare l'editor dell'interfaccia utente grafica incluso in Microsoft Windows, **Windows PowerShell Integrated Scripting Environment (ISE)**. Per altre informazioni, vedere [avvio di Windows PowerShell in Windows Server](http://technet.microsoft.com/library/hh847814.aspx) (http://technet.microsoft.com/library/hh847814.aspx). Nei riepiloghi di cmdlet seguenti, i riferimenti ai database delle applicazioni di servizio indicano tutti i database creati e utilizzati da un'applicazione di servizio [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Sono inclusi i database di configurazione, di avvisi e temporaneo.  
  
 Se quando si digitano gli esempi di PowerShell si visualizza un messaggio di errore simile al seguente:  
  
-   Install-SPRSService: Termine 'Install-SPRSService' non riconosciuto come  
    nome di cmdlet, funzione, programma eseguibile o file script. Verificare l'ortografia del nome, che il percorso sia incluso e corretto, quindi riprovare.  
  
 Si è verificato uno dei problemi seguenti:  
  
-   [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Non è installata in modalità SharePoint e pertanto il [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] non vengono installati i cmdlet.  
  
-   Il comando di PowerShell è stato eseguito in Windows PowerShell o Windows PowerShell ISE anziché nella shell di gestione di SharePoint. Utilizzare la shell di gestione di SharePoint o aggiungere lo snap-in SharePoint alla finestra di Windows PowerShell con il comando seguente:  
  
    ```  
    Add-PSSnapin Microsoft.SharePoint.PowerShell  
    ```  
  
 Per altre informazioni, vedere [utilizzare Windows PowerShell per amministrare SharePoint 2013](http://technet.microsoft.com/library/ee806878.aspx) (http://technet.microsoft.com/library/ee806878.aspx).  
  
#### <a name="to-open-the-sharepoint-management-shell-and-run-cmdlets"></a>Per aprire la shell di gestione di SharePoint ed eseguire i cmdlet  
  
1.  Fare clic sul menu **Start** .  
  
2.  Fare clic sul gruppo **Prodotti Microsoft SharePoint** .  
  
3.  Fare clic su **Shell di gestione SharePoint**.  
  
 Per visualizzare le informazioni della Guida relative alla riga di comando per un cmdlet, usare il comando PowerShell "Get-Help" al prompt dei comandi di PowerShell. Esempio:  
  
 `Get-Help Get-SPRSServiceApplicationServers`  
  
###  <a name="bkmk_sharedservice_cmdlets"></a> Cmdlet del servizio condiviso e del proxy  
 Nella tabella seguente sono elencati i cmdlet di PowerShell per il servizio SharePoint Shared di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
|Cmdlet|Description|  
|------------|-----------------|  
|Install-SPRSService|Installa e registra, o disinstalla, il servizio SharePoint Shared di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Queste operazioni possono essere eseguite solo nel computer in cui è installato SQL Server [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in modalità SharePoint. Per l'installazione, vengono eseguite due operazioni:<br /><br /> 1) al [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service è installato nella farm.<br /><br /> 2) il [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] l'istanza del servizio è installato nel computer corrente.<br /><br /> Per la disinstallazione, vengono eseguite due operazioni:<br />1) al [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] servizio viene disinstallato dal computer corrente.<br />2) il [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] servizio viene disinstallato dalla farm.<br /><br /> <br /><br /> Nota: Se sono presenti altri computer della farm con il [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] installato, il servizio o se non esistono ancora [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] applicazioni di servizio in esecuzione nella farm, viene visualizzato un messaggio di avviso.|  
|Install-SPRSServiceProxy|Installa e registra, o disinstalla, il proxy del servizio Reporting Services nella farm di SharePoint.|  
|Get-SPRSProxyUrl|Ottiene gli URL per l'accesso al [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] servizio.|  
|Get-SPRSServiceApplicationServers|Ottiene tutti i server nella farm di SharePoint locale contenenti un'installazione del servizio SharePoint Shared di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Questo cmdlet è utile per gli aggiornamenti di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , per determinare i server in cui viene eseguito il servizio condiviso e pertanto devono essere aggiornati.|  
  
###  <a name="bkmk_serviceapp_cmdlets"></a> Cmdlet dell'applicazione di servizio e del proxy  
 Nella tabella seguente sono elencati i cmdlet di PowerShell per le applicazioni di servizio [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] e i proxy associati.  
  
|Cmdlet|Description|  
|------------|-----------------|  
|Get-SPRSServiceApplication|Ottiene uno o più oggetti dell'applicazione di servizio [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].|  
|New-SPRSServiceApplication|Crea una nuova applicazione di servizio Reporting Services e i database associati.<br /><br /> Parametro LogonType: consente di specificare se nel server di report viene utilizzato un account del pool di applicazioni SSRS o un account di accesso di SQL Server per accedere al database del server di report. I possibili valori sono i seguenti:<br /><br /> 0 Autenticazione di Windows<br /><br /> 1 SQL Server<br /><br /> 2 Account pool applicazioni (impostazione predefinita)|  
|Remove-SPRSServiceApplication|Rimuove l'applicazione di servizio Reporting Services specificata. Vengono rimossi anche i database associati.|  
|Set-SPRSServiceApplication|Modifica le proprietà di un'applicazione di servizio Reporting Services esistente.|  
|New-SPRSServiceApplicationProxy|Crea un nuovo proxy dell'applicazione di servizio Reporting Services.|  
|Get-SPRSServiceApplicationProxy|Ottiene uno o più [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] proxy dell'applicazione del servizio.|  
|Dismount-SPRSDatabase|Smonta i database dell'applicazione di servizio per un'applicazione di servizio [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].|  
|Remove-SPRSDatabase|Rimuovere i database dell'applicazione di servizio per un [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] applicazione del servizio.|  
|Set-SPRSDatabase|Imposta le proprietà dei database associati a un'applicazione di servizio [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].|  
|Mount-SPRSDatabase|Monta i database per un [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] applicazione del servizio.|  
|New-SPRSDatabase|Creare nuovi database dell'applicazione di servizio per l'oggetto specificato [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] applicazione del servizio.|  
|Get-SPRSDatabaseCreationScript|Visualizza lo script di creazione del database per un'applicazione di servizio [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. È quindi possibile eseguire lo script in SQL Server Management Studio.|  
|Get-SPRSDatabase|Ottiene uno o più database dell'applicazione di servizio [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Usare il comando per ottenere l'ID del database dell'applicazione di servizio in modo da potere usare il cmdlet Set-SPRSDatabase per modificare le proprietà, ad esempio `querytimeout`. Vedere l'esempio nell'argomento [Ottenere e impostare le proprietà del database dell'applicazione Reporting Service, ad esempio timeout database](#bkmk_example_db_properties).|  
|Get-SPRSDatabaseRightsScript|Genera lo script diritti del database alla schermata di un [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] applicazione del servizio. Vengono richiesti l'utente desiderato e il database, quindi viene restituita l'istruzione Transact-SQL che è possibile eseguire per modificare le autorizzazioni. È quindi possibile eseguire lo script in SQL Server Management Studio.|  
|Get-SPRSDatabaseUpgradeScript|Visualizza uno script di aggiornamento del database. Lo script consente di aggiornare i database dell'applicazione di servizio [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] alla versione del database dell'installazione di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] corrente.|  
  
###  <a name="bkmk_ssrsfeatures_cmdlets"></a> Cmdlet correlati alle funzionalità personalizzate di Reporting Services  
  
|Cmdlet|Description|  
|------------|-----------------|  
|Update-SPRSEncryptionKey|Aggiorna la chiave di crittografia per l'applicazione di servizio Reporting Services specificata ed esegue di nuovo la crittografia dei dati.|  
|Restore-SPRSEncryptionKey|Ripristina una chiave di crittografia di cui in precedenza è stato eseguito il backup per un'applicazione di servizio Reporting Services.|  
|Remove-SPRSEncryptedData|Elimina i dati crittografati per l'applicazione di servizio Reporting Services specificata.|  
|Backup-SPRSEncryptionKey|Esegue il backup della chiave di crittografia per l'applicazione di servizio Reporting Services specificata.|  
|New-SPRSExtension|Registra una nuova estensione con un'applicazione di servizio Reporting Services.|  
|Set-SPRSExtension|Imposta le proprietà di un'estensione di Reporting Services esistente.|  
|Remove-SPRSExtension|Rimuove un'estensione da un'applicazione di servizio Reporting Services.|  
|Get-SPRSExtension|Ottiene uno o più [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] estensioni per una [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] applicazione del servizio.<br /><br /> I valori validi sono:<br /><br /> **Recapito**<br /><br /> **DeliveryUI**<br /><br /> **Rendering**<br /><br /> **Dati**<br /><br /> **Security**<br /><br /> **Autenticazione**<br /><br /> **EventProcessing**<br /><br /> **ReportItems**<br /><br /> **Progettazione**<br /><br /> **ReportItemDesigner**<br /><br /> **ReportItemConverter**<br /><br /> **ReportDefinitionCustomization**|  
|Get-SPRSSite|Ottiene i siti di SharePoint in base all'eventuale abilitazione della funzionalità "ReportingService". Per impostazione predefinita, vengono restituiti i siti in cui la funzionalità "ReportingService" è abilitata.|  
  
##  <a name="bkmk_basic_samples"></a> Esempi di base  
 Restituire un elenco di cmdlet contenenti "SPRS" nel nome. Questo sarà l'elenco completo dei [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] cmdlet.  
  
```  
Get-command –noun *SPRS*  
```  
  
 In alternativa, con un livello leggermente maggiore di dettaglio, inoltrare tramite pipe in un file di testo denominato commandlist.txt.  
  
```  
Get-command -noun *SPRS* | Select name, definition | Format-List | Out-File c:\commandlist.txt  
```  
  
 Installare il proxy del servizio e il servizio SharePoint di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
```  
Install-SPRSService  
```  
  
```  
Install-SPRSServiceProxy  
```  
  
 Avviare il [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] servizio  
  
```  
get-spserviceinstance -all |where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
```  
  
 Digitare il comando seguente dalla Shell di gestione di SharePoint per ottenere un elenco filtrato di righe del file di log. Con il comando verranno filtrate le righe contenenti "ssrscustomactionerror". In questo esempio viene analizzato il file di log creato al momento dell'installazione di rssharepoint.msi.  
  
```  
Get-content -path C:\Users\testuser\AppData\Local\Temp\rs_sp_0.log | select-string "ssrscustomactionerror"  
```  
  
##  <a name="bkmk_detailedsamples"></a> Esempi dettagliati  
 Oltre ai seguenti esempi, vedere la sezione “Script di Windows PowerShell” nell'argomento [Script di Windows PowerShell per i passaggi da 1 a 4](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md#bkmk_full_script).  
  
###  <a name="bkmk_example_create_service_application"></a> Creare un proxy e un'applicazione di servizio Reporting Services  
 Questo script di esempio consente di completare le attività seguenti:  
  
1.  Creare un proxy e un'applicazione di servizio Reporting Services. Per lo script si presuppone che il pool di applicazioni "My App Pool" esista già.  
  
2.  Aggiungere il proxy al gruppo di proxy predefiniti.  
  
3.  Concedere all'applicazione di servizio l'accesso al database del contenuto dell'applicazione Web sulla porta 80. Lo script presuppone che il sito "http://sitename" esiste già.  
  
```  
# Create service application and service application proxy  
$appPool = Get-SPServiceApplicationPool “My App Pool”  
$serviceApp = New-SPRSServiceApplication “My RS Service App” –ApplicationPool $appPool  
$serviceAppProxy = New-SPRSServiceApplicationProxy –Name “My RS Service App Proxy” –ServiceApplication $serviceApp  
  
# Add service application proxy to default proxy group.  Any web application that uses the default proxy group will now be able to use this service application.  
Get-SPServiceApplicationProxyGroup –default | Add-SPServiceApplicationProxyGroupMember –Member $serviceAppProxy  
  
# Grant application pool account access to the port 80 web application’s content database.  
$webApp = Get-SPWebApplication “http://sitename”  
$appPoolAccountName = $appPool.ProcessAccount.LookupName()  
$webApp.GrantAccessToProcessIdentity($appPoolAccountName)  
  
```  
  
###  <a name="bkmk_example_delivery_extension"></a> Rivedere e aggiornare un'estensione di recapito di Reporting Services  
 Nell'esempio di script di PowerShell seguente viene aggiornata la configurazione dell'estensione per il recapito tramite posta elettronica del server di report per l'applicazione di servizio denominata `My RS Service App`. Aggiornare i valori per il server SMTP (`<email server name>`) e l'alias di posta elettronica FROM (`<your FROM email address>`).  
  
```  
$app=get-sprsserviceapplication -Name "My RS Service App"  
$emailCfg = Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml   
$emailXml = [xml]$emailCfg   
$emailXml.SelectSingleNode("//SMTPServer").InnerText = “<email server name>”  
$emailXml.SelectSingleNode("//SendUsing").InnerText = "2"  
$emailXml.SelectSingleNode("//SMTPAuthenticate").InnerText = "2"  
$emailXml.SelectSingleNode("//From").InnerText = '<your FROM email address>'  
Set-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" -ExtensionConfiguration $emailXml.OuterXml  
```  
  
 Nell'esempio precedente, se non si conosce il nome esatto dell'applicazione di servizio, è possibile riscrivere la prima istruzione per ottenere l'applicazione di servizio in base a una ricerca del nome parziale. Esempio:  
  
```  
$app=get-sprsserviceapplication | where {$_.name -like " ssrs_testapp *"}  
```  
  
 Lo script seguente restituisce i valori di configurazione correnti per l'estensione per il recapito tramite posta elettronica del server di report per l'applicazione di servizio denominata "Applicazione di Reporting Services". Il primo passaggio consente di impostare il valore della variabile $app sull'oggetto applicazione di servizio denominato "My RS Service App"  
  
 La seconda istruzione consente di ottenere l'estensione per il recapito "Report Server Email" per l'oggetto applicazione di servizio nella variabile $app e di selezionare configurationXML.  
  
```  
$app=get-sprsserviceapplication –Name "Reporting Services Application"  
Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml  
```  
  
 È inoltre possibile riscrivere le due istruzioni sopra riportate come un'unica istruzione:  
  
```  
get-sprsserviceapplication –Name "Reporting Services Application" | Get-SPRSExtension -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml  
```  
  
###  <a name="bkmk_example_db_properties"></a> Ottenere e impostare le proprietà del database dell'applicazione Reporting Service, ad esempio timeout database  
 L'esempio seguente restituisce innanzitutto un elenco dei database e delle proprietà in modo da potere determinare il GUID del database da fornire al comando set. Per un elenco completo delle proprietà, usare `Get-SPRSDatabase | format-list`.  
  
```  
get-SPRSDatabase | select id, querytimeout,connectiontimeout, status, server, ServiceInstance   
```  
  
 Di seguito è riportato un esempio dell'output. Determinare l'ID del database da modificare e usare l'ID nel cmdlet SET.  
  
-   `Id                : 56f8d1bc-cb04-44cf-bd41-a873643c5a14`  
  
     `QueryTimeout      : 120`  
  
     `ConnectionTimeout : 15`  
  
     `Status            : Online`  
  
     `Server            : SPServer Name=uetestb01`  
  
     `ServiceInstance   : SPDatabaseServiceInstance`  
  
```  
Set-SPRSDatabase –identity 56f8d1bc-cb04-44cf-bd41-a873643c5a14 -QueryTimeout 300  
```  
  
 Per verificare il valore impostato, eseguire di nuovo il cmdlet GET.  
  
```  
Get-SPRSDatabase –identity 56f8d1bc-cb04-44cf-bd41-a873643c5a14 | select id, querytimeout,connectiontimeout, status, server, ServiceInstance  
```  
  
###  <a name="bkmk_example_list_data_extensions"></a> Elenco di estensioni per i dati reporting services – modalità SharePoint  
 L'esempio seguente esegue il ciclo di ogni applicazione di servizio di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ed elenca le estensioni per i dati per ogni applicazione.  
  
```  
$apps = Get-SPRSServiceApplication  
foreach ($app in $apps)   
{  
Write-host -ForegroundColor "yellow" Service App Name $app.Name  
Get-SPRSExtension -identity $app -ExtensionType “Data” | select name,extensiontype | Format-Table -AutoSize  
}  
```  
  
 **Output di esempio:**  
  
-   `Name           ExtensionType`  
  
     `----           -------------`  
  
     `SQL                     Data`  
  
     `SQLAZURE                Data`  
  
     `SQLPDW                  Data`  
  
     `OLEDB                   Data`  
  
     `OLEDB-MD                Data`  
  
     `ORACLE                  Data`  
  
     `ODBC                    Data`  
  
     `XML                     Data`  
  
     `SHAREPOINTLIST          Data`  
  
###  <a name="bkmk_change_subscription_owner"></a> Modificare ed elencare i proprietari di sottoscrizioni  
 Vedere [Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](subscriptions/manage-subscription-owners-and-run-subscription-powershell.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Usare PowerShell per modificare ed elencare i proprietari di sottoscrizioni di Reporting Services ed eseguire una sottoscrizione](subscriptions/manage-subscription-owners-and-run-subscription-powershell.md)   
 [Elenco di controllo: Usare PowerShell per verificare PowerPivot per SharePoint](../analysis-services/instances/install-windows/checklist-use-powershell-to-verify-power-pivot-for-sharepoint.md)   
 [Script di PowerShell di gestione di SharePoint nel sito CodePlex](http://sharepointpsscripts.codeplex.com/)   
 [Come amministrare SSRS con PowerShell](https://curatedviews.cloudapp.net/13107/how-to-administer-ssrs-using-powershell)  
  
  
