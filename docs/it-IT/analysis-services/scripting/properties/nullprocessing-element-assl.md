---
title: Elemento NullProcessing (ASSL) | Documenti Microsoft
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.custom: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- NullProcessing Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- NullProcessing
helpviewer_keywords:
- NullProcessing element
ms.assetid: 697be5c6-e9a6-4f74-9ff4-5f31400c2178
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 235fe69999b25664642b7f449b6ded806dd7b1ac
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="nullprocessing-element-assl"></a>NullProcessing Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Automatico*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*Mantenere*|Mantiene il valore Null.<br /><br /> Nota: Questo valore non è supportato per le misure distinct count.|  
|*Errore*|Genera un errore di chiave Null. Il valore di [NullKeyNotAllowed](../../../analysis-services/scripting/properties/nullkeynotallowed-element-assl.md) determina la modalità con cui l'istanza reagisce all'errore.<br /><br /> Nota: Questo valore non è supportato per le misure.|  
|*UnknownMember*|Genera un membro sconosciuto e un errore di conversione di valori Null. Il valore di [NullKeyConvertedToUnknown](../../../analysis-services/scripting/properties/nullkeyconvertedtounknown-element-assl.md) determina la modalità con cui l'istanza reagisce all'errore.<br /><br /> Nota: Questo valore non è supportato per le colonne associate alle misure.|  
|*ZeroOrBlank*|Converte il valore Null in zero (per gli elementi di dati numerici) o in una stringa vuota (per gli elementi di dati di tipo stringa).<br /><br /> Nota: Questo valore garantisce la compatibilità con le versioni precedenti di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|*Automatico*|Utilizza l'elaborazione predefinita appropriata per l'elemento:<br /><br /> *ZeroOrBlank* per gli elementi di dati OLAP.<br /><br /> *UnknownMember* per gli elementi di dati di data mining.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **NullProcessing** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.NullProcessing>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
