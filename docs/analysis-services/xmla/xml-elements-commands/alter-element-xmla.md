---
title: Elemento ALTER (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5ff62bcde0aa40e9bb052691d4d3dee1317c1217
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34574603"
---
# <a name="alter-element-xmla"></a>Elemento Alter (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene gli elementi di Analysis Services Scripting Language (ASSL) utilizzati per il [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) metodo per modificare gli oggetti in un'istanza di Analysis Services.  
  
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
|Elementi padre|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Elementi figlio|[Oggetto](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md), [ObjectDefinition](../../../analysis-services/xmla/xml-elements-properties/objectdefinition-element-xmla.md)|  
  
## <a name="attributes"></a>Attributi  
  
|attribute|Description|  
|---------------|-----------------|  
|AllowCreate|(Facoltativo **booleano** attributo) indica se gli oggetti definiti nel **Alter** comando deve essere creato se non esiste già.<br /><br /> Se impostato su true, gli oggetti definiti nel **ObjectDefinition** elemento vengono create nel [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza se non esiste già. In altre parole, il **Alter** comando viene considerato come un **crea** se gli oggetti non esistono già nell'istanza di comando.<br /><br /> Se questo attributo viene omesso o impostato su **false**, si verifica un errore se gli oggetti non esistono già.|  
|ObjectExpansion|(Facoltativo **Enum** attributo) definisce l'ambito della modifica deve essere eseguita dal **Execute** metodo.<br /><br /> Se impostato su *ObjectProperties*, **ObjectDefinition** elemento deve contenere solo la definizione completa dell'oggetto principale da modificare, inclusi gli oggetti secondari subordinati. Gli oggetti principali subordinati dell'oggetto da modificare non vengono modificati.<br /><br /> Nota: Quando si utilizza il *ObjectProperties* impostazione con il [ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md) tipo di dati, il [dati](../../../analysis-services/scripting/objects/data-element-assl.md) elemento dell'oggetto associato [ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md) non è necessario specificare i tipi di dati. Se non specificato, il **ClrAssembly** utilizza i file esistenti.<br /><br /> Se impostato su *ExpandFull*, **ObjectDefinition** elemento deve contenere non solo la definizione dell'oggetto da modificare, ma anche le definizioni di tutti gli oggetti principali discendenti dell'oggetto per essere modificato.<br /><br /> Nota: Il *ExpandFull* impostazione non può essere usata con il [Server](../../../analysis-services/scripting/objects/server-element-assl.md) elemento.|  
|Ambito|(Facoltativo **Enum** attributo) definisce la durata degli oggetti definiti nel **ObjectDefinition** elemento.<br /><br /> Se impostato su *sessione*, gli oggetti definiti nel **ObjectDefinition** l'elemento esiste solo per la durata della sessione XMLA.<br /><br /> Nota: Quando si utilizza il *sessione* impostazione, il **ObjectDefinition** elemento può contenere solo [dimensione](../../../analysis-services/scripting/objects/dimension-element-assl.md), [cubo](../../../analysis-services/scripting/objects/cube-element-assl.md), o [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) elementi ASSL.<br /><br /> Se questo attributo viene omesso, gli oggetti definiti nel **ObjectDefinition** elemento vengono rese persistenti nel [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza.|  
  
## <a name="remarks"></a>Remarks  
 Ogni **Alter** comando modifica la definizione di un oggetto principale sotto l'oggetto padre specificato da di [ParentObject](../../../analysis-services/xmla/xml-elements-properties/parentobject-element-xmla.md) elemento.  
  
## <a name="see-also"></a>Vedere anche
 [I comandi &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
