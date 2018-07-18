---
title: Mapping dei tipi di dati in set di righe e parametri | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- mapping data types [OLE DB]
- DBTYPE_SQLVARIANT data type
- SQL Server Native Client OLE DB provider, data types
- rowsets [OLE DB], data type mapping
- data types [OLE DB]
- GetColumnInfo function
- parameters [OLE DB]
- SSPROP_ALLOWNATIVEVARIANT property
- GetParameterInfo function
- OLE DB, data types
ms.assetid: 3d831ff8-3b79-4698-b2c1-2b5dd2f8235c
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: ea9322153c59e3d83e07504236df82b0aa7b3272
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37413960"
---
# <a name="data-type-mapping-in-rowsets-and-parameters"></a>Mapping dei tipi di dati in set di righe e parametri
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Nei set di righe e come valori di parametro, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client rappresenta [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i dati usando l'esempio OLE DB definiti tipi di dati, registrati nelle funzioni **IColumnsInfo:: GetColumnInfo** e **ICommandWithParameters:: GetParameterInfo**.  
  
|Tipo di dati di SQL Server|Tipo di dati OLE DB|  
|--------------------------|----------------------|  
|**bigint**|DBTYPE_I8|  
|**binary**|DBTYPE_BYTES|  
|**bit**|DBTYPE_BOOL|  
|**char**|DBTYPE_STR|  
|**datetime**|DBTYPE_DBTIMESTAMP|  
|**datetime2**|DBTYPE_DBTIME2|  
|**decimal**|DBTYPE_NUMERIC|  
|**float**|DBTYPE_R8|  
|**image**|DBTYPE_BYTES|  
|**int**|DBTYPE_I4|  
|**money**|DBTYPE_CY|  
|**nchar**|DBTYPE_WSTR|  
|**ntext**|DBTYPE_WSTR|  
|**numeric**|DBTYPE_NUMERIC|  
|**nvarchar**|DBTYPE_WSTR|  
|**real**|DBTYPE_R4|  
|**smalldatetime**|DBTYPE_DBTIMESTAMP|  
|**smallint**|DBTYPE_I2|  
|**smallmoney**|DBTYPE_CY|  
|**sql_variant**|DBTYPE_VARIANT, DBTYPE_SQLVARIANT|  
|**sysname**|DBTYPE_WSTR|  
|**text**|DBTYPE_STR|  
|**timestamp**|DBTYPE_BYTES|  
|**tinyint**|DBTYPE_UI1|  
|**UDT**|DBTYPE_UDT|  
|**uniqueidentifier**|DBTYPE_GUID|  
|**varbinary**|DBTYPE_BYTES|  
|**varchar**|DBTYPE_STR|  
|**XML**|DBTYPE_XML|  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client supporta le conversioni di dati richieste dal consumer, come illustrato nella figura.  
  
 Il **sql_variant** gli oggetti possono contenere dati di qualsiasi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] del tipo di dati, ad eccezione di text, ntext, image, varchar (max), nvarchar (max), varbinary (max), xml, timestamp e Microsoft .NET Framework common language runtime (CLR) tipi definiti dall'utente. Per un'istanza di dati sql_variant, inoltre, il tipo di dati di base sottostante non può corrispondere a sql_variant. Ad esempio, la colonna può contenere **smallint** i valori per alcune righe **float** valori per le altre righe, e **char**/**nchar**i valori nella parte restante.  
  
> [!NOTE]  
>  Il **sql_variant** tipo di dati è simile al tipo di dati Variant in Microsoft Visual Basic® e ai tipi DBTYPE_VARIANT e DBTYPE_SQLVARIANT di OLE DB.  
  
 Quando **sql_variant** i dati vengono recuperati come DBTYPE_VARIANT, vengono inseriti in una struttura VARIANT nel buffer. Tuttavia i sottotipi presenti nella struttura VARIANT non possono eseguire il mapping a sottotipi definiti nel **sql_variant** tipo di dati. Il **sql_variant** dati vengano quindi recuperati come DBTYPE_SQLVARIANT affinché tutti i sottotipi in modo che corrispondano.  
  
## <a name="dbtypesqlvariant-data-type"></a>Tipo di dati DBTYPE_SQLVARIANT  
 Per supportare le **sql_variant** tipo di dati, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client espone un tipo di dati specifico del provider denominato DBTYPE_SQLVARIANT. Quando **sql_variant** i dati vengono recuperati come DBTYPE_SQLVARIANT, vengono archiviati in una struttura SSVARIANT specifica del provider. La struttura SSVARIANT contiene tutti i sottotipi che corrispondono ai sottotipi del **sql_variant** tipo di dati.  
  
 La proprietà di sessione SSPROP_ALLOWNATIVEVARIANT deve essere inoltre impostata su TRUE.  
  
## <a name="provider-specific-property-sspropallownativevariant"></a>Proprietà SSPROP_ALLOWNATIVEVARIANT specifica del provider  
 Durante il recupero dei dati è possibile specificare in modo esplicito il tipo di dati da restituire per una colonna o un parametro. **IColumnsInfo** è anche utilizzabile per ottenere le informazioni di colonna e usarla per eseguire il binding. Quando **IColumnsInfo** viene usato per ottenere informazioni sulla colonna a scopo di associazione, se la sessione SSPROP_ALLOWNATIVEVARIANT è FALSE (valore predefinito), viene restituito DBTYPE_VARIANT per **sql_variant**colonne. Se la proprietà SSPROP_ALLOWNATIVEVARIANT è FALSE, DBTYPE_SQLVARIANT non è supportato. Se la proprietà SSPROP_ALLOWNATIVEVARIANT è impostata su TRUE, il tipo di colonna viene restituito come DBTYPE_SQLVARIANT, nel qual caso il buffer conterrà la struttura SSVARIANT. Durante il recupero dei **sql_variant** dati come DBTYPE_SQLVARIANT, la proprietà di sessione SSPROP_ALLOWNATIVEVARIANT deve essere impostata su TRUE.  
  
 La proprietà SSPROP_ALLOWNATIVEVARIANT fa parte del set di proprietà DBPROPSET_SQLSERVERSESSION specifico del provider ed è una proprietà di sessione.  
  
 La proprietà DBTYPE_VARIANT si applica a tutti gli altri provider OLE DB.  
  
## <a name="sspropallownativevariant"></a>SSPROP_ALLOWNATIVEVARIANT  
 La proprietà SSPROP_ALLOWNATIVEVARIANT è una proprietà di sessione e fa parte del set di proprietà DBPROPSET_SQLSERVERSESSION.  
  
|||  
|-|-|  
|SSPROP_ALLOWNATIVEVARIANT|Tipo: VT_BOOL<br /><br /> L/S: Lettura/Scrittura<br /><br /> Impostazione predefinita: VARIANT_FALSE<br /><br /> Descrizione: determina se i dati recuperati appartengono alla categoria DBTYPE_VARIANT o DBTYPE_SQLVARIANT.<br /><br /> VARIANT_TRUE: il tipo di colonna viene restituito come DBTYPE_SQLVARIANT e in tal caso il buffer conserva la struttura SSVARIANT.<br /><br /> VARIANT_FALSE: il tipo di colonna viene restituito come DBTYPE_VARIANT e il buffer presenta la struttura VARIANT.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-types/data-types-ole-db.md)  
  
  
