---
title: Elemento create (XMLA) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Create Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Create
- urn:schemas-microsoft-com:xml-analysis#Create
- microsoft.xml.analysis.create
helpviewer_keywords:
- Create command (XMLA)
ms.assetid: a623d362-a1ac-40e4-8816-65fac89cb391
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f3e568fb190940822a6c6ef5cb65cf6b9476f4b1
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="create-element-xmla"></a>Elemento Create (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Contiene gli elementi di Analysis Services Scripting Language (ASSL) utilizzati dal **Execute** metodo per creare oggetti in un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <Create Scope="enum" AllowOverwrite="boolean">  
      <ParentObject>...</ParentObject>  
      <ObjectDefinition>...</ObjectDefinition>  
   </Create>  
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
|Elementi figlio|[ObjectDefinition](../../../analysis-services/xmla/xml-elements-properties/objectdefinition-element-xmla.md), [ParentObject](../../../analysis-services/xmla/xml-elements-properties/parentobject-element-xmla.md)|  
  
## <a name="attributes"></a>Attributi  
  
|attribute|Description|  
|---------------|-----------------|  
|AllowOverwrite|Attributo **Boolean** facoltativo. Se è impostata su True, gli oggetti definiti nel **ObjectDefinition** elemento può sovrascrivere oggetti esistenti nel [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza. Se questo attributo è omesso o impostato a Falso, la presenza di un oggetto esistente genera un errore.|  
|Ambito|Parametro facoltativo **Enum** attributo. Definisce la durata degli oggetti definiti nel **ObjectDefinition** elemento. Se questo attributo viene omesso, gli oggetti definiti nel **ObjectDefinition** elemento vengono rese persistenti nel [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza. Il valore seguente è disponibile:<br /><br /> *Sessione*: gli oggetti definiti nel **ObjectDefinition** l'elemento esiste solo per la durata del codice XML per la sessione Analysis (XMLA).<br />                  Si noti che quando si utilizza il *sessione* impostazione, il **ObjectDefinition** elemento può contenere solo [dimensione](../../../analysis-services/scripting/objects/dimension-element-assl.md), [cubo](../../../analysis-services/scripting/objects/cube-element-assl.md), o [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) elementi ASSL.|  
  
## <a name="remarks"></a>Remarks  
 Ogni **crea** operazione crea un oggetto principale sotto un padre fornito dal **ParentObject** elemento. Se l'oggetto padre viene omesso, si presuppone che sia l'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] di destinazione. Questo genera un errore se il padre di un oggetto principale non è l'istanza di destinazione.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente crea un database vuoto denominato **Database di prova** su un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza.  
  
```  
  
      <Create xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
   <ObjectDefinition>  
      <Database xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
         <Name>Test Database</Name>  
         <Description>A test database.</Description>  
      </Database>  
   </ObjectDefinition>  
</Create>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Comandi &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
