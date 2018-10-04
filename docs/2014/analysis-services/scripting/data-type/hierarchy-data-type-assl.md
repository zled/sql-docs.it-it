---
title: Tipo di dati Hierarchy (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Hierarchy Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Hierarchy data type
ms.assetid: 2e05917e-7e5d-4dd1-817b-4ff5647747ff
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8bce652f4fcb0453606ecfa2b2f23796f55d399c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48199961"
---
# <a name="hierarchy-data-type-assl"></a>Tipo di dati Hierarchy (ASSL)
  Definisce un tipo di dati primitivo che rappresenta una gerarchia in una dimensione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Hierarchy>  
   <Name>...</Name>  
   <ID>...</ID>  
   <Description>...</Description>  
   <DisplayFolder>...</DisplayFolder>  
   <Translations>...</Translations>  
   <AllMemberName>...</AllMemberName>  
   <AllMemberTranslations>...</AllMemberTranslation>  
   <MemberNamesUnique>...</MemberNamesUnique>  
   <AllowDuplicateNames>...</AllowDuplicateNames>  
   <Levels>...</Levels>  
   <Annotations>...</Annotation>  
</Hierarchy>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|None|  
|Tipi di dati derivati|None|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|[AllMemberName](../properties/name-element-assl.md), [AllMemberTranslations](../collections/translations-element-assl.md), [AllowDuplicateNames](../properties/allowduplicatenames-element-assl.md), [Annotations](../collections/annotations-element-assl.md), [Description](../properties/description-element-assl.md), [DisplayFolder](../properties/displayfolder-element-assl.md), [ID](../properties/id-element-assl.md), [Levels](../collections/levels-element-assl.md), [MemberNamesUnique](../properties/membernamesunique-element-assl.md), [Name](../properties/name-element-assl.md), [Translations](../collections/translations-element-assl.md)|  
|Elementi derivati|[Hierarchy](../objects/hierarchy-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 L'elemento *MemberNamesUnique* non è supportato con il valore 1 o 2 di DevelopmentMode rispettivamente per le modalità del server SharePoint o tabulare.  
  
 L'elemento *MemberKeysUnique* non è supportato con il valore 1 o 2 di DevelopmentMode rispettivamente per le modalità del server SharePoint o tabulare.  
  
 L'elemento *AllowDuplicateNames* non è supportato con il valore 1 o 2 di DevelopmentMode rispettivamente per le modalità del server SharePoint o tabulare.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.Hierarchy>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
