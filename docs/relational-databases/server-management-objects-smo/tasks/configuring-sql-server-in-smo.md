---
title: Configurazione di SQL Server in SMO | Documenti Microsoft
ms.custom: 
ms.date: 08/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server, configuring
- configuration options [SMO]
ms.assetid: 0a372643-15cb-45a7-8665-04f1215df8ed
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f64bb51a733898d89f4c1cd67c2615fce6266a69
ms.sourcegitcommit: cb2f9d4db45bef37c04064a9493ac2c1d60f2c22
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/12/2018
---
# <a name="configuring-sql-server-in-smo"></a>Configurazione di SQL Server in SMO
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  In SMO la <xref:Microsoft.SqlServer.Management.Smo.Information> oggetto, il <xref:Microsoft.SqlServer.Management.Smo.Settings> oggetto, il <xref:Microsoft.SqlServer.Management.Smo.UserOptions> oggetto e <xref:Microsoft.SqlServer.Management.Smo.Configuration> oggetto contiene le impostazioni e informazioni per l'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sono disponibili varie proprietà tramite cui viene descritto il comportamento dell'istanza installata. Le proprietà consentono di descrivere opzioni di avvio, impostazioni predefinite del server, file e directory, informazioni sul sistema e sul processore, prodotto e versioni, informazioni di connessione, opzioni per la memoria, selezioni relative a lingua e regole di confronto e modalità di autenticazione.  
  
## <a name="sql-server-configuration"></a>Configurazione di SQL Server  
 Il <xref:Microsoft.SqlServer.Management.Smo.Information> le proprietà dell'oggetto contengono informazioni sull'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], ad esempio processore e piattaforma.  
  
 Il <xref:Microsoft.SqlServer.Management.Smo.Settings> le proprietà dell'oggetto contengono informazioni sull'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Oltre al profilo di posta e all'account del server, è possibile modificare il file e la directory di database predefiniti. Queste proprietà rimangono valide per la durata della connessione.  
  
 Le proprietà dell'oggetto <xref:Microsoft.SqlServer.Management.Smo.UserOptions> contengono informazioni sul comportamento delle connessioni correnti in relazione ad aritmetica, standard ANSI e transazioni.  
  
 È anche un set di opzioni di configurazione che è rappresentato dal <xref:Microsoft.SqlServer.Management.Smo.Configuration> oggetto. Contiene un set di proprietà che rappresentano le opzioni che possono essere modificate dalla stored procedure **sp_configure** . Opzioni, ad esempio **Priority Boost**, **Recovery Interval** e **Network Packet Size**controllano le prestazioni dell'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Molte di queste opzioni possono essere modificate dinamicamente, ma in alcuni casi il valore viene prima configurato, quindi modificato al riavvio dell'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 È presente un <xref:Microsoft.SqlServer.Management.Smo.Configuration> proprietà per ogni opzione di configurazione dell'oggetto. È possibile modificare l'impostazione di configurazione globale utilizzando l'oggetto <xref:Microsoft.SqlServer.Management.Smo.ConfigProperty>. Molte proprietà hanno valori massimi e minimi, anch'essi archiviati come proprietà <xref:Microsoft.SqlServer.Management.Smo.ConfigProperty>. Queste proprietà richiedono il <xref:Microsoft.SqlServer.Management.Smo.ConfigurationBase.Alter%2A> per eseguire il commit della modifica all'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Tutte le opzioni di configurazione della <xref:Microsoft.SqlServer.Management.Smo.Configuration> devono essere modificate dall'amministratore di sistema.  
  
