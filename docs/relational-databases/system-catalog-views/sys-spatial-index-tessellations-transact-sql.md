---
title: Sys. spatial_index_tessellations (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- spatial_index_tessellations
- sys.spatial_index_tessellations_TSQL
- spatial_index_tessellations_TSQL
- sys.spatial_index_tessellations
dev_langs:
- TSQL
helpviewer_keywords:
- sys.spatial_index_tessellations catalog view
ms.assetid: 8b17a9a4-b57f-4220-8138-fc73581b1670
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: cb3c73d1baf770004cb56cebaa6034ed5091090c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysspatialindextessellations-transact-sql"></a>sys.spatial_index_tessellations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

 Rappresenta le informazioni sullo schema a mosaico e i parametri di ognuno degli indici spaziali.  
  
> [!NOTE]  
>  Per informazioni sull'implementazione dello schema a mosaico, vedere [Panoramica degli indici spaziali](../../relational-databases/spatial/spatial-indexes-overview.md).  
  

|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|object_id|**int**|ID dell'oggetto in cui è definito l'indice. Ogni (object_id, index_id) coppia è presente una voce corrispondente [spatial_indexes](../../relational-databases/system-catalog-views/sys-spatial-indexes-transact-sql.md).|  
|index_id|**int**|ID dell'indice spaziale in cui è definita la colonna indicizzata.|  
|tessellation_scheme|**sysname**|Nome dello schema a mosaico, uno di: GEOMETRY_GRID, GEOGRAPHY_GRID|  
|bounding_box_xmin|**float(53)**|Coordinata X dell'angolo inferiore sinistro del riquadro casella, uno di: NULL = non applicabile per uno schema a mosaico specifico (ad esempio GEOGRAPHY_GRID) *n* = se tessellation_scheme è GEOMETRY_GRID, il valore della coordinata x-min.                     **Nota:** le coordinate definite dai parametri del rettangolo di selezione sono interpretate per ogni oggetto in base al relativo [Spatial Reference Identifier (SRID)](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).|  
|bounding_box_ymin|**float(53)**|Coordinata Y dell'angolo inferiore sinistro del riquadro casella, uno di: NULL = non applicabile per uno schema a mosaico specifico (ad esempio GEOGRAPHY_GRID) *n* = se tessellation_scheme è GEOMETRY_GRID, il valore della coordinata y-min|  
|bounding_box_xmax|**float(53)**|Coordinata X dell'angolo superiore sinistro del riquadro casella, uno di: NULL = non applicabile per uno schema a mosaico specifico (ad esempio GEOGRAPHY_GRID) *n* = se tessellation_scheme è GEOMETRY_GRID, il valore della coordinata x-max|  
|bounding_box_ymax|**float(53)**|Coordinata Y dell'angolo superiore sinistro del riquadro casella, uno di: NULL = non applicabile per uno schema a mosaico specifico (ad esempio GEOGRAPHY_GRID) *n* = se tessellation_scheme è GEOMETRY_GRID, il valore della coordinata y-max|  
|level_1_grid|**smallint**|Densità della griglia di livello principale. Se tessellation_scheme è GEOMETRY_GRID o GEOGRAPHY_GRID, uno di: 16 = griglia 4 x 4 (bassa) 64 = 8 dalla griglia 8 (MEDIUM) 256 = 16 dalla griglia 16 (alto) NULL = non applicabile per un schema di tipo o dello schema a mosaico dell'indice spaziale.  Viene restituito NULL quando viene utilizzata la nuova suddivisione a mosaico di SQL Server 11.|  
|level_1_grid_desc|**nvarchar(60)**|Densità della griglia per la griglia di primo livello, uno di: basso Media elevata NULL = non applicabile per un schema di tipo o dello schema a mosaico dell'indice spaziale.  Viene restituito NULL quando viene utilizzata la nuova suddivisione a mosaico di SQL Server 11.|  
|level_2_grid|**smallint**|Densità della griglia di secondo livello. Se tessellation_scheme è GEOMETRY_GRID o GEOGRAPHY_GRID, uno di: 16 = griglia 4 x 4 (bassa) 64 = 8 dalla griglia 8 (MEDIUM) 256 = 16 dalla griglia 16 (alto) NULL = non applicabile per un schema di tipo o dello schema a mosaico dell'indice spaziale.  Viene restituito NULL quando viene utilizzata la nuova suddivisione a mosaico di SQL Server 11.|  
|level_2_grid_desc|**nvarchar(60)**|Densità della griglia per la griglia di livello 2 °, uno di: basso Media elevata NULL = non applicabile per un schema di tipo o dello schema a mosaico dell'indice spaziale.  Viene restituito NULL quando viene utilizzata la nuova suddivisione a mosaico di SQL Server 11.|  
|level_3_grid|**smallint**|Densità della griglia di terzo livello.   Se tessellation_scheme è GEOMETRY_GRID o GEOGRAPHY_GRID, uno di: 16 = griglia 4 x 4 (bassa) 64 = 8 dalla griglia 8 (MEDIUM) 256 = 16 dalla griglia 16 (alto) NULL = non applicabile per un schema di tipo o dello schema a mosaico dell'indice spaziale.  Viene restituito NULL quando viene utilizzata la nuova suddivisione a mosaico di SQL Server 11.|  
|level_3_grid_desc|**nvarchar(60)**|Densità della griglia per la griglia di livello 3, uno di: basso Media elevata NULL = non applicabile per un schema di tipo o dello schema a mosaico dell'indice spaziale.  Viene restituito NULL quando viene utilizzata la nuova suddivisione a mosaico di SQL Server 11.|  
|level_4_grid|**smallint**|Densità della griglia di quarto livello. Se tessellation_scheme è GEOMETRY_GRID o GEOGRAPHY_GRID, uno di: 16 = griglia 4 x 4 (bassa) 64 = 8 dalla griglia 8 (MEDIUM) 256 = 16 dalla griglia 16 (alto) NULL = non applicabile per un schema di tipo o dello schema a mosaico dell'indice spaziale.  Viene restituito NULL quando viene utilizzata la nuova suddivisione a mosaico di SQL Server 11.|  
|level_4_grid_desc|**nvarchar(60)**|Densità della griglia per la griglia di livello 4, uno di: < bassa Media elevata NULL = non applicabile per un schema di tipo o dello schema a mosaico dell'indice spaziale.  Viene restituito NULL quando viene utilizzata la nuova suddivisione a mosaico di SQL Server 11.|  
|cells_per_object|**int**|Numero di celle per oggetto spaziale, uno di: se tessellation_scheme è GEOMETRY_GRID o GEOGRAPHY_GRID, *n* = numero di celle per oggetto NULL = non applicabile per un schema di tipo o dello schema a mosaico dell'indice spaziale|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo dell'oggetto &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Panoramica degli indici spaziali](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.spatial_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-spatial-indexes-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
  
