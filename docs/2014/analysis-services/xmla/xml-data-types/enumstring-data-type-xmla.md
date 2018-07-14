---
title: Tipo di dati EnumString (XMLA) | Microsoft Docs
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
- EnumString Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- EnumString
- urn:schemas-microsoft-com:xml-analysis#EnumString
- http://schemas.microsoft.com/analysisservices/2003/engine#EnumString
helpviewer_keywords:
- EnumString data type
ms.assetid: 9214195e-4539-419b-95ec-b7aa75e033ab
caps.latest.revision: 29
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ea4f9057c05d7be5a5f8d8591d27460540a377fe
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37224031"
---
# <a name="enumstring-data-type-xmla"></a>Tipo di dati EnumString (XMLA)
  Definisce un tipo di dati derivato che rappresenta un set di costanti denominate per un enumeratore specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<EnumString>...</EnumString>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|`string`|  
|Tipi di dati derivati|None|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|None|  
|Elementi derivati|None|  
  
## <a name="remarks"></a>Note  
 Enumerazioni per limitare valori della stringa a un set di impostazioni verificabili sono utilizzate in XML for Analysis (XMLA). `EnumString` utilizza il tipo di dati `string` XML standard. I valori specifici per ognuna delle costanti denominate sono specificati con la definizione dell'enumeratore. Gli enumeratori sono definiti aggiungendoli al [DISCOVER_ENUMERATORS](../../schema-rowsets/xml/discover-enumerators-rowset.md) set di righe dello schema e può essere recuperato tramite il [Discover](../xml-elements-methods-discover.md) tipo di richiesta di metodo con il DISCOVER_ENUMERATORS.  
  
 Nella tabella seguente vengono descritti gli enumeratori supportati da un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
|Enumeratore|Description|  
|----------------|-----------------|  
|ProviderType|Supporta la colonna Tipoprovider nel [DISCOVER_DATASOURCES](../../schema-rowsets/xml/discover-datasources-rowset.md) set di righe dello schema, che determina il tipo di dati che possono essere restituiti da un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza.<br /><br /> Questa enumerazione supporta anche la proprietà XMLA, `ProviderType` che determina i tipi di provider supportati da un'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Questa enumerazione è utilizzata anche nel set di righe dello schema DISCOVER_DATASOURCES.<br /><br /> Per altre informazioni sulle `ProviderType`, vedere [proprietà XMLA supportate &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|ModalitàAutenticazione|Supporta la colonna ModalitàAutenticazione nel set di righe dello schema DISCOVER_DATASOURCES che determina le credenziali di sicurezza che devono essere passate per accedere a un'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|TipoAccessoProprietà|Supporta la colonna Tipoaccessoproprietà nel [DISCOVER_PROPERTIES](../../schema-rowsets/xml/discover-properties-rowset.md) set di righe dello schema, che determina il tipo di accesso disponibile per una proprietà XMLA.|  
|SupportoStato|Supporta la proprietà XMLA, `StateSupport`, che determina il livello di statefulness supportato da un'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].<br /><br /> Per altre informazioni sulle `StateSupport`, vedere [proprietà XMLA supportate &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|VerboAzioneStato|Contiene un elenco di verbi supportato da XMLA nelle intestazioni SOAP e usato per iniziare, identificare e terminare una sessione.<br /><br /> Per altre informazioni sulle sessioni, vedere [alla gestione delle connessioni e sessioni &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md).|  
|ResultsetFormat|Supporta la proprietà XMLA `Format`, che determina il tipo di dati restituiti in un [radice](../xml-elements-properties/root-element-xmla.md) elemento.<br /><br /> Per altre informazioni sulle `Format`, vedere [proprietà XMLA supportate &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|ResultsetAxisFormat|Supporta la proprietà XMLA, `AxisFormat`, che determina il formato delle informazioni dell'asse restituito in un elemento `root` che contiene dati multidimensionali.<br /><br /> Per altre informazioni sulle `AxisFormat`, vedere [proprietà XMLA supportate &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|ResultsetContents|Supporta la proprietà XMLA, `Content`, che determina se i metadati o i dati sono restituiti in un elemento `root`.<br /><br /> Per altre informazioni sulle `Content`, vedere [proprietà XMLA supportate &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|MDXSupportLevel|Supporta la proprietà XMLA, `MDXSupport`, che indica il livello di supporto delle Espressioni MDX (MDX) disponibile su un'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].<br /><br /> Per altre informazioni sulle `MDXSupport`, vedere [proprietà XMLA supportate &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati XML &#40;XMLA&#41;](xml-data-types-xmla.md)  
  
  
