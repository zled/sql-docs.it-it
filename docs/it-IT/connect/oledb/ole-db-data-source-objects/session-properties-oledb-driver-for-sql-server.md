---
title: Proprietà di sessione - Driver OLE DB per SQL Server | Documenti Microsoft
description: Proprietà della sessione, il Driver OLE DB per SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-data-source-objects
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sessions [OLE DB]
- OLE DB Driver for SQL Server, sessions
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 4e71e94fabae18cf938f2ab65126607405fd96f9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="session-properties---ole-db-driver-for-sql-server"></a>Proprietà di sessione - Driver OLE DB per SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Il Driver OLE DB per SQL Server interpreta le proprietà di sessione di OLE DB come indicato di seguito.  
  
|ID proprietà|Description|  
|-----------------|-----------------|  
|DBPROP_SESS_AUTOCOMMITISOLEVELS|Il Driver OLE DB per SQL Server supporta tutti i livelli di isolamento delle transazioni con autocommit ad eccezione del livello chaos DBPROPVAL_TI_CHAOS.|  
  
 Nel set di proprietà specifiche del provider DBPROPSET_SQLSERVERSESSION, il Driver OLE DB per SQL Server definisce le proprietà di sessione aggiuntive seguenti.  
  
|ID proprietà|Description|  
|-----------------|-----------------|  
|SSPROP_QUOTEDCATALOGNAMES|Tipo: VT_BOOL<br /><br /> L/S: Lettura/Scrittura<br /><br /> Impostazione predefinita: VARIANT_FALSE<br /><br /> Descrizione: gli identificatori tra virgolette consentiti nella restrizione CATALOG.<br /><br /> VARIANT_TRUE: gli identificatori tra virgolette sono riconosciuti per una restrizione per catalogo per i set di righe dello schema che forniscono il supporto query distribuito.<br /><br /> VARIANT_FALSE: gli identificatori tra virgolette non sono riconosciuti per una restrizione per catalogo per i set di righe dello schema che forniscono il supporto di query distribuite.<br /><br /> Per ulteriori informazioni sui set di righe dello schema che forniscono il supporto di query distribuite, vedere [supporto di Query distribuite nei set di righe dello Schema](../../oledb/ole-db/schema-rowsets-distributed-query-support.md).|  
|SSPROP_ALLOWNATIVEVARIANT|Tipo: VT_BOOL<br /><br /> L/S: Lettura/Scrittura<br /><br /> Impostazione predefinita: VARIANT_FALSE<br /><br /> Descrizione: determina se i dati recuperati appartengono alla categoria DBTYPE_VARIANT o DBTYPE_SQLVARIANT.<br /><br /> VARIANT_TRUE: il tipo di colonna viene restituito come DBTYPE_SQLVARIANT e in tal caso il buffer conserva la struttura SSVARIANT.<br /><br /> VARIANT_FALSE: il tipo di colonna viene restituito come DBTYPE_VARIANT e il buffer presenta la struttura VARIANT.|  
|SSPROP_ASYNCH_BULKCOPY|Per utilizzare la modalità asincrona, impostare la proprietà di sessione SSPROP_ASYNCH_BULKCOPY specifica del provider su VARIANT_TRUE prima di chiamare il metodo BCPExec. Questa proprietà è disponibile nel set di proprietà DBPROPSET_SQLSERVERSESSION.|  
  
## <a name="see-also"></a>Vedere anche  
 [Gli oggetti origine dati & #40; OLE DB & #41;](../../oledb/ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
