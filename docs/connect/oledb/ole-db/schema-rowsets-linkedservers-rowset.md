---
title: Set di righe LINKEDSERVERS (OLE DB) | Microsoft Docs
description: Set di righe LINKEDSERVERS (OLE DB)
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- LINKEDSERVERS rowset
- enumerating data sources [OLE DB]
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 9fe4ab1b6fd245bdb7ac0bd08acb0564742e1188
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47694946"
---
# <a name="schema-rowsets---linkedservers-rowset"></a>Set di righe dello schema - Set di righe LINKEDSERVERS
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Il set di righe **LINKEDSERVERS** enumera le origini dati dell'organizzazione che possono partecipare nelle query distribuite di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Il set di righe **LINKEDSERVERS** contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Descrizione|  
|-----------------|--------------------|-----------------|  
|SVR_NAME|DBTYPE_WSTR|Nome di un server collegato.|  
|SVR_PRODUCT|DBTYPE_WSTR|Produttore o altro nome che identifica il tipo di archivio dati rappresentato dal nome del server collegato.|  
|SVR_PROVIDERNAME|DBTYPE_WSTR|Nome descrittivo del provider OLE DB impiegato per utilizzare dati dal server.|  
|SVR_DATASOURCE|DBTYPE_WSTR|Stringa OLE DB DBPROP_INIT_DATASOURCE utilizzata per acquisire un'origine dati dal provider.|  
|SVR_PROVIDERSTRING|DBTYPE_WSTR|Valore OLE DB DBPROP_INIT_PROVIDERSTRING utilizzato per acquisire un'origine dati dal provider.|  
|SVR_LOCATION|DBTYPE_WSTR|Stringa OLE DB DBPROP_INIT_LOCATION utilizzata per acquisire un'origine dati dal provider.|  
  
 Il set di righe viene ordinato su SRV_NAME e una singola restrizione è supportata su SRV_NAME.  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto del set di righe dello schema &#40;OLE DB&#41;](../../oledb/ole-db/schema-rowset-support-ole-db.md)  
  
  
