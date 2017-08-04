---
title: Individuazione dei componenti del flusso di dati a livello di codice | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
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
- PipelineComponentInfos collection
- data flow task [Integration Services], components
- discovering data flow components
- components [Integration Services], data flow
- data flow [Integration Services], components
ms.assetid: ff92a96a-8af6-4532-82cc-c0bbff92401b
caps.latest.revision: 44
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: 78090618d5025a6ab29c888d09db44ddfff278fa
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="discovering-data-flow-components-programmatically"></a>Individuazione dei componenti del flusso di dati a livello di programmazione
  Dopo avere aggiunto un'attività Flusso di dati a un pacchetto, il passaggio successivo consiste nel determinare quali componenti flusso di dati sono disponibili per l'utilizzo. È possibile individuare a livello di programmazione le origini, le trasformazioni e le destinazioni del flusso di dati installate e disponibili nel computer locale. Per informazioni sull'aggiunta di un'attività flusso di dati al pacchetto, vedere [aggiunta di dati flusso attività a livello di codice](../../integration-services/building-packages-programmatically/adding-the-data-flow-task-programmatically.md).  
  
## <a name="discovering-components"></a>Individuazione di componenti  
 La classe <xref:Microsoft.SqlServer.Dts.Runtime.Application> fornisce la raccolta <xref:Microsoft.SqlServer.Dts.Runtime.Application.PipelineComponentInfos%2A>, che contiene un oggetto <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo> per ogni componente installato correttamente nel computer locale. Ogni oggetto <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo> contiene informazioni su un componente, ad esempio il nome, la descrizione e il nome di creazione. È possibile utilizzare il valore restituito nella proprietà <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo.CreationName%2A> per impostare la proprietà <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> di <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> quando si aggiunge un componente a un pacchetto.  
  
## <a name="next-step"></a>Passaggio successivo  
 Dopo aver individuato i componenti disponibili, il passaggio successivo consiste per aggiungere e configurare i componenti, come descritto nell'argomento successivo: [aggiunta di dati del flusso componenti a livello di codice](../../integration-services/building-packages-programmatically/adding-data-flow-components-programmatically.md).  
  
## <a name="sample"></a>Esempio  
 Nell'esempio di codice seguente è illustrato come enumerare la raccolta <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfos> dell'oggetto <xref:Microsoft.SqlServer.Dts.Runtime.Application> per individuare a livello di programmazione i componenti del flusso di dati disponibili nel computer locale. In questo esempio richiede un riferimento all'assembly manageddts.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Application application = new Application();  
      PipelineComponentInfos componentInfos = application.PipelineComponentInfos;  
  
      foreach (PipelineComponentInfo componentInfo in componentInfos)  
      {  
        Console.WriteLine("Name: " + componentInfo.Name + "\n" +  
          " CreationName: " + componentInfo.CreationName + "\n");  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim application As Application = New Application()  
  
    Dim componentInfos As PipelineComponentInfos = application.PipelineComponentInfos  
  
    For Each componentInfo As PipelineComponentInfo In componentInfos  
      Console.WriteLine("Name: " & componentInfo.Name & vbCrLf & _  
        " CreationName: " & componentInfo.CreationName & vbCrLf)  
    Next  
  
    Console.Read()  
  
  End Sub  
  
End Module  
```
  
## <a name="see-also"></a>Vedere anche  
 [Aggiunta di componenti flusso di dati a livello di codice](../../integration-services/building-packages-programmatically/adding-data-flow-components-programmatically.md)  
  
  
