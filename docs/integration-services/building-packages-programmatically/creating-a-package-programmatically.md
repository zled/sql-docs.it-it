---
title: Creazione di un pacchetto a livello di codice | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SSIS packages, creating
- Integration Services packages, creating
- packages [Integration Services], creating
- SQL Server Integration Services packages, creating
ms.assetid: e44bcc70-32d3-43e8-a84b-29aef819d5d3
caps.latest.revision: 51
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: 58a8201d68cb6d942bd98ca3c53b6cf98336284e
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="creating-a-package-programmatically"></a>Creazione di un pacchetto a livello di programmazione
  L'oggetto <xref:Microsoft.SqlServer.Dts.Runtime.Package> rappresenta il contenitore di livello principale per tutti gli altri oggetti di una soluzione di progetto di [!INCLUDE[ssIS](../../includes/ssis-md.md)]. Essendo il contenitore di livello principale, il pacchetto è il primo oggetto creato. Gli oggetti successivi vengono aggiunti e quindi eseguiti nel contesto del pacchetto. Il pacchetto non sposta né trasforma dati, ma si basa sulle attività che contiene per eseguire questa operazione. Le attività eseguono la maggior parte delle operazioni del pacchetto e ne definiscono la funzionalità. Per creare un pacchetto sono sufficienti tre righe di codice, ma vengono aggiunti vari oggetti <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> e attività per fornire funzionalità aggiuntive. In questa sezione viene descritto come creare un pacchetto a livello di programmazione. Non vengono fornite informazioni sulla creazione di attività o di oggetti <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>, che verranno descritti nelle sezioni successive.  
  
## <a name="example"></a>Esempio  
 Per scrivere codice utilizzando l'IDE di Visual Studio, è necessario un riferimento a Microsoft.SqlServer.ManagedDTS.dll per creare un'istruzione `using` (`Imports` in Visual Basic .NET) in Microsoft.SqlServer.Dts.Runtime. Nell'esempio di codice seguente è illustrata la creazione di un pacchetto vuoto.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package package;  
      package = new Package();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim package As Package  
    package = New Package  
  
  End Sub  
  
End Module  
```  
  
 Per compilare ed eseguire l'esempio, premere F5 in Visual Studio. Per compilare il codice utilizzando il compilatore c#, **csc.exe**, al prompt dei comandi per la compilazione, utilizzare il comando seguente e i riferimenti, la sostituzione di file di  *\<filename >* con il nome del file con estensione cs o vb e assegnando un  *\<outputfilename >* di propria scelta.  
  
 **csc /target: library /out: \<outputfilename > DLL \<filename >. cs /r:Microsoft.SqlServer.Managed DTS "System.dll**  
  
 Per compilare il codice utilizzando il compilatore Visual Basic .NET, **vbc.exe**, al prompt dei comandi per la compilazione, utilizzare il comando seguente e i riferimenti di file.  
  
 **/target: library vbc /out: \<outputfilename > DLL \<filename > VB /r:Microsoft.SqlServer.Managed DTS "System.dll**  
  
 È anche possibile creare un pacchetto caricando un pacchetto esistente salvato su disco, nel file system o in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La differenza è che il <xref:Microsoft.SqlServer.Dts.Runtime.Application> oggetto viene prima creato e quindi l'oggetto pacchetto viene inserito uno dei metodi di overload dell'applicazione: **LoadPackage** per file flat, **LoadFromSQLServer** per i pacchetti salvati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], o <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromDtsServer%2A> per i pacchetti salvati nel file System. Nell'esempio seguente viene caricato un pacchetto esistente da disco, quindi vengono visualizzate diverse proprietà del pacchetto.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class ApplicationTests  
  {  
    static void Main(string[] args)  
    {  
      // The variable pkg points to the location of the  
      // ExecuteProcess package sample that was installed with  
      // the SSIS samples.  
      string pkg = @"C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" +  
        @"\Package Samples\ExecuteProcess Sample\ExecuteProcess\UsingExecuteProcess.dtsx";  
  
      Application app = new Application();  
      Package p = app.LoadPackage(pkg, null);  
  
      // Now that the package is loaded, we can query on  
      // its properties.  
      int n = p.Configurations.Count;  
      DtsProperty p2 = p.Properties["VersionGUID"];  
      DTSProtectionLevel pl = p.ProtectionLevel;  
  
      Console.WriteLine("Number of configurations = " + n.ToString());  
      Console.WriteLine("VersionGUID = " + (string)p2.GetValue(p));  
      Console.WriteLine("ProtectionLevel = " + pl.ToString());  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module ApplicationTests  
  
  Sub Main()  
  
    ' The variable pkg points to the location of the  
    ' ExecuteProcess package sample that was installed with  
    ' the SSIS samples.  
    Dim pkg As String = _  
      "C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" & _  
      "\Package Samples\ExecuteProcess Sample\ExecuteProcess\UsingExecuteProcess.dtsx"  
  
    Dim app As Application = New Application()  
    Dim p As Package = app.LoadPackage(pkg, Nothing)  
  
    ' Now that the package is loaded, we can query on  
    ' its properties.  
    Dim n As Integer = p.Configurations.Count  
    Dim p2 As DtsProperty = p.Properties("VersionGUID")  
    Dim pl As DTSProtectionLevel = p.ProtectionLevel  
  
    Console.WriteLine("Number of configurations = " & n.ToString())  
    Console.WriteLine("VersionGUID = " & CType(p2.GetValue(p), String))  
    Console.WriteLine("ProtectionLevel = " & pl.ToString())  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
 **Esempio di Output:**  
  
 `Number of configurations = 2`  
  
 `VersionGUID = {09016682-89B8-4406-AAC9-AF1E527FF50F}`  
  
 `ProtectionLevel = DontSaveSensitive`  
  
## <a name="external-resources"></a>Risorse esterne  
  
-   Post di blog, [esempio API - origine e destinazione OLE DB](http://go.microsoft.com/fwlink/?LinkId=220824), su blogs.msdn.com.  
  
-   Post di blog, [Ezapi per SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=243223), su blogs.msdn.com.  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiunta di attività a livello di codice](../../integration-services/building-packages-programmatically/adding-tasks-programmatically.md)  
  
  