## <a name="examples"></a>Esempi  
 Per gli esempi di codice seguenti, è necessario selezionare l'ambiente, il modello e il linguaggio di programmazione per la creazione dell'applicazione. Per ulteriori informazioni, vedere [crea un Visual C &#35; Progetto SMO in Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="modifying-sql-server-configuration-options-in-visual-basic"></a>Modifica delle opzioni di configurazione di SQL Server in Visual Basic  
 Nell'esempio di codice viene illustrato come aggiornare un'opzione di configurazione in Visual Basic .NET. Vengono inoltre recuperate e visualizzate informazioni relative ai valori massimi e minimi per l'opzione di configurazione specificata. Infine, viene segnalato all'utente se la modifica è stata apportata dinamicamente o se è stata archiviata fino a quando l'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] viene riavviato.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Display all the configuration options.
Dim p As ConfigProperty
For Each p In srv.Configuration.Properties
    Console.WriteLine(p.DisplayName)
Next
Console.WriteLine("There are " & srv.Configuration.Properties.Count.ToString & " configuration options.")
'Display the maximum and minimum values for ShowAdvancedOptions.
Dim min As Integer
Dim max As Integer
min = srv.Configuration.ShowAdvancedOptions.Minimum
max = srv.Configuration.ShowAdvancedOptions.Maximum
Console.WriteLine("Minimum and Maximum values are " & min & " and " & max & ".")
'Modify the value of ShowAdvancedOptions and run the Alter method.
srv.Configuration.ShowAdvancedOptions.ConfigValue = 0
srv.Configuration.Alter()
'Display when the change takes place according to the IsDynamic property.
If srv.Configuration.ShowAdvancedOptions.IsDynamic = True Then
    Console.WriteLine("Configuration option has been updated.")
Else
    Console.WriteLine("Configuration option will be updated when SQL Server is restarted.")
End If
``` 
  
## <a name="modifying-sql-server-settings-in-visual-basic"></a>Modifica delle impostazioni di SQL Server in Visual Basic  
 L'esempio di codice consente di visualizzare informazioni sull'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in <xref:Microsoft.SqlServer.Management.Smo.Information> e <xref:Microsoft.SqlServer.Management.Smo.Settings>e modifica le impostazioni di <xref:Microsoft.SqlServer.Management.Smo.Settings> e <xref:Microsoft.SqlServer.Management.Smo.UserOptions>le proprietà dell'oggetto.  
  
 Nell'esempio l'oggetto <xref:Microsoft.SqlServer.Management.Smo.UserOptions> e l'oggetto <xref:Microsoft.SqlServer.Management.Smo.Settings> hanno entrambi un metodo <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A>. È possibile eseguire il <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> metodi per questi singolarmente.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Display information about the instance of SQL Server in Information and Settings.
Console.WriteLine("OS Version = " & srv.Information.OSVersion)
Console.WriteLine("State = " & srv.Settings.State.ToString)
'Display information specific to the current user in UserOptions.
Console.WriteLine("Quoted Identifier support = " & srv.UserOptions.QuotedIdentifier)
'Modify server settings in Settings.

srv.Settings.LoginMode = ServerLoginMode.Integrated
'Modify settings specific to the current connection in UserOptions.
srv.UserOptions.AbortOnArithmeticErrors = True
'Run the Alter method to make the changes on the instance of SQL Server.
srv.Alter()
```
  
## <a name="modifying-sql-server-settings-in-visual-c"></a>Modifica delle impostazioni di SQL Server in Visual C#  
 L'esempio di codice consente di visualizzare informazioni sull'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in <xref:Microsoft.SqlServer.Management.Smo.Information> e <xref:Microsoft.SqlServer.Management.Smo.Settings>e modifica le impostazioni di <xref:Microsoft.SqlServer.Management.Smo.Settings> e <xref:Microsoft.SqlServer.Management.Smo.UserOptions>le proprietà dell'oggetto.  
  
 Nell'esempio l'oggetto <xref:Microsoft.SqlServer.Management.Smo.UserOptions> e l'oggetto <xref:Microsoft.SqlServer.Management.Smo.Settings> hanno entrambi un metodo <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A>. È possibile eseguire il <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> metodi per questi singolarmente.  
  
 `//Connect to the local, default instance of SQL Server.`  
  
```csharp  
{  
            Server srv = new Server();  
            //Display all the configuration options.   
  
            foreach (ConfigProperty p in srv.Configuration.Properties)  
            {  
                Console.WriteLine(p.DisplayName);  
            }  
            Console.WriteLine("There are " + srv.Configuration.Properties.Count.ToString() + " configuration options.");  
            //Display the maximum and minimum values for ShowAdvancedOptions.   
            int min = 0;  
            int max = 0;  
            min = srv.Configuration.ShowAdvancedOptions.Minimum;  
            max = srv.Configuration.ShowAdvancedOptions.Maximum;  
            Console.WriteLine("Minimum and Maximum values are " + min + " and " + max + ".");  
            //Modify the value of ShowAdvancedOptions and run the Alter method.   
            srv.Configuration.ShowAdvancedOptions.ConfigValue = 0;  
            srv.Configuration.Alter();  
            //Display when the change takes place according to the IsDynamic property.   
            if (srv.Configuration.ShowAdvancedOptions.IsDynamic == true)  
            {  
                Console.WriteLine("Configuration option has been updated.");  
            }  
            else  
            {  
                Console.WriteLine("Configuration option will be updated when SQL Server is restarted.");  
            }  
        }  
```  
  
## <a name="modifying-sql-server-settings-in-powershell"></a>Modifica delle impostazioni di SQL Server in PowerShell  
 L'esempio di codice consente di visualizzare informazioni sull'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in <xref:Microsoft.SqlServer.Management.Smo.Information> e <xref:Microsoft.SqlServer.Management.Smo.Settings>e modifica le impostazioni di <xref:Microsoft.SqlServer.Management.Smo.Settings> e <xref:Microsoft.SqlServer.Management.Smo.UserOptions>le proprietà dell'oggetto.  
  
 Nell'esempio l'oggetto <xref:Microsoft.SqlServer.Management.Smo.UserOptions> e l'oggetto <xref:Microsoft.SqlServer.Management.Smo.Settings> hanno entrambi un metodo <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A>. È possibile eseguire il <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> metodi per questi singolarmente.  
  
```powershell 
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\  
$srv = get-item default  
  
#Display information about the instance of SQL Server in Information and Settings.  
"OS Version = " + $srv.Information.OSVersion  
"State = "+ $srv.Settings.State.ToString()  
  
#Display information specific to the current user in UserOptions.  
"Quoted Identifier support = " + $srv.UserOptions.QuotedIdentifier  
  
#Modify server settings in Settings.  
$srv.Settings.LoginMode = [Microsoft.SqlServer.Management.SMO.ServerLoginMode]::Integrated  
  
#Modify settings specific to the current connection in UserOptions.  
$srv.UserOptions.AbortOnArithmeticErrors = $true  
  
#Run the Alter method to make the changes on the instance of SQL Server.  
$srv.Alter()  
```  
  
## <a name="modifying-sql-server-configuration-options-in-powershell"></a>Modifica delle opzioni di configurazione di SQL Server in PowerShell  
 Nell'esempio di codice viene illustrato come aggiornare un'opzione di configurazione in Visual Basic .NET. Vengono inoltre recuperate e visualizzate informazioni relative ai valori massimi e minimi per l'opzione di configurazione specificata. Infine, viene segnalato all'utente se la modifica è stata apportata dinamicamente o se è stata archiviata fino a quando l'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] viene riavviato.  
  
```powershell 
#Get a server object which corresponds to the default instance replace LocalMachine with the physical server  
cd \sql\LocalMachine  
$svr = get-item default  
  
#enumerate its properties  
foreach ($Item in $Svr.Configuration.Properties)   
{  
 $Item.DisplayName  
}  
  
"There are " + $svr.Configuration.Properties.Count.ToString() + " configuration options."  
  
#Display the maximum and minimum values for ShowAdvancedOptions.  
$min = $svr.Configuration.ShowAdvancedOptions.Minimum  
$max = $svr.Configuration.ShowAdvancedOptions.Maximum  
"Minimum and Maximum values are " + $min.ToString() + " and " + $max.ToString() + "."  
  
#Modify the value of ShowAdvancedOptions and run the Alter method.  
$svr.Configuration.ShowAdvancedOptions.ConfigValue = 0  
$svr.Configuration.Alter()  
  
#Display when the change takes place according to the IsDynamic property.  
If ($svr.Configuration.ShowAdvancedOptions.IsDynamic -eq $true)  
 {    
   "Configuration option has been updated."  
 }  
Else  
{  
    "Configuration option will be updated when SQL Server is restarted."  
}  
```  
  
  
