---
title: Supporto delle Query nei set di righe dello Schema distribuite | Documenti Microsoft
description: Supporto delle query nei set di righe dello schema distribuite
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- DBPROPSET_SQLSERVERSESSION property
- schema rowsets [OLE DB]
- distributed queries [SQL Server], OLE DB Driver for SQL Server
- OLE DB, schema rowsets
- OLE DB rowsets, schema
- rowsets [OLE DB], schema
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 13d6bbef66b1230fcc33ef4f0d75f2f8f0d854a3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="schema-rowsets---distributed-query-support"></a>Set di righe dello schema - supporto di Query distribuite
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Per supportare [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] query, il Driver OLE DB per SQL Server distribuite **IDBSchemaRowset** interfaccia restituisce metadati sui server collegati.  
  
 Se la proprietà SSPROP_QUOTEDCATALOGNAMES di DBPROPSET_SQLSERVERSESSION è VARIANT_TRUE, è possibile utilizzare un identificatore tra virgolette per specificare il nome di catalogo (ad esempio "catalogo.personale"). Quando si restringe l'output di set di righe dello schema dal catalogo, il Driver OLE DB per SQL Server riconosce un nome in due parti che contiene il server collegato e il nome del catalogo. Per i set di righe dello schema nella tabella seguente, specificando un nome di catalogo in due parti *server_collegato ***.*** catalogo* limita l'output al catalogo applicabile del server collegato denominato.  
  
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
  
 Il Driver OLE DB per SQL Server definisce il set di righe dello schema LINKEDSERVERS restituendo un elenco di origini dati OLE DB registrate come server collegati.  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto di set di righe dello schema &#40;OLE DB&#41;](../../oledb/ole-db/schema-rowset-support-ole-db.md)   
 [Set di righe LINKEDSERVERS &#40;OLE DB&#41;](../../oledb/ole-db/schema-rowsets-linkedservers-rowset.md)  
  
  
