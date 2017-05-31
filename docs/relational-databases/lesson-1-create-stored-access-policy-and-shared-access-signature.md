---
title: 'Lezione 1: Creare criteri di accesso archiviati e una firma di accesso condiviso | Microsoft Docs'
ms.custom:
- SQL2016_New_Updated
ms.date: 06/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: 41674d9d-8132-4bff-be4d-85a861419f3d
caps.latest.revision: 22
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f2c8af4701b9a01ee21613fe7e093a89f1d8f990
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="lesson-1-create-stored-access-policy-and-shared-access-signature"></a>Lezione 1: Creare criteri di accesso archiviati e una firma di accesso condiviso
In questa lezione si userà uno [script Azure PowerShell](https://azure.microsoft.com/en-us/documentation/articles/powershell-install-configure/) per creare una firma di accesso condiviso in un contenitore BLOB di Azure tramite criteri di accesso archiviati.  
  
> [!NOTE]  
> Questo script è stato scritto con Azure PowerShell 5.0.10586.  
  
Una firma di accesso condivisa è un URI che concede diritti di accesso limitati a contenitori, BLOB, code o tabelle. I criteri di accesso archiviati garantiscono un livello di controllo aggiuntivo sulle firme di accesso condivise sul lato server, ad esempio revoca, scadenza ed estensione dei diritti di accesso. Per usare questi nuovi miglioramenti, è necessario creare in un contenitore criteri con almeno diritti di lettura, scrittura ed elenco.  
  
È possibile creare criteri di accesso archiviati e una firma di accesso condiviso usando Azure PowerShell, Azure Storage SDK, l'API REST di Azure o un'utilità di terze parti. Questa esercitazione illustra come usare uno script Azure PowerShell per completare questa attività. Lo script usa il modello di distribuzione Resource Manager e crea le nuove risorse seguenti  
  
-   Gruppo di risorse  
  
-   Account di archiviazione  
  
-   Contenitore BLOB di Azure  
  
-   Criteri di firma di accesso condiviso  
  
Questo script inizia con la dichiarazione di variabili con le quali specificare i nomi per le risorse indicate sopra e i nomi dei valori di input necessari seguenti:  
  
-   Nome di prefisso usato nei nomi di altri oggetti risorsa  
  
-   Nome sottoscrizione  
  
-   Ubicazione data center  
  
> [!NOTE]  
> Questo script viene scritto in modo da consentire l'uso di Azure Resource Manager esistente o di risorse classiche del modello di distribuzione.  
  
Lo script viene completato generando l'istruzione CREATE CREDENTIAL appropriata che sarà usata nella [Lezione 2: Creare credenziali di SQL Server usando una firma di accesso condiviso](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md). Questa istruzione viene copiata negli Appunti e viene visualizzata nella console.  
  
Per creare i criteri per il contenitore e generare una chiave di firma di accesso condivisa, seguire questa procedura:  
  
1.  Aprire Windows PowerShell o Windows PowerShell ISE (vedere i requisiti della versione precedenti).  
  
2.  Modificare ed eseguire la query seguente.  
  
    ```  
    \<#   
    This script uses the Azure Resource model and creates a new ARM storage account.  
    Modify this script to use an existing ARM or classic storage account   
    using the instructions in comments within this script  
    #>  
    # Define global variables for the script  
    $prefixName = '<a prefix name>'  # used as the prefix for the name for various objects  
    $subscriptionName='<your subscription name>'   # the name  of subscription name you will use  
    $locationName = '<a data center location>'  # the data center region you will use  
    $storageAccountName= $prefixName + 'storage' # the storage account name you will create or use  
    $containerName= $prefixName + 'container'  # the storage container name to which you will attach the SAS policy with its SAS token  
    $policyName = $prefixName + 'policy' # the name of the SAS policy  
  
    \<#   
    Using Azure Resource Manager deployment model  
    Comment out this entire section and use the classic storage account name to use an existing classic storage account  
    #>  
  
    # Set a variable for the name of the resource group you will create or use  
    $resourceGroupName=$prefixName + 'rg'   
  
    # adds an authenticated Azure account for use in the session   
    Login-AzureRmAccount    
  
    # set the tenant, subscription and environment for use in the rest of   
    Set-AzureRmContext -SubscriptionName $subscriptionName   
  
    # create a new resource group - comment out this line to use an existing resource group  
    New-AzureRmResourceGroup -Name $resourceGroupName -Location $locationName   
  
    # Create a new ARM storage account - comment out this line to use an existing ARM storage account  
    New-AzureRmStorageAccount -Name $storageAccountName -ResourceGroupName $resourceGroupName -Type Standard_RAGRS -Location $locationName   
  
    # Get the access keys for the ARM storage account  
    $accountKeys = Get-AzureRmStorageAccountKey -ResourceGroupName $resourceGroupName -Name $storageAccountName  
  
    # Create a new storage account context using an ARM storage account  
    $storageContext = New-AzureStorageContext -StorageAccountName $storageAccountName -StorageAccountKey $accountKeys[0].Value 
  
    \<#  
    Using the Classic deployment model  
    Use the following four lines to use an existing classic storage account  
    #>  
    #Classic storage account name  
    #Add-AzureAccount  
    #Select-AzureSubscription -SubscriptionName $subscriptionName #provide an existing classic storage account  
    #$accountKeys = Get-AzureStorageKey -StorageAccountName $storageAccountName  
    #$storageContext = New-AzureStorageContext -StorageAccountName $storageAccountName -StorageAccountKey $accountKeys.Primary  
  
    # The remainder of this script works with either the ARM or classic sections of code above  
  
    # Creates a new container in blob storage  
    $container = New-AzureStorageContainer -Context $storageContext -Name $containerName  
    $cbc = $container.CloudBlobContainer  
  
    # Sets up a Stored Access Policy and a Shared Access Signature for the new container  
    $permissions = $cbc.GetPermissions();  
    $policyName = $policyName  
    $policy = new-object 'Microsoft.WindowsAzure.Storage.Blob.SharedAccessBlobPolicy'  
    $policy.SharedAccessStartTime = $(Get-Date).ToUniversalTime().AddMinutes(-5)  
    $policy.SharedAccessExpiryTime = $(Get-Date).ToUniversalTime().AddYears(10)  
    $policy.Permissions = "Read,Write,List,Delete"  
    $permissions.SharedAccessPolicies.Add($policyName, $policy)  
    $cbc.SetPermissions($permissions);  
  
    # Gets the Shared Access Signature for the policy  
    $policy = new-object 'Microsoft.WindowsAzure.Storage.Blob.SharedAccessBlobPolicy'  
    $sas = $cbc.GetSharedAccessSignature($policy, $policyName)  
    Write-Host 'Shared Access Signature= '$($sas.Substring(1))''  
  
    # Outputs the Transact SQL to the clipboard and to the screen to create the credential using the Shared Access Signature  
    Write-Host 'Credential T-SQL'  
    $tSql = "CREATE CREDENTIAL [{0}] WITH IDENTITY='Shared Access Signature', SECRET='{1}'" -f $cbc.Uri,$sas.Substring(1)   
    $tSql | clip  
    Write-Host $tSql  
  
    ```  
  
3.  Dopo aver completato lo script, l'istruzione CREATE CREDENTIAL sarà aggiunta agli Appunti perché sia possibile usarla nella lezione successiva.  
  
**Lezione successiva:**  
  
[Lezione 2: Creare credenziali di SQL Server usando una firma di accesso condiviso](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)  
  
## <a name="see-also"></a>Vedere anche  
[Uso delle firme di accesso condiviso, parte 1: conoscere il modello di firma di accesso condiviso](https://azure.microsoft.com/en-us/documentation/articles/storage-dotnet-shared-access-signature-part-1/)  
[Create Container](https://msdn.microsoft.com/library/azure/dd179468.aspx)  
[Set Container ACL](https://msdn.microsoft.com/library/azure/dd179391.aspx)  
[Get Container ACL](https://msdn.microsoft.com/library/azure/dd179469.aspx)  
  
  
  


