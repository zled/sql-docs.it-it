---
title: Elemento ALTER (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Alter Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Alter
- microsoft.xml.analysis.alter
- urn:schemas-microsoft-com:xml-analysis#Alter
helpviewer_keywords:
- Alter command
ms.assetid: 84e58385-c9ba-48fa-a867-94d35b777a56
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a9bdf13c64834100db14357a5a0ac7f47a6f9bf3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48205791"
---
# <a name="alter-element-xmla"></a>Elemento Alter (XMLA)
  Contiene gli elementi di Analysis Services Scripting Language (ASSL) usati per il [Execute](../xml-elements-methods-execute.md) metodo per modificare gli oggetti in un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <Alter Scope="enum" AllowCreate="boolean" ObjectExpansion="enum">  
      <Object>...</Object>  
      <ObjectDefinition>...</ObjectDefinition>  
   </Alter>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Command](../xml-elements-properties/command-element-xmla.md)|  
|Elementi figlio|[Oggetto](../xml-elements-properties/object-element-xmla.md), [ObjectDefinition](../xml-elements-properties/objectdefinition-element-xmla.md)|  
  
## <a name="attributes"></a>Attributi  
  
|attribute|Description|  
|---------------|-----------------|  
|AllowCreate|(Attributo `Boolean` facoltativo) Indica se gli oggetti definiti nel comando `Alter` devono essere creati se non esistono già.<br /><br /> Se è impostato su True, gli oggetti definiti nell'elemento `ObjectDefinition` vengono creati nell'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], se non esistono già. In altre parole, il comando `Alter` viene trattato come comando `Create` se gli oggetti non esistono già nell'istanza.<br /><br /> Se l'attributo viene omesso o impostato su `false`, se gli oggetti non esistono già si verifica un errore.|  
|ObjectExpansion|(Attributo `Enum` facoltativo) Definisce l'ambito della modifica che deve essere eseguita tramite il metodo `Execute`.<br /><br /> Se impostato su *ObjectProperties*, il `ObjectDefinition` elemento deve contenere solo la definizione completa dell'oggetto principale da modificare, inclusi gli oggetti secondari subordinati. Gli oggetti principali subordinati dell'oggetto da modificare non vengono modificati. **Nota:** quando si usa la *ObjectProperties* impostazione con il [ClrAssembly](../../scripting/data-type/assembly-data-type-assl.md) tipo di dati, la [dati](../../scripting/objects/data-element-assl.md) elemento dell'oggetto associato [ ClrAssemblyFile](../../scripting/data-type/clrassemblyfile-data-type-assl.md) non è necessario specificare i tipi di dati. Se non è specificato, `ClrAssembly` utilizza i file esistenti. <br /><br /> Se impostato su *ExpandFull*, il `ObjectDefinition` elemento dovrebbe contenere non solo la definizione dell'oggetto che si desidera modificare, ma anche le definizioni di tutti gli oggetti principali discendenti dell'oggetto da modificare. **Nota:** il *ExpandFull* impostazione non può essere usata con il [Server](../../scripting/objects/server-element-assl.md) elemento.|  
|Ambito|(Attributo `Enum` facoltativo) Definisce la durata degli oggetti definiti nell'elemento `ObjectDefinition`.<br /><br /> Se impostato su *sessione*, gli oggetti definiti nel `ObjectDefinition` elemento esiste solo per la durata della sessione XMLA. **Nota:** quando si usano i *sessione* impostazione, il `ObjectDefinition` elemento può contenere solo [dimensione](../../scripting/objects/dimension-element-assl.md), [cubo](../../scripting/objects/cube-element-assl.md), o [MiningModel ](../../scripting/objects/miningmodel-element-assl.md) Gli elementi ASSL. <br /><br /> Se questo attributo viene omesso, gli oggetti definiti nell'elemento `ObjectDefinition` vengono salvati in modo permanente sull'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
  
## <a name="remarks"></a>Note  
 Ciascuna `Alter` comando modifica la definizione di un oggetto principale nell'oggetto padre specificato per il [ParentObject](../xml-elements-properties/parentobject-element-xmla.md) elemento.  
  
## <a name="see-also"></a>Vedere anche  
 [I comandi &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
