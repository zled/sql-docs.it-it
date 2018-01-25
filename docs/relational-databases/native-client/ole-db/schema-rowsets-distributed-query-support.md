---
title: Supporto delle Query nei set di righe dello Schema distribuite | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- DBPROPSET_SQLSERVERSESSION property
- schema rowsets [OLE DB]
- distributed queries [SQL Server], SQL Server Native Client OLE DB provider
- OLE DB, schema rowsets
- OLE DB rowsets, schema
- rowsets [OLE DB], schema
ms.assetid: 11354bb6-be42-4d8d-854c-42dd3dc38656
caps.latest.revision: "29"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c115827f6c7efb8236c65648fb959594cbfcdc30
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="schema-rowsets---distributed-query-support"></a>Set di righe dello schema - supporto di Query distribuite
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Per supportare [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , query distribuite di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provider OLE DB Native Client **IDBSchemaRowset** interfaccia restituisce i metadati nei server collegati.  
  
 Se la proprietà SSPROP_QUOTEDCATALOGNAMES di DBPROPSET_SQLSERVERSESSION è VARIANT_TRUE, è possibile utilizzare un identificatore tra virgolette per specificare il nome di catalogo (ad esempio "catalogo.personale"). Quando si restringe l'output di set di righe dello schema dal catalogo, il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provider OLE DB Native Client riconosce un nome in due parti che contiene il nome del catalogo e del server collegato. Per i set di righe dello schema nella tabella seguente, specificando un nome di catalogo in due parti *server_collegato***.*** catalogo* limita l'output al catalogo applicabile del server collegato denominato.  
  
|Set di righe dello schema|Restrizione per catalogo|  
|-------------------|-------------------------|  
|DBSCHEMA_CATALOGS|CATALOG_NAME|  
|DBSCHEMA_COLUMNS|TABLE_CATALOG|  
|DBSCHEMA_PRIMARY_KEYS|TABLE_CATALOG|  
|DBSCHEMA_TABLES|TABLE_CATALOG|  
|DBSCHEMA_FOREIGN_KEYS|PK_TABLE_CATALOG FK_TABLE_CATALOG|  
|DBSCHEMA_INDEXES|TABLE_CATALOG|  
|DBSCHEMA_COLUMN_PRIVILEGES|TABLE_CATALOG|  
|DBSCHEMA_TABLE_PRIVILEGES|TABLE_CATALOG|  
  
> [!NOTE]  
>  Per limitare un set di righe dello schema a tutti i cataloghi da un server collegato, utilizzare la sintassi *server_collegato* (dove il separatore punto fa parte della specifica del nome). Questa sintassi è equivalente alla specifica di NULL come restrizione del nome di catalogo e viene utilizzata anche quando il server collegato indica un'origine dati che non supporta cataloghi.  
  
 Il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provider OLE DB Native Client definisce il set di righe dello schema LINKEDSERVERS restituendo un elenco di origini dati OLE DB registrate come server collegati.  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto di set di righe dello schema &#40; OLE DB &#41;](../../../relational-databases/native-client/ole-db/schema-rowset-support-ole-db.md)   
 [Set di righe LINKEDSERVERS &#40; OLE DB &#41;](../../../relational-databases/native-client/ole-db/schema-rowsets-linkedservers-rowset.md)  
  
  
