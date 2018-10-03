---
title: Elemento EntitySet (CSDLBI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: d4703c9e-5594-472e-a85b-0f5bd0d73d6f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dabe6cf0748f220fcef7bfb9b2577426c7ff65a2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48091631"
---
# <a name="entityset-element-csdlbi"></a>Elemento EntitySet (CSDLBI)
  L'elemento EntitySet definisce una raccolta di entità di un particolare tipo un modello di dati CSDLBI.  
  
 L'elemento EntitySet deve specificare ognuno dei tipi di entità inclusi nel modello di dati. Le informazioni su queste entità del modello vengono specificate elencando le entità figlio del tipo, l'elemento Entità. Per altre informazioni, vedere [Elemento EntityType &#40;CSDLBI&#41;](entitytype-element-csdlbi.md).  
  
 Le proprietà come le regole di confronto e la lingua vengono definite al livello di EntityContainer, non sui singoli oggetti. Tuttavia, le colonne e gli attributi di testo all'interno del modello possono presentare didascalie o traduzioni in altre lingue.  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Nella tabella seguente vengono elencati gli elementi e gli attributi che definiscono un elemento EntitySet.  
  
|Nome attributo|Obbligatorio|Description|  
|--------------------|-----------------|-----------------|  
|Didascalia|no|Descrizione intuitiva del set di entità.|  
|CollectionCaption|no|Stringa contenente il nome plurale dell'entità.|  
|ReferenceName|no|Contiene il nome completo e non unito dell'entità. In un modello multidimensionale, corrisponde al nome di CubeDimension.|  
|Hidden|no|Indica se l'entità è nascosta. Per impostazione predefinita le entità non sono nascoste.|  
  
## <a name="example"></a>Esempio  
 **Tabella**  
  
 Nel seguente esempio, in CSDLBI versione 1.1, vengono illustrate le definizioni delle tabelle Date e Geography del modello tabulare di AdventureWorks.  
  
```  
  
<EntitySet   
   Name="Date"   
   EntityType="Sandbox. Date">  
<bi:EntitySet />  
</EntitySet>  
  
<EntitySet   
   Name="Geography"   
   EntityType="Sandbox.Geography">  
<bi:EntitySet />  
</EntitySet>  
```  
  
## <a name="example"></a>Esempio  
 **Multidimensionale**  
  
 Nell'esempio seguente, in CSDLBI versione 1.1, vengono illustrati diversi elementi EntitySet del cubo Operations di Contoso Retail.  
  
```  
  
<EntitySet Name="Outage" EntityType="Sandbox.Outage">  
       <bi:EntitySet />  
</EntitySet>  
  
<EntitySet Name="Store" EntityType="Sandbox.Store">  
     <bi:EntitySet />  
</EntitySet>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento tecnico per le annotazioni di Business Intelligence per CSDL](technical-reference-for-bi-annotations-to-csdl.md)  
  
  
