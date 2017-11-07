---
title: Elemento Annotation (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Annotation Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Annotation
helpviewer_keywords:
- Annotation element
ms.assetid: 7d75291a-47b4-498a-8ba4-3d093b8513b2
caps.latest.revision: 43
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 109386991ba5d632e6c40523241f6d64c4dba05d
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="annotation-element-assl"></a>Elemento Annotation (ASSL)
  Contiene elementi utilizzati per estendere lo schema ASSL (Analysis Services Scripting Language).  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Annotations>  
   <Annotation>  
      <Name>...</Name>  
      <Visibility>...</Visibility>  
      <Value>...</Value>  
   </Annotation>  
</Annotations >  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Annotazioni](../../../analysis-services/scripting/collections/annotations-element-assl.md)|  
|Elementi figlio|[Nome](../../../analysis-services/scripting/properties/name-element-assl.md), [valore](../../../analysis-services/scripting/properties/value-element-assl.md), [visibilità](../../../analysis-services/scripting/properties/visibility-element-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Il **annotazione** elemento fornisce estensibilità dello schema ASSL per tutti gli oggetti diversi da quelli utilizzati esclusivamente per definire un tipo di dati complessi. Il **valore** elemento il **annotazione** elemento può contenere valori XML validi di qualsiasi spazio dei nomi XML diverso da ASSL, soggetti alle regole seguenti:  
  
-   Il valore XML può contenere solo elementi.  
  
-   Ogni elemento deve avere un nome univoco. È consigliabile che il valore del **nome** elemento il **annotazione** elemento fa riferimento a nomi di destinazione.  
  
 Queste regole vengono imposte per consentire il contenuto del **annotazione** coppie elemento deve essere esposta come un set di nome/valore tramite altre interfacce, ad esempio gli oggetti DSO (Decision Support).  
  
 Commenti e gli spazi vuoti all'interno di **annotazione** elemento che non sono racchiusi all'interno di un elemento figlio non può essere mantenuta. Tutti gli elementi devono inoltre essere di lettura/scrittura. Gli elementi di sola lettura vengono ignorati.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.Annotation>.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetti &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  

