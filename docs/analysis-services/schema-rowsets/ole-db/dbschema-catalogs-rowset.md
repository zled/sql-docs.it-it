---
title: Set di righe DBSCHEMA_CATALOGS | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DBSCHEMA_CATALOGS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DBSCHEMA_CATALOGS rowset
ms.assetid: f02dc75d-5442-4eea-b33a-567dc816be7a
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0632d90765112ee54de8e78a66fdefa1ff27334f
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="dbschemacatalogs-rowset"></a>Set di righe DBSCHEMA_CATALOGS
  Identifica gli attributi fisici associati a cataloghi accessibili dal sistema di gestione di database (DBMS).  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DBSCHEMA_CATALOGS** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Lunghezza|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|255|Nome del catalogo. Non può essere null.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Descrizione leggibile della tabella.|  
|**RUOLI**|**DBTYPE_WSTR**||Elenco di ruoli delimitato da virgole a cui appartiene l'utente corrente.<br /><br /> Un asterisco (\*) è incluso come ruolo se l'utente corrente è un server o amministratore del database.<br /><br /> **Nome utente** viene aggiunto al **ruoli** se uno dei ruoli utilizza la sicurezza dinamica.|  
|**DATE_MODIFIED**|**DBTYPE_DBTIMESTAMP**||Data dell'ultima modifica apportata al catalogo.|  
  
 Il set di righe viene ordinato in base **CATALOG_NAME**.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DBSCHEMA_CATALOGS** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Facoltativo|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello Schema OLE DB](../../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)  
  
  

