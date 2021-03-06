---
title: Definizione e identificazione di oggetti (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 595a792e515e862297389faccc324fff8727b8da
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/26/2018
ms.locfileid: "50147986"
---
# <a name="defining-and-identifying-objects-xmla"></a>Definizione e identificazione di oggetti (XMLA)
  Nei comandi XMLA (XML for Analysis) gli oggetti vengono identificati tramite identificatori e riferimenti all'oggetto e vengono definiti tramite comandi XMLA relativi a elementi ASSL (Analysis Services Scripting Language).  
  
## <a name="object-identifiers"></a>Identificatori di oggetto  
 Un oggetto viene identificato tramite l'identificatore univoco dell'oggetto come definito in un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Gli identificatori di oggetto possono essere specificati in modo esplicito o determinati dall'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] quando l'oggetto viene creato in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. È possibile usare la [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) metodo per recuperare gli identificatori di oggetto per successivi `Discover` oppure [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) chiamate al metodo.  
  
## <a name="object-references"></a>Riferimenti agli oggetti  
 Numerosi comandi XMLA, ad esempio [eliminare](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/delete-element-xmla) oppure [processo](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla), usare un riferimento all'oggetto per fare riferimento a un oggetto in modo non ambiguo. Un riferimento all'oggetto contiene l'identificatore dell'oggetto su cui viene eseguito un comando e gli identificatori di oggetto dei predecessori dell'oggetto specifico. Il riferimento all'oggetto per una partizione ad esempio contiene l'identificatore di oggetto della partizione nonché gli identificatori di oggetto del gruppo di misure padre della partizione specifica, del cubo e del database.  
  
## <a name="object-definitions"></a>Definizioni di oggetti  
 Il [Create](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla) e [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) comandi in XMLA creano o modificano, rispettivamente, gli oggetti in un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] istanza. Le definizioni per tali oggetti sono rappresentate da un [ObjectDefinition](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/objectdefinition-element-xmla) elemento che contiene elementi ASSL. Gli identificatori di oggetto possono essere specificati in modo esplicito per tutti i principali e molti oggetti secondari tramite il [ID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) elemento. Se l'elemento `ID` non viene utilizzato, l'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] specifica un identificatore univoco, con una convenzione di denominazione che dipende dall'oggetto da identificare. Per altre informazioni su come usare il `Create` e `Alter` comandi per definire gli oggetti, vedere [creazione e modifica di oggetti &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects).  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento dell'oggetto &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)   
 [Elemento ParentObject &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)   
 [Elemento Source &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla)   
 [Elemento target &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/target-element-xmla)   
 [Sviluppo con XMLA in Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
