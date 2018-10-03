---
title: Elemento NullProcessing (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c7fa4c851e6818a3c9607fed0fdb8b9c499a63d0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48139891"
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
  
## <a name="remarks"></a>Note  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Mantenere*|Mantiene il valore Null. **Nota:** questo valore non è supportato per le misure distinct count.|  
|*Errore*|Genera un errore di chiave Null. Il valore di [NullKeyNotAllowed](nullkeynotallowed-element-assl.md) determina come l'istanza reagisce all'errore. **Nota:** questo valore non è supportato per le misure.|  
|*UnknownMember*|Genera un membro sconosciuto e un errore di conversione di valori Null. Il valore di [NullKeyConvertedToUnknown](nullkeyconvertedtounknown-element-assl.md) determina come l'istanza reagisce all'errore. **Nota:** questo valore non è supportato per le colonne associate alle misure.|  
|*ZeroOrBlank*|Converte il valore Null in zero (per gli elementi di dati numerici) o in una stringa vuota (per gli elementi di dati di tipo stringa). **Nota:** questo valore garantisce la compatibilità con le versioni precedenti di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|*Automatico*|Utilizza l'elaborazione predefinita appropriata per l'elemento:<br /><br /> -   *ZeroOrBlank* per gli elementi di dati OLAP.<br />-   *UnknownMember* per gli elementi di dati data mining.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `NullProcessing` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.NullProcessing>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
