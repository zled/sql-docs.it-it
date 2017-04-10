---
title: "Caricare gli assembly SMO in Windows PowerShell | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8ca42b69-da5a-47f4-9085-34e443f0e389
caps.latest.revision: 9
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 9
---
# Caricare gli assembly SMO in Windows PowerShell
  In questo argomento viene descritta la modalità di caricamento assembly SMO (SQL Server Management Object, SMO) negli script di Windows PowerShell che non utilizzano il provider SQL Server PowerShell.  
  
## Prima di iniziare  
 Il meccanismo preferito per il caricamento degli assembly SMO consiste nel caricare il modulo **sqlps** . Il provider [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] incluso nel modulo carica automaticamente gli assembly SMO e implementa anche le caratteristiche che estendono l'utilità degli oggetti SMO negli script di PowerShell.  Per altre informazioni, vedere [Importare il modulo SQLPS](../../relational-databases/scripting/import-the-sqlps-module.md).
  
 Nei due casi seguenti potrebbe essere necessario caricare direttamente gli assembly SMO:  
  
-   Se lo script fa riferimento a un oggetto SMO prima del primo comando che fa riferimento al provider o ai cmdlet dagli snap-in di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Se si desidera eseguire il porting del codice SMO da un altro linguaggio, ad esempio C# o Visual Basic, che non utilizza il provider o i cmdlet.  
  
## Esempio: caricamento di SQL Server Management Objects  
 Il codice seguente consente di caricare gli assembly SMO.  
  
```  
#  
# Loads the SQL Server Management Objects (SMO)  
#  
  
$ErrorActionPreference = "Stop"  
  
$sqlpsreg="HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.SqlServer.Management.PowerShell.sqlps"  
  
if (Get-ChildItem $sqlpsreg -ErrorAction "SilentlyContinue")  
{  
    throw "SQL Server Provider for Windows PowerShell is not installed."  
}  
else  
{  
    $item = Get-ItemProperty $sqlpsreg  
    $sqlpsPath = [System.IO.Path]::GetDirectoryName($item.Path)  
}  
  
$assemblylist =   
"Microsoft.SqlServer.Management.Common",  
"Microsoft.SqlServer.Smo",  
"Microsoft.SqlServer.Dmf ",  
"Microsoft.SqlServer.Instapi ",  
"Microsoft.SqlServer.SqlWmiManagement ",  
"Microsoft.SqlServer.ConnectionInfo ",  
"Microsoft.SqlServer.SmoExtended ",  
"Microsoft.SqlServer.SqlTDiagM ",  
"Microsoft.SqlServer.SString ",  
"Microsoft.SqlServer.Management.RegisteredServers ",  
"Microsoft.SqlServer.Management.Sdk.Sfc ",  
"Microsoft.SqlServer.SqlEnum ",  
"Microsoft.SqlServer.RegSvrEnum ",  
"Microsoft.SqlServer.WmiEnum ",  
"Microsoft.SqlServer.ServiceBrokerEnum ",  
"Microsoft.SqlServer.ConnectionInfoExtended ",  
"Microsoft.SqlServer.Management.Collector ",  
"Microsoft.SqlServer.Management.CollectorEnum",  
"Microsoft.SqlServer.Management.Dac",  
"Microsoft.SqlServer.Management.DacEnum",  
"Microsoft.SqlServer.Management.Utility"  
  
foreach ($asm in $assemblylist)  
{  
    $asm = [Reflection.Assembly]::LoadWithPartialName($asm)  
}  
  
Push-Location  
cd $sqlpsPath  
update-FormatData -prependpath SQLProvider.Format.ps1xml   
Pop-Location  
```  
  
## Vedere anche  
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)  
  
  