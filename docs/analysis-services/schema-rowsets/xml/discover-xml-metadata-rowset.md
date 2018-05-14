---
title: Set di righe DISCOVER_XML_METADATA | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 74b0c33570c9a7f6889e9754eeac7426f72c98ac
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="discoverxmlmetadata-rowset"></a>Set di righe DISCOVER_XML_METADATA
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Restituisce un documento XML in cui viene descritto un oggetto richiesto. Il set di righe restituito è sempre costituito da una riga e una colonna.  
  
 Se si chiama il [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) metodo con il **DISCOVER_XML_METATDATA** valore di enumerazione nel [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) elemento, il **Discover**metodo restituisce il **DISCOVER_XML_METATDATA** set di righe.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il set di righe **DISCOVER_XML_METADATA** contiene la colonna seguente.  
  
|Nome colonna|Indicatore del tipo|Lunghezza|Description|  
|-----------------|--------------------|------------|-----------------|  
|**METADATA**|**DBTYPE_WSTR**||Documento XML che descrive l'oggetto richiesto dalla restrizione.|  
  
 Questo set di righe dello schema non è ordinato.  
  
> [!IMPORTANT]  
>  Non è possibile eseguire una query nel set di righe **DISCOVER_XML_METADATA** utilizzando la sintassi del comando SELECT. Tuttavia, il **DISCOVER_XML_METADATA** set di righe possono essere eseguite utilizzando <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe **DISCOVER_XML_METADATA** può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**DatabaseID**|**DBTYPE_WSTR**|Facoltativa.|  
|**DimensionID**|**DBTYPE_WSTR**|Facoltativa.|  
|**CubeID**|**DBTYPE_WSTR**|Facoltativa.|  
|**MeasureGroupID**|**DBTYPE_WSTR**|Facoltativa.|  
|**Elemento PartitionID**|**DBTYPE_WSTR**|Facoltativa.|  
|**PerspectiveID**|**DBTYPE_WSTR**|Facoltativa.|  
|**DimensionPermissionID**|**DBTYPE_WSTR**|Facoltativa.|  
|**RoleID**|**DBTYPE_WSTR**|Facoltativa.|  
|**DatabasePermissionID**|**DBTYPE_WSTR**|Facoltativa.|  
|**MiningModelID**|**DBTYPE_WSTR**|Facoltativa.|  
|**MiningModelPermissionID**|**DBTYPE_WSTR**|Facoltativa.|  
|**DataSourceID**|**DBTYPE_WSTR**|Facoltativa.|  
|**MiningStructureID**|**DBTYPE_WSTR**|Facoltativa.|  
|**AggregationDesignID**|**DBTYPE_WSTR**|Facoltativa.|  
|**TraceID**|**DBTYPE_WSTR**|Facoltativa.|  
|**MiningStructurePermissionID**|**DBTYPE_WSTR**|Facoltativa.|  
|**CubePermissionID**|**DBTYPE_WSTR**|Facoltativa.|  
|**AssemblyID**|**DBTYPE_WSTR**|Facoltativa.|  
|**MdxScriptID**|**DBTYPE_WSTR**|Facoltativa.|  
|**DataSourceViewID**|**DBTYPE_WSTR**|Facoltativa.|  
|**DataSourcePermissionID**|**DBTYPE_WSTR**|Facoltativa.|  
|**ObjectExpansion**|**DBTYPE_WSTR**|Facoltativa.|  
  
 La restrizione **ObjectExpansion**, è disponibile per ogni oggetto principale di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Il client utilizza in genere le restrizioni per descrivere gli oggetti OLAP per i quali deve essere restituita l'istruzione DDL e utilizza la restrizione **ObjectExpansion** per definire il grado di espansione nell'istruzione DDL restituita. Nella tabella seguente indica se il valore di enumerazione è consentito per [Alter elemento &#40;XMLA&#41; ](../../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md) comandi.  
  
|Valore di enumerazione|Description|  
|-----------------------|-----------------|  
|**ReferenceOnly**|Restituisce solo il nome, l'ID, il timestamp e lo stato richiesti per gli oggetti richiesti e per tutti gli oggetti principali discendenti in modo ricorsivo.|  
|**ObjectProperties**|Espande l'oggetto richiesto senza riferimenti agli oggetti contenuti, include gli oggetti contenuti subordinati espansi.|  
|**ExpandObject**|Come per *ObjectProperties*, ma restituisce inoltre il nome, l'ID e il timestamp per gli oggetti principali contenuti.|  
|**ExpandFull**|Espande completamente l'oggetto richiesto in modo ricorsivo fino alla parte inferiore di ogni oggetto contenuto.|  
  
## <a name="see-also"></a>Vedere anche  
 [XML for Analysis i rowset dello Schema](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
