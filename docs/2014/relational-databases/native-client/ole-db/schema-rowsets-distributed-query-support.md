---
title: Supporto delle Query nei set di righe dello Schema distribuite | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- DBPROPSET_SQLSERVERSESSION property
- schema rowsets [OLE DB]
- distributed queries [SQL Server], SQL Server Native Client OLE DB provider
- OLE DB, schema rowsets
- OLE DB rowsets, schema
- rowsets [OLE DB], schema
ms.assetid: 11354bb6-be42-4d8d-854c-42dd3dc38656
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b640761d4c88f5a6a93772e12a2249f9f88f28f5
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37419760"
---
# <a name="distributed-query-support-in-schema-rowsets"></a>Supporto di query distribuite nei set di righe dello schema
  Per supportare [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] query distribuite, il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client provider OLE DB **IDBSchemaRowset** interfaccia restituisce metadati sui server collegati.  
  
 Se la proprietà SSPROP_QUOTEDCATALOGNAMES di DBPROPSET_SQLSERVERSESSION è VARIANT_TRUE, è possibile utilizzare un identificatore tra virgolette per specificare il nome di catalogo (ad esempio "catalogo.personale"). Quando si limita l'output di set di righe dello schema dal catalogo, il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provider OLE DB Native Client riconosce un nome in due parti che contiene il nome di catalogo e server collegato. Per i set di righe dello schema nella tabella seguente, specificando un nome di catalogo in due parti *linked_server ***.*** catalogo* limita l'output al catalogo applicabile del server collegato denominato.  
  
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
>  Per limitare un set di righe dello schema a tutti i cataloghi da un server collegato, usare la sintassi *linked_server* (dove il separatore punto fa parte della specifica del nome). Questa sintassi è equivalente alla specifica di NULL come restrizione del nome di catalogo e viene utilizzata anche quando il server collegato indica un'origine dati che non supporta cataloghi.  
  
 Il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provider OLE DB Native Client definisce il set di righe dello schema LINKEDSERVERS restituendo un elenco di origini dati OLE DB registrate come server collegati.  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto di set di righe dello schema &#40;OLE DB&#41;](schema-rowset-support-ole-db.md)   
 [Set di righe LINKEDSERVERS &#40;OLE DB&#41;](schema-rowsets-linkedservers-rowset.md)  
  
  
