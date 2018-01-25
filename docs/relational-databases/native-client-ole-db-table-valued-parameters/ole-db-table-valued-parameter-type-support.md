---
title: Supporto tipo di parametro con valori di tabella OLE DB | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-table-valued-parameters
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: table-valued parameters (OLE DB), API support (OLE DB)
ms.assetid: 147036a0-260e-4f81-8b3b-89209e023a32
caps.latest.revision: "22"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 84b7677ea2dea591b25f64101577b0bf51b26142
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="ole-db-table-valued-parameter-type-support"></a>Supporto del tipo di parametro con valori di tabella OLE DB
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  In questo argomento viene descritto il supporto del tipo OLE DB per i parametri con valori di tabella.  
  
## <a name="table-valued-parameter-rowset-object"></a>Oggetto set di righe di parametri con valori di tabella  
 È possibile creare un oggetto set di righe specifico per i parametri con valori di tabella. Creare l'oggetto set di righe di parametri con valori di tabella utilizzando ITableDefinitionWithConstraints::CreateTableWithConstraints o IOpenRowset:: OPENROWSET. A tale scopo, impostare il *eKind* appartenente il *pTableID* parametro su DBKIND_GUID_NAME e specificare CLSID_ROWSET_INMEMORY come il *guid* membro. Il nome del tipo di server per il parametro con valori di tabella deve essere specificato nel *pwszName* membro di *pTableID* quando si utilizza IOpenRowset:: OPENROWSET. L'oggetto set di righe di parametri con valori di tabella si comporta come un normale oggetto del provider OLE DB di SQL Server Native Client.  
  
```  
const GUID CLSID_ROWSET_TVP =   
{0xc7ef28d5, 0x7bee, 0x443f, {0x86, 0xda, 0xe3, 0x98, 0x4f, 0xcd, 0x4d, 0xf9}};  
  
CoType RowsetTVP  
{  
[mandatory] interface IAccessor;  
[mandatory] interface IColumnsInfo;  
[mandatory] interface IConvertType;  
[mandatory] interface IRowset;  
[mandatory] interface IRowsetInfo;  
[optional]  interface IColumnsRowset;  
[optional]  interface IRowsetChange;  
[optional]  interface ISupportErrorInfo;  
};  
```  
  
## <a name="dbtypetable"></a>DBTYPE_TABLE  
 Un nuovo tipo, DBTYPE_TABLE, rappresenta un tipo di tabella. Tale tipo specifica i parametri con valori di tabella nelle varie interfacce OLE DB in cui è richiesto un oggetto DBTYPE.  
  
```  
#define DBTYPE_TABLE (143)  
```  
  
 Il formato di DBTYPE_TABLE è identico a quello di DBTYPE_IUNKNOWN. Si tratta di un puntatore a un oggetto nel buffer di dati. Per una specifica completa nelle associazioni, il consumer inserisce dati nel buffer DBOBJECT, con *iid* impostato su una delle interfacce oggetto set di righe (IID_IRowset). Se non viene specificato alcun oggetto DBOBJECT nelle associazioni, verrà considerato come IID_IRowset.  
  
 Le conversioni da e verso DBTYPE_TABLE per altri tipi non sono supportate. IConvertType::CanConvert restituisce S_FALSE per la conversione non supportata per qualsiasi richiesta diversa da DBTYPE_TABLE a conversione DBTYPE_TABLE. Ciò presuppone l'uso di DBCONVERTFLAGS_PARAMETER sull'oggetto Command.  
  
## <a name="methods"></a>Metodi  
 Per informazioni sui metodi OLE DB che supportano i parametri con valori di tabella, vedere [OLE DB Table-Valued il tipo di parametro supporta &#40; Metodi &#41; ](../../relational-databases/native-client-ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-methods.md).  
  
## <a name="properties"></a>Proprietà  
 Per informazioni sulle proprietà OLE DB che supportano i parametri con valori di tabella, vedere [OLE DB Table-Valued il tipo di parametro supporta &#40; Proprietà &#41; ](../../relational-databases/native-client-ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-properties.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Table-Valued parametri &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Utilizzare i valori di tabella parametri &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
