---
title: Tipo di dati EnumString (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: EnumString Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- EnumString
- urn:schemas-microsoft-com:xml-analysis#EnumString
- http://schemas.microsoft.com/analysisservices/2003/engine#EnumString
helpviewer_keywords: EnumString data type
ms.assetid: 9214195e-4539-419b-95ec-b7aa75e033ab
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 4018f8cafb3daed98c05d9d59c12a0cfb1998e7a
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="enumstring-data-type-xmla"></a>Tipo di dati EnumString (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Definisce un tipo di dati derivato che rappresenta un set di costanti denominate per un enumeratore specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<EnumString>...</EnumString>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipi di dati di base|**string**|  
|Tipi di dati derivati|Nessuno|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|Nessuno|  
|Elementi figlio|Nessuno|  
|Elementi derivati|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Enumerazioni per limitare valori della stringa a un set di impostazioni verificabili sono utilizzate in XML for Analysis (XMLA). **EnumString** utilizza XML standard **stringa** tipo di dati. I valori specifici per ognuna delle costanti denominate sono specificati con la definizione dell'enumeratore. Gli enumeratori sono definiti aggiungendoli al file il [DISCOVER_ENUMERATORS](../../../analysis-services/schema-rowsets/xml/discover-enumerators-rowset.md) set di righe dello schema e può essere recuperato tramite il [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) tipo di metodo con il DISCOVER_ENUMERATORS richiesta.  
  
 Nella tabella seguente vengono descritti gli enumeratori supportati da un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
|Enumeratore|Description|  
|----------------|-----------------|  
|ProviderType|Supporta la colonna Tipoprovider nel [DISCOVER_DATASOURCES](../../../analysis-services/schema-rowsets/xml/discover-datasources-rowset.md) set di righe dello schema, che determina il tipo di dati che possono essere restituiti da un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza.<br /><br /> Questa enumerazione supporta anche la proprietà XMLA, **Tipoprovider**, che determina i tipi di provider supportati da un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza. Questa enumerazione è utilizzata anche nel set di righe dello schema DISCOVER_DATASOURCES.<br /><br /> Per ulteriori informazioni su **Tipoprovider**, vedere [supportate proprietà XMLA &#40; XMLA &#41; ](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|ModalitàAutenticazione|Supporta la colonna ModalitàAutenticazione nel set di righe dello schema DISCOVER_DATASOURCES che determina le credenziali di sicurezza che devono essere passate per accedere a un'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|TipoAccessoProprietà|Supporta la colonna Tipoaccessoproprietà nel [DISCOVER_PROPERTIES](../../../analysis-services/schema-rowsets/xml/discover-properties-rowset.md) set di righe dello schema, che determina il tipo di accesso disponibile per una proprietà XMLA.|  
|SupportoStato|Supporta la proprietà XMLA, **Supportostato**, che determina il livello di statefulness supportato da un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza.<br /><br /> Per ulteriori informazioni su **Supportostato**, vedere [supportate proprietà XMLA &#40; XMLA &#41; ](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|VerboAzioneStato|Contiene un elenco di verbi supportato da XMLA nelle intestazioni SOAP e usato per iniziare, identificare e terminare una sessione.<br /><br /> Per ulteriori informazioni sulle sessioni, vedere [alla gestione delle connessioni e sessioni &#40; XMLA &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md).|  
|ResultsetFormat|Supporta la proprietà XMLA, **formato**, che determina il tipo di dati restituiti un [radice](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) elemento.<br /><br /> Per ulteriori informazioni su **formato**, vedere [supportate proprietà XMLA &#40; XMLA &#41; ](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|ResultsetAxisFormat|Supporta la proprietà XMLA, **AxisFormat**, che determina il formato delle informazioni dell'asse restituite in un **radice** elemento che contiene dati multidimensionali.<br /><br /> Per ulteriori informazioni su **AxisFormat**, vedere [supportate proprietà XMLA &#40; XMLA &#41; ](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|ResultsetContents|Supporta la proprietà XMLA, **contenuto**, che determina se i dati o metadati vengono restituiti un **radice** elemento.<br /><br /> Per ulteriori informazioni su **contenuto**, vedere [supportate proprietà XMLA &#40; XMLA &#41; ](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|MDXSupportLevel|Supporta la proprietà XMLA, **MDXSupport**, che indica il livello di supporto MDX (Multidimensional Expressions) disponibile in un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza.<br /><br /> Per ulteriori informazioni su **MDXSupport**, vedere [supportate proprietà XMLA &#40; XMLA &#41; ](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati XML &#40; XMLA &#41;](../../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)  
  
  
