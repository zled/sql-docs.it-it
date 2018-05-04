---
title: Informazioni proprietà di origine dati | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-ole-db-data-source-objects
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, data source properties
- properties [OLE DB]
- data source properties [OLE DB]
- information properties [OLE DB]
- OLE DB data source properties [SQL Server Native Client]
ms.assetid: 7fd80e47-5bd9-41e2-a3d3-091a7c8c5f2b
caps.latest.revision: 37
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: dc0a6a54e09879df19efc1e78508120d5879a2ba
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="data-source-information-properties"></a>Proprietà delle informazioni sulle origini dati
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Nel set di proprietà DBPROPSET_SQLSERVERDATASOURCEINFO specifico del provider il provider OLE DB di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client definisce le seguenti proprietà delle informazioni sulle origini dati.  
  
|ID proprietà|Description|  
|-----------------|-----------------|  
|SSPROP_COLUMNLEVELCOLLATION|Tipo: VT_BOOL<br /><br /> L/S: Lettura<br /><br /> Impostazione predefinita: VARIANT_TRUE<br /><br /> Descrizione: utilizzato per determinare se le regole di confronto a livello di colonna sono supportate.<br /><br /> VARIANT_TRUE: le regole di confronto a livello di colonna sono supportate.<br /><br /> VARIANT_FALSE: le regole di confronto a livello di colonna non sono supportate.|  
|SSPROP_UNICODELCID|Tipo: VT_I4 L/S: Lettura<br /><br /> Descrizione: ID delle impostazioni locali Unicode.<br /><br /> Si tratta delle impostazioni locali utilizzate per l'ordinamento dei dati Unicode.|  
|SSPROP_UNICODECOMPARISONSTYLE|Tipo: VT_I4 L/S: Lettura<br /><br /> Descrizione: stile di confronto Unicode.<br /><br /> Opzioni di ordinamento utilizzate per l'ordinamento dei dati Unicode.|  
  
 Nel set di proprietà DBPROPSET_SQLSERVERSTREAM specifico del provider il provider OLE DB di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client definisce le proprietà di sessione aggiuntive indicate di seguito.  
  
|ID proprietà|Description|  
|-----------------|-----------------|  
|SSPROP_STREAM_XMLROOT|Tipo: VT_BSTR L/S: Lettura/Scrittura<br /><br /> Descrizione: il risultato di una query FOR XML potrebbe non essere un documento corretto. Quando questa proprietà viene specificata, il risultato di un ' Seleziona... for XML' viene eseguito il wrapping di query nel tag radice fornito da questa proprietà per restituire un documento XML ben formato. Se la query viene eseguita nel browser, è possibile che nel browser stesso vengano visualizzati errori del parser durante il caricamento del risultato. Per evitare l'errore, SQL ISAPI supporta la parola chiave ROOT che viene mappata alla proprietà SSPROP_STREAM_XMLROOT.|  
  
## <a name="see-also"></a>Vedere anche  
 [Gli oggetti origine dati & #40; OLE DB & #41;](../../relational-databases/native-client-ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
