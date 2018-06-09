---
title: Tipo di dati EnumString (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a795b4cf935f7eae8052c52a3527005f362b533c
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34573803"
---
# <a name="enumstring-data-type-xmla"></a>Tipo di dati EnumString (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Definisce un tipo di dati derivato che rappresenta un set di costanti denominate per un enumeratore specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<EnumString>...</EnumString>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|**string**|  
|Tipi di dati derivati|None|  
  
## <a name="data-type-relationships"></a>Relazioni tra tipi di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|None|  
|Elementi derivati|None|  
  
## <a name="remarks"></a>Remarks  
 Enumerazioni per limitare valori della stringa a un set di impostazioni verificabili sono utilizzate in XML for Analysis (XMLA). **EnumString** utilizza XML standard **stringa** tipo di dati. I valori specifici per ognuna delle costanti denominate sono specificati con la definizione dell'enumeratore. Gli enumeratori sono definiti aggiungendoli al file il [DISCOVER_ENUMERATORS](../../../analysis-services/schema-rowsets/xml/discover-enumerators-rowset.md) set di righe dello schema e può essere recuperato tramite il [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) tipo di metodo con il DISCOVER_ENUMERATORS richiesta.  
  
 Nella tabella seguente vengono descritti gli enumeratori supportati da un'istanza di Analysis Services.  
  
|Enumeratore|Description|  
|----------------|-----------------|  
|ProviderType|Supporta la colonna Tipoprovider nel [DISCOVER_DATASOURCES](../../../analysis-services/schema-rowsets/xml/discover-datasources-rowset.md) set di righe dello schema, che determina il tipo di dati che possono essere restituiti da un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza.<br /><br /> Questa enumerazione supporta anche la proprietà XMLA, **Tipoprovider**, che determina i tipi di provider supportati da un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza. Questa enumerazione è utilizzata anche nel set di righe dello schema DISCOVER_DATASOURCES.<br /><br /> Per ulteriori informazioni **Tipoprovider**, vedere [proprietà XMLA supportate &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|ModalitàAutenticazione|Supporta la colonna ModalitàAutenticazione nel set di righe dello schema DISCOVER_DATASOURCES che determina le credenziali di sicurezza che devono essere passate per accedere a un'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|TipoAccessoProprietà|Supporta la colonna Tipoaccessoproprietà nel [DISCOVER_PROPERTIES](../../../analysis-services/schema-rowsets/xml/discover-properties-rowset.md) set di righe dello schema, che determina il tipo di accesso disponibile per una proprietà XMLA.|  
|SupportoStato|Supporta la proprietà XMLA, **Supportostato**, che determina il livello di statefulness supportato da un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza.<br /><br /> Per ulteriori informazioni **Supportostato**, vedere [proprietà XMLA supportate &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|VerboAzioneStato|Contiene un elenco di verbi supportato da XMLA nelle intestazioni SOAP e usato per iniziare, identificare e terminare una sessione.<br /><br /> Per ulteriori informazioni sulle sessioni, vedere [gestione delle connessioni e sessioni &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md).|  
|ResultsetFormat|Supporta la proprietà XMLA, **formato**, che determina il tipo di dati restituiti un [radice](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) elemento.<br /><br /> Per ulteriori informazioni **formato**, vedere [proprietà XMLA supportate &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|ResultsetAxisFormat|Supporta la proprietà XMLA, **AxisFormat**, che determina il formato delle informazioni dell'asse restituite in un **radice** elemento che contiene dati multidimensionali.<br /><br /> Per ulteriori informazioni **AxisFormat**, vedere [proprietà XMLA supportate &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|ResultsetContents|Supporta la proprietà XMLA, **contenuto**, che determina se i dati o metadati vengono restituiti un **radice** elemento.<br /><br /> Per ulteriori informazioni **contenuto**, vedere [proprietà XMLA supportate &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|MDXSupportLevel|Supporta la proprietà XMLA, **MDXSupport**, che indica il livello di supporto MDX (Multidimensional Expressions) disponibile in un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza.<br /><br /> Per ulteriori informazioni **MDXSupport**, vedere [proprietà XMLA supportate &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
  
## <a name="see-also"></a>Vedere anche
 [Tipi di dati XML &#40;XMLA&#41;](../../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)  
  
  
