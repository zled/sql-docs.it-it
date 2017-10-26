---
title: "Aggiunta di attività flusso di dati a livello di codice | Documenti Microsoft"
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
- adding Data Flow task
- SSIS data flow
- data flow task [Integration Services], adding
- MainPipe object
ms.assetid: 0ca03712-a82e-4aa7-949b-f869a8936ddf
caps.latest.revision: 48
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 0a7b0c3e51d7df76689f16ed91f60972d171bd9a
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="adding-the-data-flow-task-programmatically"></a>Aggiunta dell'attività Flusso di dati a livello di programmazione
  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] è inclusa l'attività Flusso di dati, rappresentata dallo spazio dei nomi <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper> del modello a oggetti. Flusso di dati è un'attività speciale, a elevate prestazioni, dedicata alla trasformazione e allo spostamento dei dati durante l'esecuzione del pacchetto. Analogamente ad altre attività, Flusso di dati è inclusa nell'oggetto <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> e dal punto di vista del motore di run-time è solo un'altra attività del pacchetto. Tuttavia, il flusso di dati contiene oggetti aggiuntivi denominati componenti del flusso di dati. Si tratta dei componenti che consentono lo spostamento dei dati da un'origine a una destinazione, a volte tramite una trasformazione. Tali componenti definiscono sia la direzione dello spostamento che la modalità di trasformazione dei dati. La configurazione dell'attività Flusso di dati implica l'aggiunta di componenti e quindi la relativa connessione per stabilire il flusso dei dati e ottenere la trasformazione desiderata.  
  
 Esistono tre tipi di componenti all'interno di un'attività flusso di dati: **origini flusso di dati**, **trasformazioni flusso di dati**, e **destinazioni flusso di dati**, come illustrato in questo ordine nella il [!INCLUDE[ssIS](../../includes/ssis-md.md)] della casella degli strumenti di progettazione. Questi tipi vengono anche definiti più semplicemente come origini, trasformazioni o destinazioni. Come implicano i nomi, i dati vengono spostati da un'origine a una trasformazione e quindi a una destinazione. Si tratta di una descrizione semplicistica del flusso di dati per illustrare il concetto, ma l'attività Flusso di dati è sufficientemente flessibile e potente da gestire più origini e da connettere molte trasformazioni che inviano l'output a molte destinazioni.  
  
 L'attività Flusso di dati viene aggiunta in un pacchetto allo stesso modo delle altre attività. Una volta aggiunta, l'attività viene configurata con l'aggiunta, la configurazione e la connessione dei relativi componenti.  
  
## <a name="sample"></a>Esempio  
 Nell'esempio di codice seguente viene illustrato come aggiungere un'attività Flusso di dati in un pacchetto. L'esempio richiede un riferimento agli assembly Microsoft.SqlServer.PipelineHost, Microsoft.SqlServer.DTSPipelineWrap e Microsoft.SqlServer.ManagedDTS.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package p = new Package();  
      Executable e = p.Executables.Add("STOCK:PipelineTask");  
      TaskHost thMainPipe = e as TaskHost;  
      MainPipe dataFlowTask = thMainPipe.InnerObject as MainPipe;   
    }  
  }  
}  
```  
  
```vb  
Imports System.IO  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
Module Module1  
  
  Sub Main()  
  
    Dim p As Package = New Package()  
    Dim e As Executable = p.Executables.Add("STOCK:PipelineTask")  
    Dim thMainPipe As TaskHost = CType(e, TaskHost)  
    Dim dataFlowTask As MainPipe = CType(thMainPipe.InnerObject, MainPipe)  
  
  End Sub  
  
End Module  
```  
  
## <a name="external-resources"></a>Risorse esterne  
 Post di blog, [Ezapi per SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=243223), su blogs.msdn.com.  
  
## <a name="see-also"></a>Vedere anche  
 [Individuazione dei componenti del flusso di dati a livello di programmazione](../../integration-services/building-packages-programmatically/discovering-data-flow-components-programmatically.md)  
  
  

