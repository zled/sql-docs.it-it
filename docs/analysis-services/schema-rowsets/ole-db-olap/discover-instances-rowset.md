---
title: Set di righe DISCOVER_INSTANCES | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4143aa33cc4c09914ffb05aaccbb12f2fe64d440
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="discoverinstances-rowset"></a>Set di righe DISCOVER_INSTANCES
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Descrive le istanze nel server.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DISCOVER_INSTANCES** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Lunghezza|Description|  
|-----------------|--------------------|------------|-----------------|  
|**INSTANCE_NAME**|**DBTYPE_WSTR**||Nome dell’istanza.|  
|**INSTANCE_PORT_NUMBER**|**DBTYPE_I4**||Numero di porta su cui l'istanza resta in attesa.|  
|**INSTANCE_STATE**|**DBTYPE_I4**||Stato dell'istanza del server:<br /><br /> **Avviato**<br /><br /> **Stopped**<br /><br /> **Avvio**<br /><br /> **L'arresto**<br /><br /> **In sospeso**|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DISCOVER_INSTANCES** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**INSTANCE_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
  
## <a name="see-also"></a>Vedere anche  
 [OLE DB per OLAP i rowset dello Schema](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
