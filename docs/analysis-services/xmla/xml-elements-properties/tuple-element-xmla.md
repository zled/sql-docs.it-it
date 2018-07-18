---
title: Elemento Tuple (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0192a126b3be4338cedd47c1cd5b175ba1debc41
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38062668"
---
# <a name="tuple-element-xmla"></a>Elemento Tuple (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene una raccolta di elementi [Member](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md) contenuti dall'elemento padre [Tuple](../../../analysis-services/xmla/xml-elements-properties/tuples-element-xmla.md).  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Tuples>  
   <Tuple>  
      <Member>...</Member>  
   </Tuple>  
   ...  
</Tuples>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche di elementi  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Elementi-relazioni  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Tuple](../../../analysis-services/xmla/xml-elements-properties/tuples-element-xmla.md)|  
|Elementi figlio|[Membro](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Quando un'applicazione client imposta la proprietà **AxisFormat** su *TupleFormat*, un’asse viene rappresentata come un set di tuple. Ogni elemento **Axis** contiene un elemento **Tuples** che rappresenta il set di tuple su quell’asse. Ogni tupla viene rappresentata usando un elemento **Tuple** che contiene elementi **Member** di ogni gerarchia sull'asse.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra la struttura dell'elemento **Tuple** quando un client specifica *TupleFormat* o *CustomFormat* per la proprietà XMLA **AxisFormat**, presupponendo i membri seguenti per l'asse:  
  
|||||  
|-|-|-|-|  
|Gerarchia **Time**|1999|1999|2000|  
|Gerarchia **Category**|Valore effettivo|Budget|Budget|  
  
```  
<Axes>  
   <Axis name="Axis0">  
      <Tuples>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Actual]</UName>  
               ...  
            </Member>  
         </Tuple>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Tuple>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[2000]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Tuple>  
      </Tuples>  
   </Axis>  
   ...  
</Axes>  
```  
  
## <a name="see-also"></a>Vedere anche
 [Proprietà &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
