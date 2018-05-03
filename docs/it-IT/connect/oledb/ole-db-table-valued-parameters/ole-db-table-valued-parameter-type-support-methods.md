---
title: Supporto dei tipi OLE DB parametro con valori di tabella (metodi) | Documenti Microsoft
description: Supporto tipo di parametro OLE DB Table-Valued (metodi)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-table-valued-parameters
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (methods)
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 098422b2a7fc641c9a8c98dfa6df5e6bcc6b6797
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="ole-db-table-valued-parameter-type-support-methods"></a>Supporto dei tipi di parametro con valori di tabella OLE DB (metodi)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  I parametri con valori di tabella sono supportati dai seguenti metodi OLE DB standard:  
  
|Metodo|Supporto dei parametri con valori di tabella|  
|------------|-------------------------------------|  
|ITableDefinitionWithConstraints::CreateTableWithConstraints|Utilizzato quando si conoscono le informazioni sul tipo di parametro con valori di tabella e si desidera creare un'istanza dell'oggetto set di righe di parametri con valori di tabella in base alle informazioni sul tipo.<br /><br /> Per ulteriori informazioni, vedere "Scenario statico" in [la creazione dei set di righe di parametri con valori di tabella](../../oledb/ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md).|  
|IOpenRowset::OpenRowset|Utilizzato quando non si conoscono le informazioni sul tipo di un parametro con valori di tabella e si desidera creare un'istanza dell'oggetto set di righe di parametri con valori di tabella in base alle informazioni sui metadati recuperate dal server.<br /><br /> Per ulteriori informazioni, vedere "Scenario dinamico" in [la creazione dei set di righe di parametri con valori di tabella](../../oledb/ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md).|  
|ISSCommandWithParameters::SetParameterInfo|Per specificare un parametro di comando di parametro con valori di tabella, il consumer specifica il tipo del parametro come "table" o "DBTYPE_TABLE" nel *pwszName* membro della struttura DBPARAMBINDINFO. Il *ulParamSize* è impostato su ~ 0. Per ulteriori informazioni, vedere "Specifica dei parametri con valori di tabella" in [Executing Commands Containing Table-Valued parametri](../../oledb/ole-db-table-valued-parameters/executing-commands-containing-table-valued-parameters.md).|  
|Isscommandwithparameters:: Setparameterproperties|Imposta le proprietà specifiche per i parametri con valori di tabella, ad esempio nome dello schema, nome del tipo, ordine delle colonne e colonne predefinite.<br /><br /> Il consumer specifica il numero ordinale del parametro di *iOrdinal* della struttura SSPARAMPROPS. Il set di proprietà richiesto è DBPROPSET_SQLSERVERPARAMETER.|  
|ISSCommandWithParameters::GetParameterInfo|Ottiene i tipi di tutti i parametri per un comando specificato.<br /><br /> Per i parametri con valori di tabella, la *wType* campo nella struttura DBPARAMINFO sarà necessario tipo DBTYPE_TABLE. Il *ulParamSize* campo verrà impostato su ~ 0 per indicare la lunghezza sconosciuta.|  
|Isscommandwithparameters:: Getparameterproperties|Ottiene informazioni sul tipo aggiuntive per i parametri del tipo DBTYPE_TABLE.<br /><br /> Il consumer specifica il numero ordinale del parametro di *iOrdinal* membro della struttura SSPARAMPROPS. Il consumer può richiedere qualsiasi proprietà nel set di proprietà DBPROPSET_SQLSERVERPARAMETER riportati nella sezione isscommandwithparameters:: Setparameterproperties.<br /><br /> Poiché il consumer non conosce il tipo di parametro con valori di tabella, il provider deve impostare SSPROP_PARAM_TYPE_TYPENAME, SSPROP_PARAM_TYPE_SCHEMANAME e SSPROP_PARAM_TYPE_CATALOGNAME sui valori corretti. Le proprietà restanti, SSPROP_PARAM_TABLE_DEFAULT_COLUMNS e SSPROP_PARAM_TABLE_COLUMN_SORT_ORDER, utilizzeranno i valori predefiniti. Dopo che il consumer ha individuato il nome del tipo di parametro con valori di tabella, Usa IOpenRowset:: OPENROWSET per creare un'istanza di questo parametro con valori di tabella, specificando il nome del tipo di parametro con valori di tabella. Per ulteriori informazioni, vedere [individuazione del tipo di parametro con valori di tabella](../../oledb/ole-db-table-valued-parameters/table-valued-parameter-type-discovery.md).|  
|IRowsetInfo:: GetProperties|Ottiene le proprietà del set di righe di parametri con valori di tabella. Il consumer può utilizzare queste proprietà per configurare le associazioni in modo ottimale.|  
|IColumnsRowset::GetColumnsRowset|Recupera le informazioni sui metadati relative a una tabella di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per i parametri con valori di tabella, questa stessa interfaccia fornisce informazioni dettagliate sui metadati relative a ogni colonna, ad esempio:<br /><br /> DBCOLUMN_FLAGS indica se i valori sono supportati tramite il bit DBCOLUMNFLAGS_ISNULLABLE.<br /><br /> DBCOLUMN_ISUNIQUE indica se la nuova colonna è una colonna Identity.<br /><br /> DBCOLUMN_COMPUTEMODE indica se la colonna viene calcolata.|  
|IAccessor::CreateAccessor|Per associare un oggetto set di righe di parametri con valori di tabella a un parametro di comando, si crea una funzione di accesso con il relativo *wType* membro impostato su DBTYPE_TABLE. La struttura DBOBJECT conterrà IID_IRowset o qualsiasi altra interfaccia di oggetto valido di set di righe nel *iid* membro. Il resto dei campi viene gestito in modo analogo a DBTYPE_IUNKNOWN.|  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto tipo di parametro con valori di tabella OLE DB](../../oledb/ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support.md)   
 [Creazione dei set di righe di parametri con valori di tabella](../../oledb/ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md)   
 [Utilizzare i valori di tabella parametri & #40; OLE DB & #41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
