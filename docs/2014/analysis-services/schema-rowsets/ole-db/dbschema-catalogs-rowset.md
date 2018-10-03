---
title: Set di righe DBSCHEMA_CATALOGS | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DBSCHEMA_CATALOGS
topic_type:
- apiref
helpviewer_keywords:
- DBSCHEMA_CATALOGS rowset
ms.assetid: f02dc75d-5442-4eea-b33a-567dc816be7a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f9c503d60de405836d90938caa6bff10f96378a1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48163231"
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
  
  
