---
title: Elemento Annotation (ASSL) | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 303ed41b27538d5e21541e2912e892d91fd0f3d0
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34034478"
---
# <a name="annotation-element-assl"></a>Elemento Annotation (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
 [Oggetti & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
