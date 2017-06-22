---
title: Accesso al Provider WMI a livello di codice | Documenti Microsoft
ms.custom: 
ms.date: 11/02/2016
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
ms.assetid: 67bd266b-1484-4863-8152-060a993420a9
caps.latest.revision: 7
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: a8608faf31e4132570de4e57e748d02057c3722d
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="accessing-the-wmi-provider-programmatically"></a>Accesso al provider WMI a livello di programmazione

## <a name="wmi-provider-overview"></a>Cenni preliminari sul provider WMI  
 Lo spazio dei nomi utilizzato per ottenere informazioni su [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] nel codice negli esempi illustrati in questo argomento è il **System. Management** dello spazio dei nomi, vedere il [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Il **System. Management** spazio dei nomi fornisce un set di classi di codice gestito tramite il quale [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] applicazioni possono accedere e modificare le informazioni di gestione. Per ulteriori informazioni sull'utilizzo di WMI per Reporting Services utilizzando le classi di **System. Management** dello spazio dei nomi, vedere la sezione "l'accesso a gestione informazioni con System. Managment nel [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK.  
  
## <a name="finding-a-report-server-instance"></a>Individuazione di un'istanza del server di report  
 Il metodo migliore per individuare le informazioni nelle installazioni del server di report consiste nell'eseguire un'enumerazione nella raccolta di istanze WMI. Nell'esempio seguente viene illustrato come individuare le proprietà in ogni istanza del server di report creando una raccolta ed eseguendo un ciclo al suo interno per visualizzare le proprietà.  
  
```vb  
Imports System  
Imports System.Management  
Imports System.IO  
  
Module Module1  
    Sub Main()  
        Const WmiNamespace As String = "\\<ServerName>\root\Microsoft\SqlServer\ReportServer\<InstanceName>\v10\Admin"  
        Const WmiRSClass As String = _  
           "\\<ServerName>\root\Microsoft\SqlServer\ReportServer\<InstanceName>\v13\admin:MSReportServer_ConfigurationSetting"  
  
        Dim serverClass As ManagementClass  
        Dim scope As ManagementScope  
        scope = New ManagementScope(WmiNamespace)  
        'Connect to the Reporting Services namespace.  
        scope.Connect()  
  
        'Create the server class.  
        serverClass = New ManagementClass(WmiRSClass)  
        'Connect to the management object.  
        serverClass.Get()  
        If serverClass Is Nothing Then Throw New Exception("No class found")  
  
        'Loop through the instances of the server class.  
        Dim instances As ManagementObjectCollection = serverClass.GetInstances()  
        Dim instance As ManagementObject  
        For Each instance In instances  
            Console.Out.WriteLine("Instance Detected")  
            Dim instProps As PropertyDataCollection = instance.Properties  
            Dim prop As PropertyData  
            For Each prop In instProps  
                Dim name As String = prop.Name  
                Dim val As Object = prop.Value  
                Console.Out.Write("Property Name: " + name)  
                If val Is Nothing Then  
                    Console.Out.WriteLine("     Value: <null>")  
                Else  
                    Console.Out.WriteLine("     Value: " + val.ToString())  
                End If  
            Next  
        Next  
  
        Console.WriteLine("--- Press any key ---")  
        Console.ReadKey()  
  
    End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Management;  
using System.IO;  
[assembly: CLSCompliant(true)]  
  
class Class1  
{  
    [STAThread]  
    static void Main(string[] args)  
    {  
        const string WmiNamespace = @"\\<ServerName>\root\Microsoft\SqlServer\ReportServer\<InstanceName>\v10\Admin";  
        const string WmiRSClass =  
          @"\\<ServerName>\root\Microsoft\SqlServer\ReportServer\<InstanceName>\v13\admin:MSReportServer_ConfigurationSetting";  
        ManagementClass serverClass;  
        ManagementScope scope;  
        scope = new ManagementScope(WmiNamespace);  
  
        // Connect to the Reporting Services namespace.  
        scope.Connect();  
        // Create the server class.  
        serverClass = new ManagementClass(WmiRSClass);  
        // Connect to the management object.  
        serverClass.Get();  
        if (serverClass == null)  
            throw new Exception("No class found");  
  
        // Loop through the instances of the server class.  
        ManagementObjectCollection instances = serverClass.GetInstances();  
  
        foreach (ManagementObject instance in instances)  
        {  
            Console.Out.WriteLine("Instance Detected");  
            PropertyDataCollection instProps = instance.Properties;  
            foreach (PropertyData prop in instProps)  
            {  
                string name = prop.Name;  
                object val = prop.Value;  
                Console.Out.Write("Property Name: " + name);  
                if (val != null)  
                    Console.Out.WriteLine("     Value: " + val.ToString());  
                else  
                    Console.Out.WriteLine("     Value: <null>");  
            }  
        }  
        Console.WriteLine("\n--- Press any key ---");  
        Console.ReadKey();  
    }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Accedere al Provider WMI di Reporting Services](../reporting-services/tools/access-the-reporting-services-wmi-provider.md)   
 [File di configurazione RsReportServer.config](../reporting-services/report-server/rsreportserver-config-configuration-file.md)  
  
  

