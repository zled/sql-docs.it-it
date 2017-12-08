---
title: Definizione e identificazione di oggetti (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- objects [XML for Analysis]
- identifying objects [XML for Analysis]
- XML for Analysis, objects
- object references [XML for Analysis]
- object identifiers [XML for Analysis]
- object definitions [XML for Analysis]
- XMLA, objects
ms.assetid: 43b65f6d-0123-4556-81f0-c7a0b84361e5
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5f04bf324a3434c9806f27ab15a32e3c53d962d7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="defining-and-identifying-objects-xmla"></a>Definizione e identificazione di oggetti (XMLA)
  Nei comandi XMLA (XML for Analysis) gli oggetti vengono identificati tramite identificatori e riferimenti all'oggetto e vengono definiti tramite comandi XMLA relativi a elementi ASSL (Analysis Services Scripting Language).  
  
## <a name="object-identifiers"></a>Identificatori di oggetto  
 Un oggetto viene identificato tramite l'identificatore univoco dell'oggetto come definito in un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Gli identificatori di oggetto possono essere specificati in modo esplicito o determinati dall'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] quando l'oggetto viene creato in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. È possibile utilizzare il [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) metodo per recuperare gli identificatori di oggetto per successive **Discover** o [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md) chiamate al metodo.  
  
## <a name="object-references"></a>Riferimenti agli oggetti  
 Numerosi comandi XMLA, ad esempio [eliminare](../../analysis-services/xmla/xml-elements-commands/delete-element-xmla.md) o [processo](../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md), utilizzare un riferimento all'oggetto per fare riferimento a un oggetto in modo non ambiguo. Un riferimento all'oggetto contiene l'identificatore dell'oggetto su cui viene eseguito un comando e gli identificatori di oggetto dei predecessori dell'oggetto specifico. Il riferimento all'oggetto per una partizione ad esempio contiene l'identificatore di oggetto della partizione nonché gli identificatori di oggetto del gruppo di misure padre della partizione specifica, del cubo e del database.  
  
## <a name="object-definitions"></a>Definizioni di oggetti  
 Il [crea](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md) e [Alter](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md) comandi XMLA creano o modificano, rispettivamente, oggetti in un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] istanza. Le definizioni per tali oggetti sono rappresentate da un [ObjectDefinition](../../analysis-services/xmla/xml-elements-properties/objectdefinition-element-xmla.md) elemento che contiene elementi ASSL. Gli identificatori di oggetto possono essere specificati in modo esplicito per tutti i principali e molti oggetti secondari tramite il [ID](../../analysis-services/xmla/xml-elements-properties/id-element-xmla.md) elemento. Se il **ID** elemento non viene usato, il [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] istanza fornisce un identificatore univoco, con una convenzione di denominazione che dipende dall'oggetto che deve essere identificato. Per ulteriori informazioni sull'utilizzo di **crea** e **Alter** comandi per definire gli oggetti, vedere [creazione e modifica di oggetti &#40; XMLA &#41; ](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/creating-and-altering-objects-xmla.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto elemento &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)   
 [Elemento ParentObject &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-properties/parentobject-element-xmla.md)   
 [Elemento Source &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md)   
 [Elemento di destinazione &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-properties/target-element-xmla.md)   
 [Sviluppo con XMLA in Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
