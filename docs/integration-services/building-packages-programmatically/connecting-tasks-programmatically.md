---
title: "Connessione di attività a livello di codice | Documenti Microsoft"
ms.custom: 
ms.date: 03/04/2017
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
- tasks [Integration Services], precedence constraints
- precedence constraints [Integration Services], connecting tasks
- constraints [Integration Services]
ms.assetid: 23668e88-cef4-4009-a9cf-38e607eab7a2
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: 27be63f22fda13f0959f28c4ee36cc2b12c66058
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="connecting-tasks-programmatically"></a>Connessione di attività a livello di programmazione
  Un vincolo di precedenza, rappresentato nel modello a oggetti dalla classe <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>, stabilisce l'ordine di esecuzione degli oggetti <xref:Microsoft.SqlServer.Dts.Runtime.Executable> in un pacchetto. Con il vincolo di precedenza, l'esecuzione dei contenitori e delle attività di un pacchetto diventa dipendente dal risultato dell'esecuzione di un'attività o di un contenitore precedente. I vincoli di precedenza vengono stabiliti tra coppie di oggetti <xref:Microsoft.SqlServer.Dts.Runtime.Executable> chiamando il metodo <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraints.Add%2A> della raccolta <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraints> sull'oggetto contenitore. Dopo aver creato un vincolo tra due oggetti eseguibili, impostare la proprietà <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> per stabilire i criteri per l'esecuzione del secondo eseguibile definito nel vincolo.  
  
 È possibile utilizzare sia un vincolo che un'espressione in un singolo vincolo di precedenza, a seconda del valore specificato per la proprietà <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.EvalOp%2A>, come descritto nella tabella seguente:  
  
|Valore della proprietà EvalOp|Description|  
|----------------------------------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DTSPrecedenceEvalOp.Constraint>|Specifica che il risultato dell'esecuzione determina se l'attività o il contenitore vincolato viene eseguito. Impostare la proprietà <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> di <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> sul valore desiderato dell'enumerazione <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult>.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DTSPrecedenceEvalOp.Expression>|Specifica che il valore di un'espressione determina se l'attività o il contenitore vincolato viene eseguito. Impostare la proprietà <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A> di <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DTSPrecedenceEvalOp.ExpressionAndConstraint>|Specifica che, affinché l'attività o il contenitore vincolato venga eseguito, è necessario che il risultato del vincolo si verifichi e che l'espressione restituisca un valore. Impostare sia il <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> e <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A> le proprietà del <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>e impostare relativo <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.LogicalAnd%2A> proprietà **true**.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DTSPrecedenceEvalOp.ExpressionOrConstraint>|Specifica che, affinché l'attività o il contenitore vincolato venga eseguito, è necessario che il risultato del vincolo si verifichi oppure che l'espressione restituisca un valore. Impostare sia il <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> e <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A> le proprietà del <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>e impostare relativo <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.LogicalAnd%2A> proprietà **false**.|  
  
 Nell'esempio di codice seguente è illustrata l'aggiunta di due attività a un pacchetto. Tra le attività viene creato <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> che impedisce l'esecuzione della seconda attività finché non viene completata la prima.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package p = new Package();  
  
      // Add a File System task.  
      Executable eFileTask1 = p.Executables.Add("STOCK:FileSystemTask");  
      TaskHost thFileHost1 = eFileTask1 as TaskHost;  
  
      // Add a second File System task.  
      Executable eFileTask2 = p.Executables.Add("STOCK:FileSystemTask");  
      TaskHost thFileHost2 = eFileTask2 as TaskHost;  
  
      // Put a precedence constraint between the tasks.  
      // Set the constraint to specify that the second File System task cannot run  
      // until the first File System task finishes.  
      PrecedenceConstraint pcFileTasks =   
        p.PrecedenceConstraints.Add((Executable)thFileHost1, (Executable)thFileHost2);  
      pcFileTasks.Value = DTSExecResult.Completion;  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim p As Package = New Package()  
    ' Add a File System task.  
    Dim eFileTask1 As Executable = p.Executables.Add("STOCK:FileSystemTask")  
    Dim thFileHost1 As TaskHost = CType(eFileTask1, TaskHost)  
  
    ' Add a second File System task.  
    Dim eFileTask2 As Executable = p.Executables.Add("STOCK:FileSystemTask")  
    Dim thFileHost2 As TaskHost = CType(eFileTask2, TaskHost)  
  
    ' Put a precedence constraint between the tasks.  
    ' Set the constraint to specify that the second File System task cannot run  
    ' until the first File System task finishes.  
    Dim pcFileTasks As PrecedenceConstraint = _  
      p.PrecedenceConstraints.Add(CType(thFileHost1, Executable), CType(thFileHost2, Executable))  
    pcFileTasks.Value = DTSExecResult.Completion  
  
  End Sub  
  
End Module  
```
  
## <a name="see-also"></a>Vedere anche  
 [Aggiunta di attività flusso di dati a livello di codice](../../integration-services/building-packages-programmatically/adding-the-data-flow-task-programmatically.md)  
  
  
