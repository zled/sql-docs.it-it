---
title: Set di righe LINKEDSERVERS (OLE DB) | Documenti Microsoft
description: Set di righe LINKEDSERVERS (OLE DB)
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
- LINKEDSERVERS rowset
- enumerating data sources [OLE DB]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 43bf9dbfc63bc310b1ff9e5d7671c0b5f8e31e53
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="schema-rowsets---linkedservers-rowset"></a>Set di righe dello schema - set di righe LINKEDSERVERS
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Il **LINKEDSERVERS** set di righe enumera le origini dati dell'organizzazione che possono partecipare [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] query distribuite.  
  
 Il **LINKEDSERVERS** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Description|  
|-----------------|--------------------|-----------------|  
|SVR_NAME|DBTYPE_WSTR|Nome di un server collegato.|  
|SVR_PRODUCT|DBTYPE_WSTR|Produttore o altro nome che identifica il tipo di archivio dati rappresentato dal nome del server collegato.|  
|SVR_PROVIDERNAME|DBTYPE_WSTR|Nome descrittivo del provider OLE DB impiegato per utilizzare dati dal server.|  
|SVR_DATASOURCE|DBTYPE_WSTR|Stringa OLE DB DBPROP_INIT_DATASOURCE utilizzata per acquisire un'origine dati dal provider.|  
|SVR_PROVIDERSTRING|DBTYPE_WSTR|Valore OLE DB DBPROP_INIT_PROVIDERSTRING utilizzato per acquisire un'origine dati dal provider.|  
|SVR_LOCATION|DBTYPE_WSTR|Stringa OLE DB DBPROP_INIT_LOCATION utilizzata per acquisire un'origine dati dal provider.|  
  
 Il set di righe viene ordinato su SRV_NAME e una singola restrizione è supportata su SRV_NAME.  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto di set di righe dello schema &#40;OLE DB&#41;](../../oledb/ole-db/schema-rowset-support-ole-db.md)  
  
  
