---
title: Definizione e identificazione di oggetti (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- objects [XML for Analysis]
- identifying objects [XML for Analysis]
- XML for Analysis, objects
- object references [XML for Analysis]
- object identifiers [XML for Analysis]
- object definitions [XML for Analysis]
- XMLA, objects
ms.assetid: 43b65f6d-0123-4556-81f0-c7a0b84361e5
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c788129026d4dffe5c81efc82492fa8a5566de2a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37303041"
---
# <a name="defining-and-identifying-objects-xmla"></a>Definizione e identificazione di oggetti (XMLA)
  Nei comandi XMLA (XML for Analysis) gli oggetti vengono identificati tramite identificatori e riferimenti all'oggetto e vengono definiti tramite comandi XMLA relativi a elementi ASSL (Analysis Services Scripting Language).  
  
## <a name="object-identifiers"></a>Identificatori di oggetto  
 Un oggetto viene identificato tramite l'identificatore univoco dell'oggetto come definito in un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Gli identificatori di oggetto possono essere specificati in modo esplicito o determinati dall'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] quando l'oggetto viene creato in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. È possibile usare la [Discover](../xmla/xml-elements-methods-discover.md) metodo per recuperare gli identificatori di oggetto per successivi `Discover` oppure [Execute](../xmla/xml-elements-methods-execute.md) chiamate al metodo.  
  
## <a name="object-references"></a>Riferimenti agli oggetti  
 Numerosi comandi XMLA, ad esempio [eliminare](../xmla/xml-elements-commands/delete-element-xmla.md) oppure [processo](../xmla/xml-elements-commands/process-element-xmla.md), usare un riferimento all'oggetto per fare riferimento a un oggetto in modo non ambiguo. Un riferimento all'oggetto contiene l'identificatore dell'oggetto su cui viene eseguito un comando e gli identificatori di oggetto dei predecessori dell'oggetto specifico. Il riferimento all'oggetto per una partizione ad esempio contiene l'identificatore di oggetto della partizione nonché gli identificatori di oggetto del gruppo di misure padre della partizione specifica, del cubo e del database.  
  
## <a name="object-definitions"></a>Definizioni di oggetti  
 Il [Create](../xmla/xml-elements-commands/create-element-xmla.md) e [Alter](../xmla/xml-elements-commands/alter-element-xmla.md) comandi in XMLA creano o modificano, rispettivamente, gli oggetti in un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] istanza. Le definizioni per tali oggetti sono rappresentate da un [ObjectDefinition](../xmla/xml-elements-properties/objectdefinition-element-xmla.md) elemento che contiene elementi ASSL. Gli identificatori di oggetto possono essere specificati in modo esplicito per tutti i principali e molti oggetti secondari tramite il [ID](../xmla/xml-elements-properties/id-element-xmla.md) elemento. Se l'elemento `ID` non viene utilizzato, l'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] specifica un identificatore univoco, con una convenzione di denominazione che dipende dall'oggetto da identificare. Per altre informazioni su come usare il `Create` e `Alter` comandi per definire gli oggetti, vedere [creazione e modifica di oggetti &#40;XMLA&#41;](../xmla/xml-elements-objects.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento dell'oggetto &#40;XMLA&#41;](../xmla/xml-elements-properties/object-element-xmla.md)   
 [Elemento ParentObject &#40;XMLA&#41;](../xmla/xml-elements-properties/parentobject-element-xmla.md)   
 [Elemento Source &#40;XMLA&#41;](../xmla/xml-elements-properties/source-element-xmla.md)   
 [Elemento target &#40;XMLA&#41;](../xmla/xml-elements-properties/target-element-xmla.md)   
 [Sviluppo con XMLA in Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
