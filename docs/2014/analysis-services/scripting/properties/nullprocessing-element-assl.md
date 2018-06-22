---
title: Elemento NullProcessing (ASSL) | Documenti Microsoft
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
- NullProcessing Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- NullProcessing
helpviewer_keywords:
- NullProcessing element
ms.assetid: 697be5c6-e9a6-4f74-9ff4-5f31400c2178
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 54b75b2e1a7bddd6f7b5df1aeda0311c1b60ff99
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055782"
---
# <a name="nullprocessing-element-assl"></a>NullProcessing Element (ASSL)
  Definisce come vengono elaborati i valori null.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DataItem>  
   ...  
   <NullProcessing>...</NullProcessing>  
   ...  
</DataItem>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Automatico*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Preserve*|Mantiene il valore Null. **Nota:** questo valore non è supportato per le misure distinct count.|  
|*Errore*|Genera un errore di chiave Null. Il valore di [NullKeyNotAllowed](nullkeynotallowed-element-assl.md) determina la modalità con cui l'istanza reagisce all'errore. **Nota:** questo valore non è supportato per le misure.|  
|*UnknownMember*|Genera un membro sconosciuto e un errore di conversione di valori Null. Il valore di [NullKeyConvertedToUnknown](nullkeyconvertedtounknown-element-assl.md) determina la modalità con cui l'istanza reagisce all'errore. **Nota:** questo valore non è supportato per le colonne associate alle misure.|  
|*ZeroOrBlank*|Converte il valore Null in zero (per gli elementi di dati numerici) o in una stringa vuota (per gli elementi di dati di tipo stringa). **Nota:** questo valore garantisce la compatibilità con le versioni precedenti di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|*Automatico*|Utilizza l'elaborazione predefinita appropriata per l'elemento:<br /><br /> -   *ZeroOrBlank* per gli elementi di dati OLAP.<br />-   *UnknownMember* per gli elementi di dati data mining.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `NullProcessing` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.NullProcessing>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  