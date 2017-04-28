---
title: Gestire l&quot;autenticazione nel motore di database PowerShell | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ab9212a6-6628-4f08-a38c-d3156e05ddea
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 135580dd67315ad9eb07361dcff7b1334398a0aa
ms.lasthandoff: 04/11/2017

---
# <a name="manage-authentication-in-database-engine-powershell"></a>Gestire l'autenticazione in motore di database PowerShell
  Per impostazione predefinita, i componenti PowerShell di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzano l'autenticazione di Windows in caso di connessione a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)]. È possibile usare l'autenticazione di SQL Server definendo un'unità virtuale PowerShell o specificando i parametri **–Username** e **–Password** per **Invoke-Sqlcmd**.  
  
1.  **Before you begin:**  [Permissions](#Permissions)  
  
2.  **To set authentication, using:**  [A Virtual Drive](#SQLAuthVirtDrv), [Invoke-Sqlcmd](#SQLAuthInvSqlCmd)  
  
##  <a name="Permissions"></a> Autorizzazioni  
 Tutte le azioni eseguibili in un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] vengono controllate dalle autorizzazioni concesse alle credenziali di autenticazione utilizzate per connettersi all'istanza. Per impostazione predefinita, il provider e i cmdlet di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzano l'account di Windows in esecuzione per eseguire una connessione con autenticazione di Windows al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 Per effettuare una connessione con autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è necessario fornire un ID di accesso per l'autenticazione di SQL Server e una password. Se si usa il provider di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , è necessario associare le credenziali di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a un'unità virtuale e quindi usare il comando di modifica della directory (**cd**) per stabilire la connessione a tale unità. In Windows PowerShell le credenziali di sicurezza possono essere associate solo a unità virtuali.  
  
##  <a name="SQLAuthVirtDrv"></a> Autenticazione di SQL Server tramite un'unità virtuale  
 **Per creare un'unità virtuale associata a un accesso di autenticazione di SQL Server**  
  
1.  Creare una funzione che:  
  
    1.  Disponga di parametri per il nome da assegnare all'unità virtuale, l'ID di accesso e il percorso del provider da associare all'unità virtuale.  
  
    2.  Usi **read-host** per richiedere all'utente la password.  
  
    3.  Usi **new-object** per creare un oggetto credenziali.  
  
    4.  Usi **new-psdrive** per creare un'unità virtuale con le credenziali fornite.  
  
2.  Richiamare la funzione per creare un'unità virtuale con le credenziali fornite.  
  
### <a name="example-virtual-drive"></a>Esempio (unità virtuale)  
 In questo esempio viene creata una funzione denominata **sqldrive** che può essere utilizzata per creare un'unità virtuale associata all'account di accesso con autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e all'istanza specificati.  
  
 La funzione **sqldrive** richiede di immettere la password per effettuare l'accesso, mascherandola durante la digitazione. Quando si usa il comando di modifica della directory (**cd**) per connettersi a un percorso usando il nome di unità virtuale, tutte le operazioni vengono eseguite usando le credenziali di accesso con autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fornite al momento della creazione dell'unità.  
  
```  
## Create a function that specifies the login and prompts for the password.  
  
function sqldrive  
{  
    param( [string]$name, [string]$login = "MyLogin", [string]$root = "SQLSERVER:\SQL\MyComputer\MyInstance" )  
    $pwd = read-host -AsSecureString -Prompt "Password"  
    $cred = new-object System.Management.Automation.PSCredential -argumentlist $login,$pwd  
    New-PSDrive $name -PSProvider SqlServer -Root $root -Credential $cred -Scope 1  
}  
  
## Use the sqldrive function to create a SQLAuth virtual drive.  
sqldrive SQLAuth  
  
## CD to the virtual drive, which invokes the supplied authentication credentials.  
cd SQLAuth  
```  
  
##  <a name="SQLAuthInvSqlCmd"></a> Autenticazione di SQL Server tramite Invoke-Sqlcmd  
 **Per utilizzare Invoke-Sqlcmd con l'autenticazione di SQL Server**  
  
1.  Utilizzare il parametro **–Username** per specificare un ID di accesso e il parametro **–Password** per specificare la password associata.  
  
### <a name="example-invoke-sqlcmd"></a>Esempio (Invoke-Sqlcmd)  
 In questo esempio viene utilizzato l'host della lettura cmdlet per la richiesta di una password all'utente, quindi viene stabilita la connessione tramite l'autenticazione di SQL Server.  
  
```  
## Prompt the user for their password.  
$pwd = read-host -AsSecureString -Prompt "Password"  
  
Invoke-Sqlcmd -Query "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance "MyComputer\MyInstance" –Username “MyLogin” –Password $pwd  
```  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)   
 [Provider PowerShell per SQL Server](../../relational-databases/scripting/sql-server-powershell-provider.md)   
 [Cmdlet Invoke-Sqlcmd](../../powershell/invoke-sqlcmd-cmdlet.md)  
  
  
