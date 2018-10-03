---
title: Elemento ObjectDefinition (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ObjectDefinition Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#ObjectDefinition
- http://schemas.microsoft.com/analysisservices/2003/engine#ObjectDefinition
- microsoft.xml.analysis.objectdefinition
helpviewer_keywords:
- ObjectDefinition element
ms.assetid: 1911868c-a018-4308-8cf9-972a57f610a1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bc2b42ca96ef57bc46e5c04a5bc1f7528493aa83
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48214141"
---
# <a name="objectdefinition-element-xmla"></a>Elemento ObjectDefinition (XMLA)
  Contiene uno o più elementi di Analysis Services Scripting Language (ASSL), usati per creare o modificare oggetti in un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Create> <!-- or Alter -->  
   ...  
   <ObjectDefinition>  
      <!-- One or more ASSL elements -->  
   </ObjectDefinition>  
   ...  
</Create>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[ALTER](../xml-elements-commands/alter-element-xmla.md), [creare](../xml-elements-commands/create-element-xmla.md)|  
|Elementi figlio|Elementi ASSL obbligatori. Uno o più elementi ASSL, utilizzati per definire oggetti [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Per altre informazioni su ASSL, vedere [proprietà &#40;XMLA&#41;](xml-elements-properties.md).|  
  
## <a name="remarks"></a>Note  
  
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
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
