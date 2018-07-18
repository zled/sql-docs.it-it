---
title: Set di righe DBSCHEMA_CATALOGS | Microsoft Docs
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
- DBSCHEMA_CATALOGS
topic_type:
- apiref
helpviewer_keywords:
- DBSCHEMA_CATALOGS rowset
ms.assetid: f02dc75d-5442-4eea-b33a-567dc816be7a
caps.latest.revision: 31
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b2151d55ce06a8111ab1707e5673ee6d6982ef05
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37187048"
---
# <a name="dbschemacatalogs-rowset"></a>Set di righe DBSCHEMA_CATALOGS
  Identifica gli attributi fisici associati a cataloghi accessibili dal sistema di gestione di database (DBMS).  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DBSCHEMA_CATALOGS` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|255|Nome del catalogo. Non può essere null.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Descrizione leggibile della tabella.|  
|`ROLES`|`DBTYPE_WSTR`||Elenco di ruoli delimitato da virgole a cui appartiene l'utente corrente.<br /><br /> Un asterisco (\*) è incluso come ruolo se l'utente corrente è un server o un amministratore del database.<br /><br /> `Username` viene aggiunto a `ROLES` se uno dei ruoli utilizza la sicurezza dinamica.|  
|`DATE_MODIFIED`|`DBTYPE_DBTIMESTAMP`||Data dell'ultima modifica apportata al catalogo.|  
  
 Il set di righe viene ordinato in base a `CATALOG_NAME`.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `DBSCHEMA_CATALOGS` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Facoltativo|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema OLE DB](ole-db-schema-rowsets.md)  
  
  
