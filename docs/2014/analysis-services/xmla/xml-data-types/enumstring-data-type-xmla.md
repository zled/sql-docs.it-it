---
title: Tipo di dati EnumString (XMLA) | Documenti Microsoft
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
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 034ebe0218a8effece3aee526f9920850a7df536
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36158059"
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
  
## <a name="remarks"></a>Remarks  
 Enumerazioni per limitare valori della stringa a un set di impostazioni verificabili sono utilizzate in XML for Analysis (XMLA). `EnumString` utilizza il tipo di dati `string` XML standard. I valori specifici per ognuna delle costanti denominate sono specificati con la definizione dell'enumeratore. Gli enumeratori sono definiti aggiungendoli alla [DISCOVER_ENUMERATORS](../../schema-rowsets/xml/discover-enumerators-rowset.md) set di righe dello schema e può essere recuperato tramite il [Discover](../xml-elements-methods-discover.md) tipo di metodo con il DISCOVER_ENUMERATORS richiesta.  
  
 Nella tabella seguente vengono descritti gli enumeratori supportati da un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
|Enumeratore|Description|  
|----------------|-----------------|  
|ProviderType|Supporta la colonna Tipoprovider nel [DISCOVER_DATASOURCES](../../schema-rowsets/xml/discover-datasources-rowset.md) set di righe dello schema, che determina il tipo di dati che possono essere restituiti da un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza.<br /><br /> Questa enumerazione supporta anche la proprietà XMLA, `ProviderType` che determina i tipi di provider supportati da un'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Questa enumerazione è utilizzata anche nel set di righe dello schema DISCOVER_DATASOURCES.<br /><br /> Per ulteriori informazioni `ProviderType`, vedere [proprietà XMLA supportate &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|ModalitàAutenticazione|Supporta la colonna ModalitàAutenticazione nel set di righe dello schema DISCOVER_DATASOURCES che determina le credenziali di sicurezza che devono essere passate per accedere a un'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|TipoAccessoProprietà|Supporta la colonna Tipoaccessoproprietà nel [DISCOVER_PROPERTIES](../../schema-rowsets/xml/discover-properties-rowset.md) set di righe dello schema, che determina il tipo di accesso disponibile per una proprietà XMLA.|  
|SupportoStato|Supporta la proprietà XMLA, `StateSupport`, che determina il livello di statefulness supportato da un'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].<br /><br /> Per ulteriori informazioni `StateSupport`, vedere [proprietà XMLA supportate &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|VerboAzioneStato|Contiene un elenco di verbi supportato da XMLA nelle intestazioni SOAP e usato per iniziare, identificare e terminare una sessione.<br /><br /> Per ulteriori informazioni sulle sessioni, vedere [gestione delle connessioni e sessioni &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md).|  
|ResultsetFormat|Supporta la proprietà XMLA `Format`, che determina il tipo di dati restituiti in un [radice](../xml-elements-properties/root-element-xmla.md) elemento.<br /><br /> Per ulteriori informazioni `Format`, vedere [proprietà XMLA supportate &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|ResultsetAxisFormat|Supporta la proprietà XMLA, `AxisFormat`, che determina il formato delle informazioni dell'asse restituito in un elemento `root` che contiene dati multidimensionali.<br /><br /> Per ulteriori informazioni `AxisFormat`, vedere [proprietà XMLA supportate &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|ResultsetContents|Supporta la proprietà XMLA, `Content`, che determina se i metadati o i dati sono restituiti in un elemento `root`.<br /><br /> Per ulteriori informazioni `Content`, vedere [proprietà XMLA supportate &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|MDXSupportLevel|Supporta la proprietà XMLA, `MDXSupport`, che indica il livello di supporto delle Espressioni MDX (MDX) disponibile su un'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].<br /><br /> Per ulteriori informazioni `MDXSupport`, vedere [proprietà XMLA supportate &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati XML &#40;XMLA&#41;](xml-data-types-xmla.md)  
  
  