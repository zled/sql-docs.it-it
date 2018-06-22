---
title: Configurazione di SQL Server in SMO | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server, configuring
- configuration options [SMO]
ms.assetid: 0a372643-15cb-45a7-8665-04f1215df8ed
caps.latest.revision: 40
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 56220abf90214d83715baeb706406c375374b681
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069792"
---
# <a name="configuring-sql-server-in-smo"></a>Configurazione di SQL Server in SMO
  In SMO, il <xref:Microsoft.SqlServer.Management.Smo.Information> oggetto, il <xref:Microsoft.SqlServer.Management.Smo.Settings> oggetto, la <xref:Microsoft.SqlServer.Management.Smo.UserOptions> oggetto e il <xref:Microsoft.SqlServer.Management.Smo.Configuration> oggetto contiene le impostazioni e informazioni per l'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sono disponibili varie proprietà tramite cui viene descritto il comportamento dell'istanza installata. Le proprietà consentono di descrivere opzioni di avvio, impostazioni predefinite del server, file e directory, informazioni sul sistema e sul processore, prodotto e versioni, informazioni di connessione, opzioni per la memoria, selezioni relative a lingua e regole di confronto e modalità di autenticazione.  
  
## <a name="sql-server-configuration"></a>Configurazione di SQL Server  
 Il <xref:Microsoft.SqlServer.Management.Smo.Information> le proprietà dell'oggetto contengono informazioni sull'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], ad esempio processore e piattaforma.  
  
 Il <xref:Microsoft.SqlServer.Management.Smo.Settings> le proprietà dell'oggetto contengono informazioni sull'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Oltre al profilo di posta e all'account del server, è possibile modificare il file e la directory di database predefiniti. Queste proprietà rimangono valide per la durata della connessione.  
  
 Le proprietà dell'oggetto <xref:Microsoft.SqlServer.Management.Smo.UserOptions> contengono informazioni sul comportamento delle connessioni correnti in relazione ad aritmetica, standard ANSI e transazioni.  
  
 È anche un set di opzioni di configurazione che è rappresentato dal <xref:Microsoft.SqlServer.Management.Smo.Configuration> oggetto. Contiene un set di proprietà che rappresentano le opzioni che possono essere modificate dalla stored procedure `sp_configure`. Impostazione di opzioni, ad esempio **Priority Boost**, **Recovery Interval** e **Network Packet Size**controllano le prestazioni dell'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Molte di queste opzioni possono essere modificate dinamicamente, ma in alcuni casi il valore viene prima configurato, quindi modificato al riavvio dell'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 È presente un <xref:Microsoft.SqlServer.Management.Smo.Configuration> proprietà per ogni opzione di configurazione dell'oggetto. È possibile modificare l'impostazione di configurazione globale utilizzando l'oggetto <xref:Microsoft.SqlServer.Management.Smo.ConfigProperty>. Molte proprietà hanno valori massimi e minimi, anch'essi archiviati come proprietà <xref:Microsoft.SqlServer.Management.Smo.ConfigProperty>. Queste proprietà richiedono il <xref:Microsoft.SqlServer.Management.Smo.ConfigurationBase.Alter%2A> per eseguire il commit della modifica all'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Tutte le opzioni di configurazione della <xref:Microsoft.SqlServer.Management.Smo.Configuration> devono essere modificate dall'amministratore di sistema.  
  
## <a name="examples"></a>Esempi  
 Per gli esempi di codice seguenti, è necessario selezionare l'ambiente, il modello e il linguaggio di programmazione per la creazione dell'applicazione. Per altre informazioni, vedere [creare un progetto di Visual Basic SMO in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) e [creare un Visual C&#35; progetto SMO in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="modifying-sql-server-configuration-options-in-visual-basic"></a>Modifica delle opzioni di configurazione di SQL Server in Visual Basic  
 Nell'esempio di codice viene illustrato come aggiornare un'opzione di configurazione in Visual Basic .NET. Vengono inoltre recuperate e visualizzate informazioni relative ai valori massimi e minimi per l'opzione di configurazione specificata. Infine, viene segnalato all'utente se la modifica è stata apportata dinamicamente o se vengono archiviato finché l'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] viene riavviato.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBConfigure2](SMO How to#SMO_VBConfigure2)]  -->  
  
## <a name="modifying-sql-server-settings-in-visual-basic"></a>Modifica delle impostazioni di SQL Server in Visual Basic  
 Nell'esempio di codice vengono visualizzate informazioni relative all'istanza del [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in <xref:Microsoft.SqlServer.Management.Smo.Information> e <xref:Microsoft.SqlServer.Management.Smo.Settings>e modificate le impostazioni nelle <xref:Microsoft.SqlServer.Management.Smo.Settings> e <xref:Microsoft.SqlServer.Management.Smo.UserOptions>le proprietà dell'oggetto.  
  
 Nell'esempio l'oggetto <xref:Microsoft.SqlServer.Management.Smo.UserOptions> e l'oggetto <xref:Microsoft.SqlServer.Management.Smo.Settings> hanno entrambi un metodo <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A>. È possibile eseguire il <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> metodi per questi singolarmente.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBConfigure1](SMO How to#SMO_VBConfigure1)]  -->  
  
## <a name="modifying-sql-server-settings-in-visual-c"></a>Modifica delle impostazioni di SQL Server in Visual C#  
 Nell'esempio di codice vengono visualizzate informazioni relative all'istanza del [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in <xref:Microsoft.SqlServer.Management.Smo.Information> e <xref:Microsoft.SqlServer.Management.Smo.Settings>e modificate le impostazioni nelle <xref:Microsoft.SqlServer.Management.Smo.Settings> e <xref:Microsoft.SqlServer.Management.Smo.UserOptions>le proprietà dell'oggetto.  
  
 Nell'esempio l'oggetto <xref:Microsoft.SqlServer.Management.Smo.UserOptions> e l'oggetto <xref:Microsoft.SqlServer.Management.Smo.Settings> hanno entrambi un metodo <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A>. È possibile eseguire il <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> metodi per questi singolarmente.  
  
 `//Connect to the local, default instance of SQL Server.`  
  
```  
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
 Nell'esempio di codice vengono visualizzate informazioni relative all'istanza del [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in <xref:Microsoft.SqlServer.Management.Smo.Information> e <xref:Microsoft.SqlServer.Management.Smo.Settings>e modificate le impostazioni nelle <xref:Microsoft.SqlServer.Management.Smo.Settings> e <xref:Microsoft.SqlServer.Management.Smo.UserOptions>le proprietà dell'oggetto.  
  
 Nell'esempio l'oggetto <xref:Microsoft.SqlServer.Management.Smo.UserOptions> e l'oggetto <xref:Microsoft.SqlServer.Management.Smo.Settings> hanno entrambi un metodo <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A>. È possibile eseguire il <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> metodi per questi singolarmente.  
  
```  
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
 Nell'esempio di codice viene illustrato come aggiornare un'opzione di configurazione in Visual Basic .NET. Vengono inoltre recuperate e visualizzate informazioni relative ai valori massimi e minimi per l'opzione di configurazione specificata. Infine, viene segnalato all'utente se la modifica è stata apportata dinamicamente o se vengono archiviato finché l'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] viene riavviato.  
  
```  
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
  
  