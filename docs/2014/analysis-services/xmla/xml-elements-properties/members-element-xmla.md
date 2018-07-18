---
title: Elemento Members (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Members Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Members
- urn:schemas-microsoft-com:xml-analysis#Members
- microsoft.xml.analysis.members
helpviewer_keywords:
- Members element
ms.assetid: 55f9ec3a-5a41-4b3a-acd6-c07598868c46
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 37eb0532f56fd4aff8ca760b843697f30f3c9585
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37201961"
---
# <a name="members-element-xmla"></a>Elemento Members (XMLA)
  Contiene una raccolta di [membro](member-element-xmla.md) gli elementi contenuti dall'elemento padre [CrossProduct](crossproduct-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<CrossProduct>  
   <Members Hierarchy="string">  
      <Member>...</Member>  
   </Members>  
   ...  
</CrossProduct>  
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
|Elementi padre|[CrossProduct](crossproduct-element-xmla.md)|  
|Elementi figlio|[Membro](member-element-xmla.md)|  
  
## <a name="attributes"></a>Attributi  
  
|attribute|Description|  
|---------------|-----------------|  
|Gerarchia|Obbligatorio `String` attributo. Il nome della gerarchia a cui appartengono i membri contenuti nell'elemento `Members`.|  
  
## <a name="remarks"></a>Note  
 Quando un'applicazione client imposta la `AxisFormat` proprietà *ClusterFormat*, i membri su ogni asse sono divisi in cluster in cui ogni cluster rappresenta un prodotto incrociato tra set ordinati di membri da ogni gerarchia. Ogni elemento `Axis` è costituito da uno o più elementi `CrossProduct`. Ogni elemento `CrossProduct` contiene un elemento `Members` per ogni gerarchia sull'asse. L'elemento `Members` contiene a sua volta un elemento `Member` per ogni membro della gerarchia specificata incluso nel prodotto incrociato.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrata la struttura del `Members` elemento quando un client specifica *ClusterFormat* per il `AxisFormat` proprietà XMLA, presupponendo i membri seguenti per l'asse:  
  
||||||  
|-|-|-|-|-|  
|Gerarchia `Time`|1999|1999|2000|2001|  
|Gerarchia `Category`|Valore effettivo|Budget|Budget|Budget|  
|Clusters|Cluster 1|Cluster 1|Cluster 1|Cluster 2|  
  
```  
<Axes>  
   <Axis name="Axis0">  
      <CrossProduct Size = "4">  
         <Members Hierarchy="Time">  
            <Member>  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member>  
               <UName>[Time].[2000]</UName>  
               ...  
            </Member>  
         </Members>  
         <Members Hierarchy="Category">  
            <Member>  
               <UName>[Scenario].[Actual]</UName>  
               ...  
            </Member>  
            <Member>  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Members>  
      </CrossProduct>  
      <CrossProduct Size = "1">  
         <Members Hierarchy="Time">  
            <Member>  
               <UName>[Time].[2001]</UName>  
               ...  
            </Member>  
         </Members>  
         <Members Hierarchy="Category">  
            <Member>  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Members>  
      </CrossProduct>  
   </Axis>  
   ...  
</Axes>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
