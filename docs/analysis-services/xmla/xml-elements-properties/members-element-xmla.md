---
title: Elemento Members (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5ae4326e00ba98075a86079157484c5963d0147d
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34579103"
---
# <a name="members-element-xmla"></a>Elemento Members (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene una raccolta di [membro](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md) elementi contenuti dall'elemento padre [CrossProduct](../../../analysis-services/xmla/xml-elements-properties/crossproduct-element-xmla.md) elemento.  
  
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
|Elementi padre|[CrossProduct](../../../analysis-services/xmla/xml-elements-properties/crossproduct-element-xmla.md)|  
|Elementi figlio|[Membro](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md)|  
  
## <a name="attributes"></a>Attributi  
  
|attribute|Description|  
|---------------|-----------------|  
|Gerarchia|Richiesto **stringa** attributo. Il nome della gerarchia a cui i membri contenuti di **membri** l'elemento appartiene.|  
  
## <a name="remarks"></a>Remarks  
 Quando un'applicazione client imposta il **AxisFormat** proprietà *ClusterFormat*, i membri su ogni asse sono divisi in cluster in cui ogni cluster rappresenta un prodotto incrociato tra set ordinati di membri di ogni gerarchia. Ogni **asse** elemento è costituito da uno o più **CrossProduct** elementi. Ogni **CrossProduct** elemento contiene un **membri** elemento per ogni gerarchia sull'asse. Il **membri** a sua volta, contiene un elemento, **membro** elemento per ogni membro della gerarchia specificata incluso il prodotto incrociato.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrata la struttura del **membri** elemento quando un client specifica *ClusterFormat* per il **AxisFormat** proprietà XMLA, dato il membri seguenti per l'asse:  
  
||||||  
|-|-|-|-|-|  
|Gerarchia **Time**|1999|1999|2000|2001|  
|Gerarchia **Category**|Valore effettivo|Budget|Budget|Budget|  
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
 [Proprietà &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
