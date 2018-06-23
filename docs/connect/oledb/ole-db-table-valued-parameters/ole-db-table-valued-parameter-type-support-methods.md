---
title: Supporto dei tipi OLE DB parametro con valori di tabella (metodi) | Documenti Microsoft
description: Supporto tipo di parametro OLE DB Table-Valued (metodi)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-table-valued-parameters
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (methods)
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 1f2b05fb6856544413ee2fb48251621880e94193
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/16/2018
ms.locfileid: "35690334"
---
# <a name="ole-db-table-valued-parameter-type-support-methods"></a>Supporto dei tipi di parametro con valori di tabella OLE DB (metodi)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  I parametri con valori di tabella sono supportati dai seguenti metodi OLE DB standard:  
  
|Metodo|Supporto dei parametri con valori di tabella|  
|------------|-------------------------------------|  
|ITableDefinitionWithConstraints::CreateTableWithConstraints|Utilizzato quando si conoscono le informazioni sul tipo di parametro con valori di tabella e si desidera creare un'istanza dell'oggetto set di righe di parametri con valori di tabella in base alle informazioni sul tipo.<br /><br /> Per altre informazioni, vedere "Scenario statico" nella [la creazione dei set di righe di parametri con valori di tabella](../../oledb/ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md).|  
|IOpenRowset::OpenRowset|Utilizzato quando non si conoscono le informazioni sul tipo di un parametro con valori di tabella e si desidera creare un'istanza dell'oggetto set di righe di parametri con valori di tabella in base alle informazioni sui metadati recuperate dal server.<br /><br /> Per altre informazioni, vedere "Scenario dinamico" in [la creazione dei set di righe di parametri con valori di tabella](../../oledb/ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md).|  
|ISSCommandWithParameters::SetParameterInfo|Per specificare un parametro di comando di parametro con valori di tabella, il consumer specifica il tipo del parametro come "table" o "DBTYPE_TABLE" nel *pwszName* membro della struttura DBPARAMBINDINFO. Il *ulParamSize* è impostato su ~ 0. Per altre informazioni, vedere "Specifica dei parametri con valori di tabella" nella [Executing Commands Containing Table-Valued parametri](../../oledb/ole-db-table-valued-parameters/executing-commands-containing-table-valued-parameters.md).|  
|Isscommandwithparameters:: Setparameterproperties|Imposta le proprietà specifiche per i parametri con valori di tabella, ad esempio nome dello schema, nome del tipo, ordine delle colonne e colonne predefinite.<br /><br /> Il consumer specifica il numero ordinale del parametro nel *iOrdinal* della struttura SSPARAMPROPS. Il set di proprietà richiesto è DBPROPSET_SQLSERVERPARAMETER.|  
|ISSCommandWithParameters::GetParameterInfo|Ottiene i tipi di tutti i parametri per un comando specificato.<br /><br /> Per i parametri con valori di tabella, la *wType* campo nella struttura DBPARAMINFO sarà DBTYPE_TABLE di tipo. Il *ulParamSize* campo verrà impostato su ~ 0 per indicare lunghezza sconosciuto.|  
|Isscommandwithparameters:: Getparameterproperties|Ottiene informazioni sul tipo aggiuntive per i parametri del tipo DBTYPE_TABLE.<br /><br /> Il consumer specifica il numero ordinale del parametro nel *iOrdinal* membro della struttura SSPARAMPROPS. Il consumer può richiedere qualsiasi proprietà nel set di proprietà DBPROPSET_SQLSERVERPARAMETER che sono elencate sotto isscommandwithparameters:: Setparameterproperties.<br /><br /> Poiché il consumer non conosce il tipo di parametro con valori di tabella, il provider deve impostare SSPROP_PARAM_TYPE_TYPENAME, SSPROP_PARAM_TYPE_SCHEMANAME e SSPROP_PARAM_TYPE_CATALOGNAME sui valori corretti. Le proprietà restanti, SSPROP_PARAM_TABLE_DEFAULT_COLUMNS e SSPROP_PARAM_TABLE_COLUMN_SORT_ORDER, utilizzeranno i valori predefiniti. Dopo che il consumer ha individuato il nome del tipo di parametro con valori di tabella, Usa IOpenRowset:: OPENROWSET per creare un'istanza di questo parametro con valori di tabella, specificando il nome del tipo di parametro con valori di tabella. Per altre informazioni, vedere [individuazione del tipo di parametro con valori di tabella](../../oledb/ole-db-table-valued-parameters/table-valued-parameter-type-discovery.md).|  
|IRowsetInfo:: GetProperties|Ottiene le proprietà del set di righe di parametri con valori di tabella. Il consumer può utilizzare queste proprietà per configurare le associazioni in modo ottimale.|  
|IColumnsRowset::GetColumnsRowset|Recupera le informazioni sui metadati relative a una tabella di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per i parametri con valori di tabella, questa stessa interfaccia fornisce informazioni dettagliate sui metadati relative a ogni colonna, ad esempio:<br /><br /> DBCOLUMN_FLAGS indica se i valori sono supportati tramite il bit DBCOLUMNFLAGS_ISNULLABLE.<br /><br /> DBCOLUMN_ISUNIQUE indica se la nuova colonna è una colonna Identity.<br /><br /> DBCOLUMN_COMPUTEMODE indica se la colonna viene calcolata.|  
|IAccessor::CreateAccessor|Per associare un oggetto set di righe di parametri con valori di tabella a un parametro di comando, si crea una funzione di accesso con il relativo *wType* membro impostato su DBTYPE_TABLE. Struttura DBOBJECT conterrà IID_IRowset o qualsiasi altra interfaccia di oggetto set di righe valida nel *iid* membro. Il resto dei campi viene gestito in modo analogo a DBTYPE_IUNKNOWN.|  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto tipo di parametro con valori di tabella OLE DB](../../oledb/ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support.md)   
 [Creazione dei set di righe di parametri con valori di tabella](../../oledb/ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md)   
 [Utilizzare parametri con valori di tabella &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
