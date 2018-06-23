---
title: Set di righe DBSCHEMA_TABLES | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DBSCHEMA_TABLES
topic_type:
- apiref
helpviewer_keywords:
- DBSCHEMA_TABLES rowset
ms.assetid: 14c16e6b-0aff-4ad1-b98f-cdb7df0f8d73
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 9033dc2f48b74bc13268d06f66a084f4ada22cfc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36077875"
---
# <a name="dbschematables-rowset"></a>Set di righe DBSCHEMA_TABLES
  Identifica i gruppi di misure e le dimensioni esposte come tabelle all'interno [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DBSCHEMA_TABLES` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`TABLE_CATALOG`|`DBTYPE_WSTR`|255|Nome del catalogo a cui appartiene l'oggetto.|  
|`TABLE_SCHEMA`|`DBTYPE_WSTR`|255|Nome del cubo a cui appartiene l'oggetto.|  
|`TABLE_NAME`|`DBTYPE_WSTR`|255|Nome dell'oggetto, se `TABLE_TYPE` è `TABLE`.|  
|`TABLE_TYPE`|`DBTYPE_WSTR`||Tipo della tabella.<br /><br /> `TABLE` indica che l'oggetto è un gruppo di misure.<br /><br /> `SYSTEM TABLE` indica che l'oggetto è una dimensione.|  
|`TABLE_GUID`|`DBTYPE_GUID`||Non supportato.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Descrizione leggibile dell'oggetto.|  
|`TABLE_PROPID`|`DBTYPE_UI4`||Non supportato.|  
|`DATE_CREATED`|`DBTYPE_DBTIMESTAMP`||Non supportato.|  
|`DATE_MODIFIED`|`DBTYPE_DBTIMESTAMP`||Data dell'ultima modifica apportata all'oggetto.|  
|`TABLE_OLAP_TYPE`|`DBTYPE_WSTR`||Tipo OLAP dell'oggetto.<br /><br /> **MEASURE_GROUP** indica l'oggetto è un gruppo di misure.<br /><br /> `CUBE_DIMENSION` indica che l'oggetto è una dimensione.|  
  
 Il set di righe viene ordinato in base a `TABLE_TYPE`, `TABLE_CATALOG`, `TABLE_SCHEMA` e `TABLE_NAME`.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `DBSCHEMA_TABLES` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`TABLE_CATALOG`|`DBTYPE_WSTR`|Facoltativo|  
|`TABLE_SCHEMA`|`DBTYPE_WSTR`|Facoltativo|  
|`TABLE_NAME`|`DBTYPE_WSTR`|Facoltativo|  
|`TABLE_TYPE`|`DBTYPE_WSTR`|Facoltativo|  
|`TABLE_OLAP_TYPE`|`DBTYPE_WSTR`|Facoltativo|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema OLE DB](ole-db-schema-rowsets.md)  
  
  