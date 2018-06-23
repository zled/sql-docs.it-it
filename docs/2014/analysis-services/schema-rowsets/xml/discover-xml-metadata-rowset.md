---
title: Set di righe DISCOVER_XML_METADATA | Documenti Microsoft
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
- DISCOVER_XML_METADATA
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_XML_METADATA rowset
ms.assetid: 0befd026-db1b-43ac-b0e6-734abb56a4b1
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 4452408b36fe50300277d0d0f8e076357403539f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169095"
---
# <a name="discoverxmlmetadata-rowset"></a>Set di righe DISCOVER_XML_METADATA
  Restituisce un documento XML in cui viene descritto un oggetto richiesto. Il set di righe restituito è sempre costituito da una riga e una colonna.  
  
 Se si chiama il [Discover](../../xmla/xml-elements-methods-discover.md) metodo con il `DISCOVER_XML_METATDATA` valore di enumerazione nel [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md) elemento, il `Discover` metodo restituisce il `DISCOVER_XML_METATDATA` set di righe.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il set di righe `DISCOVER_XML_METADATA` contiene la colonna seguente.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`METADATA`|`DBTYPE_WSTR`||Documento XML che descrive l'oggetto richiesto dalla restrizione.|  
  
 Questo set di righe dello schema non è ordinato.  
  
> [!IMPORTANT]  
>  Non è possibile eseguire una query nel set di righe `DISCOVER_XML_METADATA` utilizzando la sintassi del comando SELECT. È tuttavia possibile eseguire una query sul set di righe `DISCOVER_XML_METADATA` utilizzando <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `DISCOVER_XML_METADATA` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`DatabaseID`|`DBTYPE_WSTR`|Facoltativo.|  
|`DimensionID`|`DBTYPE_WSTR`|Facoltativo.|  
|`CubeID`|`DBTYPE_WSTR`|Facoltativo.|  
|`MeasureGroupID`|`DBTYPE_WSTR`|Facoltativo.|  
|`PartitionID`|`DBTYPE_WSTR`|Facoltativo.|  
|`PerspectiveID`|`DBTYPE_WSTR`|Facoltativo.|  
|`DimensionPermissionID`|`DBTYPE_WSTR`|Facoltativo.|  
|`RoleID`|`DBTYPE_WSTR`|Facoltativo.|  
|`DatabasePermissionID`|`DBTYPE_WSTR`|Facoltativo.|  
|`MiningModelID`|`DBTYPE_WSTR`|Facoltativo.|  
|`MiningModelPermissionID`|`DBTYPE_WSTR`|Facoltativo.|  
|`DataSourceID`|`DBTYPE_WSTR`|Facoltativo.|  
|`MiningStructureID`|`DBTYPE_WSTR`|Facoltativo.|  
|`AggregationDesignID`|`DBTYPE_WSTR`|Facoltativo.|  
|`TraceID`|`DBTYPE_WSTR`|Facoltativo.|  
|`MiningStructurePermissionID`|`DBTYPE_WSTR`|Facoltativo.|  
|`CubePermissionID`|`DBTYPE_WSTR`|Facoltativo.|  
|`AssemblyID`|`DBTYPE_WSTR`|Facoltativo.|  
|`MdxScriptID`|`DBTYPE_WSTR`|Facoltativo.|  
|`DataSourceViewID`|`DBTYPE_WSTR`|Facoltativo.|  
|`DataSourcePermissionID`|`DBTYPE_WSTR`|Facoltativo.|  
|`ObjectExpansion`|`DBTYPE_WSTR`|Facoltativo.|  
  
 La restrizione `ObjectExpansion`, è disponibile per ogni oggetto principale di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Il client utilizza in genere le restrizioni per descrivere gli oggetti OLAP per i quali deve essere restituita l'istruzione DDL e utilizza la restrizione `ObjectExpansion` per definire il grado di espansione nell'istruzione DDL restituita. Nella tabella seguente indica se il valore di enumerazione è consentito per [Alter elemento &#40;XMLA&#41; ](../../xmla/xml-elements-commands/alter-element-xmla.md) comandi.  
  
|Valore di enumerazione|Description|  
|-----------------------|-----------------|  
|`ReferenceOnly`|Restituisce solo il nome, l'ID, il timestamp e lo stato richiesti per gli oggetti richiesti e per tutti gli oggetti principali discendenti in modo ricorsivo.|  
|`ObjectProperties`|Espande l'oggetto richiesto senza riferimenti agli oggetti contenuti, include gli oggetti contenuti subordinati espansi.|  
|`ExpandObject`|Come per *ObjectProperties*, ma restituisce inoltre il nome, l'ID e il timestamp per gli oggetti principali contenuti.|  
|`ExpandFull`|Espande completamente l'oggetto richiesto in modo ricorsivo fino alla parte inferiore di ogni oggetto contenuto.|  
  
## <a name="see-also"></a>Vedere anche  
 [XML per set di righe dello schema di analisi](xml-for-analysis-schema-rowsets.md)  
  
  