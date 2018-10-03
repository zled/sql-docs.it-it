---
title: Elemento create (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Create Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Create
- urn:schemas-microsoft-com:xml-analysis#Create
- microsoft.xml.analysis.create
helpviewer_keywords:
- Create command (XMLA)
ms.assetid: a623d362-a1ac-40e4-8816-65fac89cb391
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b64f6b222793fdd7c6b92e7462fc10976c0bc139
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48051291"
---
# <a name="create-element-xmla"></a>Elemento Create (XMLA)
  Contiene gli elementi di Analysis Services Scripting Language (ASSL) usati per il `Execute` metodo per creare oggetti in un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza.  
  
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
|Elementi padre|[Command](../xml-elements-properties/command-element-xmla.md)|  
|Elementi figlio|[ObjectDefinition](../xml-elements-properties/objectdefinition-element-xmla.md), [ParentObject](../xml-elements-properties/object-element-xmla.md)|  
  
## <a name="attributes"></a>Attributi  
  
|attribute|Description|  
|---------------|-----------------|  
|AllowOverwrite|Facoltativo `Boolean` attributo. Se è impostato a Vero, gli oggetti definiti nell'elemento `ObjectDefinition` possono sovrascrivere oggetti esistenti sull'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Se questo attributo è omesso o impostato a Falso, la presenza di un oggetto esistente genera un errore.|  
|Ambito|Facoltativo `Enum` attributo. Definisce la durata degli oggetti definiti nell'elemento `ObjectDefinition`. Se questo attributo viene omesso, gli oggetti definiti nell'elemento `ObjectDefinition` vengono salvati in modo permanente sull'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Sono disponibili i valori seguenti.<br /><br /> -   *Sessione*<br />     Gli oggetti definiti nell'elemento `ObjectDefinition` esistono solo per la durata della sessione di XML for Analysis (XMLA). **Nota:** quando si usano i *sessione* impostazione, il `ObjectDefinition` elemento può contenere solo [dimensione](../../scripting/objects/dimension-element-assl.md), [cubo](../../scripting/objects/cube-element-assl.md), o [MiningModel ](../../scripting/objects/miningmodel-element-assl.md) Gli elementi ASSL.|  
  
## <a name="remarks"></a>Note  
 Ogni operazione `Create` crea un oggetto principale sotto un padre fornito dall'elemento `ParentObject`. Se l'oggetto padre viene omesso, si presuppone che sia l'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] di destinazione. Questo genera un errore se il padre di un oggetto principale non è l'istanza di destinazione.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrata la creazione di un database vuoto denominato `Test Database` in un'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
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
 [I comandi &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
