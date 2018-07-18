---
title: Mapping dei tipi di dati in ITableDefinition | Documenti Microsoft
description: Mapping dei tipi di dati in ITableDefinition
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-data-types
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- mapping data types [OLE DB]
- OLE DB Driver for SQL Server, data types
- ITableDefinition interface
- DBCOLUMNDESC structure
- data types [OLE DB]
- CreateTable function
- OLE DB, data types
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: d613fc7be394bbf16c86c5e217e3dfe83a4296a1
ms.sourcegitcommit: e1bc8c486680e6d6929c0f5885d97d013a537149
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/15/2018
ms.locfileid: "35666351"
---
# <a name="data-type-mapping-in-itabledefinition"></a>Mapping dei tipi di dati in ITableDefinition
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Quando si creano tabelle utilizzando il **itabledefinition:: CreateTable** funzione, è possibile specificare il Driver OLE DB per il consumer di SQL Server [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipi di dati nel *pwszTypeName* membro del Matrice DBCOLUMNDESC passata. Se il consumer specifica il tipo di dati di una colonna in base al nome, rappresentato dal mapping del tipo di dati OLE DB di *wType* membro della struttura DBCOLUMNDESC, viene ignorato.  
  
 Quando si specificano nuovi tipi di dati di colonna con tipi di dati OLE DB utilizzando una struttura DBCOLUMNDESC *wType* membro, il Driver OLE DB per SQL Server esegue il mapping di tipi di dati OLE DB come indicato di seguito.  
  
|Tipo di dati OLE DB|SQL Server<br /><br /> Tipo di dati|Informazioni aggiuntive|  
|----------------------|------------------------------|----------------------------|  
|DBTYPE_BOOL|**bit**||  
|DBTYPE_BYTES|**binario**, **varbinary**, **immagine** o **varbinary (max)**|Controlla se il Driver OLE DB per SQL Server la *ulColumnSize* membro della struttura DBCOLUMNDESC. In, il valore e la versione di base il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dell'istanza, il Driver OLE DB per SQL Server esegue il mapping di tipo su cui **immagine**.<br /><br /> Se il valore di *ulColumnSize* è minore della lunghezza massima di un **binario** tipi di dati colonna, il Driver OLE DB per SQL Server analizza DBCOLUMNDESC *rgPropertySets*membro. Se DBPROP_COL_FIXEDLENGTH è VARIANT_TRUE, il Driver OLE DB per SQL Server esegue il mapping di tipo su cui **binario**. Se il valore della proprietà è VARIANT_FALSE, il Driver OLE DB per SQL Server esegue il mapping di tipo su cui **varbinary**. In entrambi i casi, DBCOLUMNDESC *ulColumnSize* determina la larghezza della colonna di SQL Server creata.|  
|DBTYPE_CY|**money**||  
|DBTYPE_DBTIMESTAMP|**datetime2**||  
|DBTYPE_GUID|**uniqueidentifier**||  
|DBTYPE_I2|**smallint**||  
|DBTYPE_I4|**int**||  
|DBTYPE_I8|**bigint**||
|DBTYPE_NUMERIC|**numeric**|Il Driver OLE DB per SQL Server controlla la DBCOLUMDESC *bPrecision* e *bScale* membri per determinare la precisione e scala per il **numerico** colonna.|  
|DBTYPE_R4|**real**||  
|DBTYPE_R8|**float**||  
|DBTYPE_STR|**Char**, **varchar**, **testo** o **varchar (max)**|Controlla se il Driver OLE DB per SQL Server la *ulColumnSize* membro della struttura DBCOLUMNDESC. In base al valore e la versione del [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dell'istanza, il Driver OLE DB per SQL Server esegue il mapping di tipo su cui **testo**.<br /><br /> Se il valore di *ulColumnSize* è minore della lunghezza massima pari a una colonna di tipo carattere multibyte, il Driver OLE DB per SQL Server analizza DBCOLUMNDESC *rgPropertySets* membro. Se DBPROP_COL_FIXEDLENGTH è VARIANT_TRUE, il Driver OLE DB per SQL Server esegue il mapping di tipo su cui **char**. Se il valore della proprietà è VARIANT_FALSE, il Driver OLE DB per SQL Server esegue il mapping di tipo su cui **varchar**. In entrambi i casi, DBCOLUMNDESC *ulColumnSize* membro determina la larghezza del [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] colonna creata.|  
|DBTYPE_UDT|**UDT**|Le seguenti informazioni vengono utilizzate **DBCOLUMNDESC** strutture da **itabledefinition:: CreateTable** quando sono necessarie colonne di tipo definito dall'utente:<br /><br /> *pwSzTypeName* viene ignorato.<br /><br /> *rgPropertySets* deve includere un **DBPROPSET_SQLSERVERCOLUMN** proprietà impostata come descritto nella sezione sul **DBPROPSET_SQLSERVERCOLUMN**in [User-Defined Type ](../../oledb/features/using-user-defined-types.md).|  
|DBTYPE_UI1|**tinyint**||  
|DBTYPE_VARIANT|**sql_variant**||
|DBTYPE_WSTR|**nchar**, **nvarchar**, **ntext** o **nvarchar (max)**|Controlla se il Driver OLE DB per SQL Server la *ulColumnSize* membro della struttura DBCOLUMNDESC. In base al valore, il Driver OLE DB per SQL Server esegue il mapping di tipo su cui **ntext**.<br /><br /> Se il valore di *ulColumnSize* è minore della lunghezza massima pari a una colonna di tipo di dati carattere Unicode, il Driver OLE DB per SQL Server analizza DBCOLUMNDESC *rgPropertySets* membro. Se DBPROP_COL_FIXEDLENGTH è VARIANT_TRUE, il Driver OLE DB per SQL Server esegue il mapping di tipo su cui **nchar**. Se il valore della proprietà è VARIANT_FALSE, il Driver OLE DB per SQL Server esegue il mapping di tipo su cui **nvarchar**. In entrambi i casi, DBCOLUMNDESC *ulColumnSize* membro determina la larghezza del [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] colonna creata.|  
|DBTYPE_XML|**XML**||  

> [!NOTE]  
>  Quando si crea una nuova tabella, il Driver OLE DB per SQL Server esegue il mapping solo OLE DB dati tipo valori di enumerazione specificati nella tabella precedente. Il tentativo di creare una tabella con una colonna di qualsiasi altro tipo di dati OLE DB DB genera un errore.  

## <a name="see-also"></a>Vedere anche  
 [Tipi di dati &#40;OLE DB&#41;](../../oledb/ole-db-data-types/data-types-ole-db.md)  
  
  
