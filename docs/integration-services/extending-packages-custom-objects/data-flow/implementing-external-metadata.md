---
title: Implementazione di metadati esterni | Documenti Microsoft
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
- disconnected validation [Integration Services]
- connected validation [Integration Services]
- custom data flow components [Integration Services], validating
- validation [Integration Services], components
- metadata [Integration Services]
- data flow components [Integration Services], validating
- data flow components [Integration Services], external metadata
- custom data flow components [Integration Services], external metadata
- external metadata [Integration Services]
ms.assetid: 8f5bd3ed-3e79-43a4-b6c1-435e4c2cc8cc
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 96d413bca20ec171d515ac6d0ad81b5b994bd854
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="implementing-external-metadata"></a>Implementazione di metadati esterni
  Quando un componente è disconnesso dalla relativa origine dati, è possibile convalidare le colonne nelle raccolte di colonne di input e output in base alle colonne presenti nell'origine dati esterna utilizzando l'interfaccia <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100>. Questa interfaccia consente di mantenere uno snapshot delle colonne presenti nell'origine dati esterna e di eseguire il mapping di queste colonne alle raccolte di colonne di input e output del componente.  
  
 L'implementazione di colonne di metadati esterni aggiunge un livello di overhead e complessità allo sviluppo di componenti, perché è necessario mantenere una raccolta aggiuntiva di colonne ed eseguire la convalida in base ad essa, ma la possibilità di evitare onerosi round trip al server per la convalida giustifica questa attività di sviluppo.  
  
## <a name="populating-external-metadata-columns"></a>Popolamento di colonne di metadati esterni  
 Le colonne di metadati esterni vengono in genere aggiunte alla raccolta quando viene creata la corrispondente colonna di input o di output. Le nuove colonne vengono create chiamando il metodo <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.New%2A>. Le proprietà della colonna vengono quindi impostate in base all'origine dati esterna.  
  
 Il mapping della colonna di metadati esterni alla corrispondente colonna di input o di output viene eseguito assegnando l'ID della prima alla proprietà <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.ExternalMetadataColumnID%2A> della seconda. In questo modo è possibile individuare facilmente la colonna di metadati esterni per una specifica colonna di input o di output utilizzando il metodo <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.GetObjectByID%2A> della raccolta.  
  
 Nell'esempio seguente viene illustrato come creare una colonna di metadati esterni e quindi eseguirne il mapping a una colonna di output impostando la proprietà <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.ExternalMetadataColumnID%2A>.  
  
```csharp  
public void CreateExternalMetaDataColumn(IDTSOutput100 output, int outputColumnID )  
{  
    IDTSOutputColumn100 oColumn = output.OutputColumnCollection.GetObjectByID(outputColumnID);  
    IDTSExternalMetadataColumn100 eColumn = output.ExternalMetadataColumnCollection.New();  
  
    eColumn.DataType = oColumn.DataType;  
    eColumn.Precision = oColumn.Precision;  
    eColumn.Scale = oColumn.Scale;  
    eColumn.Length = oColumn.Length;  
    eColumn.CodePage = oColumn.CodePage;  
  
    oColumn.ExternalMetadataColumnID = eColumn.ID;  
}  
```  
  
```vb  
Public Sub CreateExternalMetaDataColumn(ByVal output As IDTSOutput100, ByVal outputColumnID As Integer)   
 Dim oColumn As IDTSOutputColumn100 = output.OutputColumnCollection.GetObjectByID(outputColumnID)   
 Dim eColumn As IDTSExternalMetadataColumn100 = output.ExternalMetadataColumnCollection.New   
 eColumn.DataType = oColumn.DataType   
 eColumn.Precision = oColumn.Precision   
 eColumn.Scale = oColumn.Scale   
 eColumn.Length = oColumn.Length   
 eColumn.CodePage = oColumn.CodePage   
 oColumn.ExternalMetadataColumnID = eColumn.ID   
End Sub  
```  
  
## <a name="validating-with-external-metadata-columns"></a>Convalida delle colonne di metadati esterni  
 La convalida richiede passaggi aggiuntivi per i componenti che mantengono una raccolta di colonne di metadati esterni, perché è necessario eseguirla in base a una raccolta aggiuntiva di colonne. La convalida può essere eseguita in modalità connessa o disconnessa.  
  
### <a name="connected-validation"></a>Convalida in modalità connessa  
 Quando un componente è connesso a un'origine dati esterna, le colonne delle raccolte di input o output vengono verificate direttamente in base all'origine dati esterna. È inoltre necessario convalidare le colonne della raccolta di metadati esterni. Questa operazione è necessaria perché la raccolta dei metadati esterni può essere modificata utilizzando il **Editor avanzato** in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], e le modifiche apportate alla raccolta non sono rilevabili. Pertanto, se connessi, i componenti devono assicurarsi che le colonne della raccolta di colonne di metadati esterni continuino a riflettere le colonne presenti nell'origine dati esterna.  
  
 È possibile scegliere di nascondere la raccolta di metadati esterni nel **Editor avanzato** impostando il <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.IsUsed%2A> proprietà della raccolta in **false**. Tuttavia in questo modo si nasconde anche la **Mapping colonne** scheda dell'editor, che consente agli utenti di eseguire il mapping di colonne da una raccolta di input o output e le colonne nella raccolta delle colonne di metadati esterna. Impostando questa proprietà su **false** non impedisce agli sviluppatori di modifica a livello di codice della raccolta, ma fornisce un livello di protezione per la raccolta di colonne di metadati esterna di un componente utilizzato esclusivamente in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].  
  
### <a name="disconnected-validation"></a>Convalida in modalità disconnessa  
 Quando un componente è disconnesso da un'origine dati esterna, la convalida risulta semplificata, perché le colonne della raccolta di input o output vengono verificate direttamente in base alle colonne della raccolta di metadati esterni e non rispetto all'origine esterna. Un componente deve eseguire la convalida in modalità disconnessa quando non è stata stabilita la connessione all'origine dati esterna o quando il <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ValidateExternalMetadata%2A> proprietà **false**.  
  
 Nell'esempio di codice seguente è illustrata un'implementazione di un componente che esegue la convalida in base alla raccolta di colonne di metadati esterni.  
  
```csharp  
public override DTSValidationStatus Validate()  
{  
    if( this.isConnected && ComponentMetaData.ValidateExternalMetaData )  
    {  
        // TODO: Perform connected validation.  
    }  
    else  
    {  
        // TODO: Perform disconnected validation.  
    }  
}  
```  
  
```vb  
Public  Overrides Function Validate() As DTSValidationStatus   
 If Me.isConnected AndAlso ComponentMetaData.ValidateExternalMetaData Then   
  ' TODO: Perform connected validation.  
 Else   
  ' TODO: Perform disconnected validation.  
 End If   
End Function  
```  

## <a name="see-also"></a>Vedere anche  
 [Flusso di dati](../../../integration-services/data-flow/data-flow.md)  
  
  

