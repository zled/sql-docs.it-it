---
title: Tipo di dati DataSource (ASSL) | Documenti Microsoft
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
- DataSource Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- DataSource data type
ms.assetid: 05e8de8d-452d-4128-98a6-4437df227fec
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 4b30438e709f6762ae194174ae9ab2be06bfd32d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169092"
---
# <a name="datasource-data-type-assl"></a>Tipo di dati DataSource (ASSL)
  Definisce un tipo di dati primitivo astratto che rappresenta un'origine dati in un [Database](../objects/database-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DataSource>  
   <Name>...</Name>  
   <ID>...</ID>  
   <CreatedTimestamp>...</CreateTimestamp>  
   <LastSchemaUpdate>...</LastSchemaUpdate>  
   <ManagedProvider>...</ManagedProvider>  
   <ConnectionString>...</ConnectionString>  
   <ConnectionStringSecurity>...</ConnectionStringSecurity>  
   <ImpersonationInfo>...</ImpersonationInfo>  
   <Isolation>...</Isolation>  
   <MaxActiveConnections>...</MaxActiveConnections>  
   <Description>...</Description>  
   <Timeout>...</Timeout>  
   <Annotations>...</Annotations>  
   <DataSourcePermission>...</DataSourcePermission>  
</DataSource>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|None|  
|Tipi di dati derivati|[RelationalDataSource](datasource-data-type-assl.md), [OlapDataSource](olapdatasource-data-type-assl.md), [PushedDataSource](pusheddatasource-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|[Annotations](../collections/annotations-element-assl.md), [ConnectionString](../properties/connectionstring-element-assl.md), [ConnectionStringSecurity](../properties/connectionstringsecurity-element-assl.md), [CreatedTimestamp](../properties/createdtimestamp-element-assl.md), [DataSourcePermission](../collections/datasourcepermissions-element-assl.md), [Description](../properties/description-element-assl.md), [ID](../properties/id-element-assl.md), [ImpersonationInfo](../properties/impersonationinfo-element-assl.md), [Isolation](../properties/isolation-element-assl.md), [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md), [ManagedProvider](../properties/managedprovider-element-assl.md), [MaxActiveConnections](../properties/maxactiveconnections-element-assl.md), [Name](../properties/name-element-assl.md), [Timeout](../properties/timeout-element-assl.md)|  
|Elementi derivati|None|  
  
## <a name="remarks"></a>Remarks  
 Quando si definiscono associazioni out-of-line, l'elemento `Name` è facoltativo. La non obbligatorietà di un elemento `Name` consente la definizione delle origini dati all'interno dell'associazione per i cubi, partizioni e così via. Per le origini dati contenute in un elemento `Database`, `Name` è un elemento obbligatorio.  
  
 Per altre informazioni sulle origini dati, vedere [Origini dati nei modelli multidimensionali](../../multidimensional-models/data-sources-in-multidimensional-models.md).  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.DataSource>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  