---
title: Set di righe DBSCHEMA_CATALOGS | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 61e4de1591752919a5916d6044591bda49b14992
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34033312"
---
# <a name="dbschemacatalogs-rowset"></a>Set di righe DBSCHEMA_CATALOGS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Identifica gli attributi fisici associati a cataloghi accessibili dal sistema di gestione di database (DBMS).  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DBSCHEMA_CATALOGS** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Lunghezza|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|255|Nome del catalogo. Non può essere null.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Descrizione leggibile della tabella.|  
|**RUOLI**|**DBTYPE_WSTR**||Elenco di ruoli delimitato da virgole a cui appartiene l'utente corrente.<br /><br /> Un asterisco (\*) è incluso come ruolo se l'utente corrente è un server o amministratore del database.<br /><br /> **Nome utente** viene aggiunto alla **ruoli** se uno dei ruoli utilizza la sicurezza dinamica.|  
|**DATE_MODIFIED**|**DBTYPE_DBTIMESTAMP**||Data dell'ultima modifica apportata al catalogo.|  
  
 Il set di righe viene ordinato in base **CATALOG_NAME**.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DBSCHEMA_CATALOGS** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Facoltativo|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello Schema OLE DB](../../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)  
  
  
