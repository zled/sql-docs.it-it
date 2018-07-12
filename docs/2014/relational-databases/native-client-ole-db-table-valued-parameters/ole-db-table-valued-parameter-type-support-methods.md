---
title: Supporto dei tipi OLE DB parametro con valori di tabella (metodi) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (methods)
ms.assetid: e3c2a450-8fd4-44cb-93d8-affe1b65c68e
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eebe58ccc32e7440505237730b062ff9b6056ef0
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37411220"
---
# <a name="ole-db-table-valued-parameter-type-support-methods"></a>Supporto dei tipi di parametro con valori di tabella OLE DB (metodi)
  I parametri con valori di tabella sono supportati dai seguenti metodi OLE DB standard:  
  
|Metodo|Supporto dei parametri con valori di tabella|  
|------------|-------------------------------------|  
|ITableDefinitionWithConstraints::CreateTableWithConstraints|Utilizzato quando si conoscono le informazioni sul tipo di parametro con valori di tabella e si desidera creare un'istanza dell'oggetto set di righe di parametri con valori di tabella in base alle informazioni sul tipo.<br /><br /> Per altre informazioni, vedere "Scenario statico" nella [creazione di set di righe di parametri con valori di tabella](table-valued-parameter-rowset-creation.md).|  
|IOpenRowset::OpenRowset|Utilizzato quando non si conoscono le informazioni sul tipo di un parametro con valori di tabella e si desidera creare un'istanza dell'oggetto set di righe di parametri con valori di tabella in base alle informazioni sui metadati recuperate dal server.<br /><br /> Per altre informazioni, vedere "Scenario dinamico" in [creazione di set di righe di parametri con valori di tabella](table-valued-parameter-rowset-creation.md).|  
|ISSCommandWithParameters::SetParameterInfo|Per specificare un parametro di comando di parametro con valori di tabella, il consumer specifica il tipo del parametro come "table" o "DBTYPE_TABLE" nel *pwszName* membro della struttura DBPARAMBINDINFO. Il *ulParamSize* è impostato su ~ 0. Per altre informazioni, vedere "Specifica dei parametri con valori di tabella" nella [Executing Commands Containing Table-Valued parametri](executing-commands-containing-table-valued-parameters.md).|  
|Isscommandwithparameters:: Setparameterproperties|Imposta le proprietà specifiche per i parametri con valori di tabella, ad esempio nome dello schema, nome del tipo, ordine delle colonne e colonne predefinite.<br /><br /> Il consumer specifica il numero ordinale del parametro nel *iOrdinal* della struttura SSPARAMPROPS. Il set di proprietà richiesto è DBPROPSET_SQLSERVERPARAMETER.|  
|ISSCommandWithParameters::GetParameterInfo|Ottiene i tipi di tutti i parametri per un comando specificato.<br /><br /> Per i parametri con valori di tabella, la *wType* campo nella struttura DBPARAMINFO sarà DBTYPE_TABLE di tipo. Il *ulParamSize* campo verrà impostato su ~ 0 per indicare lunghezza sconosciuto.|  
|Isscommandwithparameters:: Getparameterproperties|Ottiene informazioni sul tipo aggiuntive per i parametri del tipo DBTYPE_TABLE.<br /><br /> Il consumer specifica il numero ordinale del parametro nel *iOrdinal* membro della struttura SSPARAMPROPS. Il consumer può richiedere qualsiasi proprietà nel set di proprietà DBPROPSET_SQLSERVERPARAMETER che sono elencate sotto isscommandwithparameters:: Setparameterproperties.<br /><br /> Poiché il consumer non conosce il tipo di parametro con valori di tabella, il provider deve impostare SSPROP_PARAM_TYPE_TYPENAME, SSPROP_PARAM_TYPE_SCHEMANAME e SSPROP_PARAM_TYPE_CATALOGNAME sui valori corretti. Le proprietà restanti, SSPROP_PARAM_TABLE_DEFAULT_COLUMNS e SSPROP_PARAM_TABLE_COLUMN_SORT_ORDER, utilizzeranno i valori predefiniti. Dopo che il consumer ha individuato il nome del tipo di parametro con valori di tabella, Usa IOpenRowset:: OPENROWSET per creare un'istanza di questo parametro con valori di tabella, specificando il nome del tipo di parametro con valori di tabella. Per altre informazioni, vedere [individuazione del tipo di parametro con valori di tabella](../../database-engine/dev-guide/table-valued-parameter-type-discovery.md).|  
|IRowsetInfo:: GetProperties|Ottiene le proprietà del set di righe di parametri con valori di tabella. Il consumer può utilizzare queste proprietà per configurare le associazioni in modo ottimale.|  
|IColumnsRowset::GetColumnsRowset|Recupera le informazioni sui metadati relative a una tabella di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per i parametri con valori di tabella, questa stessa interfaccia fornisce informazioni dettagliate sui metadati relative a ogni colonna, ad esempio:<br /><br /> -DBCOLUMN_FLAGS indica se i valori tramite il bit DBCOLUMNFLAGS_ISNULLABLE.<br />-DBCOLUMN_ISUNIQUE indica se la colonna è una colonna identity.<br />-DBCOLUMN_COMPUTEMODE indica se la colonna è calcolata.|  
|IAccessor::CreateAccessor|Per associare un oggetto set di righe di parametri con valori di tabella a un parametro del comando, si crea una funzione di accesso con relativi *wType* membro impostato su DBTYPE_TABLE. La struttura DBOBJECT conterrà IID_IRowset o su qualsiasi altra interfaccia di oggetto valido del set di righe nel *iid* membro. Il resto dei campi viene gestito in modo analogo a DBTYPE_IUNKNOWN.|  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto dei tipi di parametro con valori di tabella OLE DB](ole-db-table-valued-parameter-type-support.md)   
 [Creazione di set di righe di parametri con valori di tabella](table-valued-parameter-rowset-creation.md)   
 [Usare parametri con valori di tabella &#40;OLE DB&#41;](table-valued-parameters-ole-db.md)  
  
  
