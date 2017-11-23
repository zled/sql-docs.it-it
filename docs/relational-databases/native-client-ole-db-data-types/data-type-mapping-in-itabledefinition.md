---
title: Mapping dei tipi di dati in ITableDefinition | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-data-types
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- mapping data types [OLE DB]
- SQL Server Native Client OLE DB provider, data types
- ITableDefinition interface
- DBCOLUMNDESC structure
- data types [OLE DB]
- CreateTable function
- OLE DB, data types
ms.assetid: 13292d1f-c17e-4d11-bf98-3460a10cbb18
caps.latest.revision: "35"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c9e8c3fbcce7146c2de17caa97e70a539de6a90b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="data-type-mapping-in-itabledefinition"></a>Mapping dei tipi di dati in ITableDefinition
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Quando si creano tabelle utilizzando il **itabledefinition:: CreateTable** funzione, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consumer del provider OLE DB Native Client è possibile specificare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipi di dati nel *pwszTypeName* membro della matrice DBCOLUMNDESC passata. Se il consumer specifica il tipo di dati di una colonna in base al nome, rappresentato dal mapping del tipo di dati OLE DB di *wType* membro della struttura DBCOLUMNDESC, viene ignorato.  
  
 Quando si specificano nuovi tipi di dati di colonna con tipi di dati OLE DB utilizzando la struttura DBCOLUMNDESC *wType* membro, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client esegue il mapping di tipi di dati OLE DB come indicato di seguito.  
  
|Tipo di dati OLE DB|SQL Server<br /><br /> Tipo di dati|Informazioni aggiuntive|  
|----------------------|------------------------------|----------------------------|  
|DBTYPE_BOOL|**bit**||  
|DBTYPE_BYTES|**binario**, **varbinary**, **immagine,** o **varbinary (max)**|Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client controlla il *ulColumnSize* membro della struttura DBCOLUMNDESC. In base al valore e versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client esegue il mapping per il tipo di **immagine**.<br /><br /> Se il valore di *ulColumnSize* è minore della lunghezza massima di un **binario** colonna tipo di dati, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client controlla DBCOLUMNDESC *rgPropertySets* membro. Se DBPROP_COL_FIXEDLENGTH è VARIANT_TRUE, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client esegue il mapping di tipo per **binario**. Se il valore della proprietà è VARIANT_FALSE, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client esegue il mapping di tipo per **varbinary**. In entrambi i casi, DBCOLUMNDESC *ulColumnSize* determina la larghezza della colonna di SQL Server creata.|  
|DBTYPE_CY|**money**||  
|DBTYPE_DBTIMESTAMP|**datetime**||  
|DBTYPE_GUID|**uniqueidentifier**||  
|DBTYPE_I2|**smallint**||  
|DBTYPE_I4|**int**||  
|DBTYPE_NUMERIC|**numeric**|Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client controlla il DBCOLUMDESC *bPrecision* e *bScale* membri per determinare la precisione e scala per il **numerico** colonna.|  
|DBTYPE_R4|**real**||  
|DBTYPE_R8|**float**||  
|DBTYPE_STR|**Char**, **varchar**, **testo,** o **varchar (max)**|Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client controlla il *ulColumnSize* membro della struttura DBCOLUMNDESC. In base al valore e la versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client esegue il mapping di tipo per **testo**.<br /><br /> Se il valore di *ulColumnSize* è minore della lunghezza massima di una colonna di tipo di dati carattere multibyte, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client controlla DBCOLUMNDESC *rgPropertySets* membro. Se DBPROP_COL_FIXEDLENGTH è VARIANT_TRUE, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client esegue il mapping di tipo per **char**. Se il valore della proprietà è VARIANT_FALSE, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client esegue il mapping di tipo per **varchar**. In entrambi i casi, DBCOLUMNDESC *ulColumnSize* membro determina la larghezza del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] colonna creata.|  
|DBTYPE_UDT|**UDT**|Le seguenti informazioni vengono utilizzate **DBCOLUMNDESC** strutture da **itabledefinition:: CreateTable** quando sono necessarie colonne di tipo definito dall'utente:<br /><br /> *pwSzTypeName* viene ignorato.<br /><br /> *rgPropertySets* deve includere un **DBPROPSET_SQLSERVERCOLUMN** impostata come descritto nella sezione in **DBPROPSET_SQLSERVERCOLUMN**nella [definito dall'utente utilizzando Tipi](../../relational-databases/native-client/features/using-user-defined-types.md).|  
|DBTYPE_UI1|**tinyint**||  
|DBTYPE_WSTR|**nchar**, **nvarchar**, **ntext** o **nvarchar (max)**|Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client controlla il *ulColumnSize* membro della struttura DBCOLUMNDESC. In base al valore, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client esegue il mapping di tipo per **ntext**.<br /><br /> Se il valore di *ulColumnSize* è minore della lunghezza massima di una colonna a tipo di dati character Unicode, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client controlla DBCOLUMNDESC *rgPropertySets* membro. Se DBPROP_COL_FIXEDLENGTH è VARIANT_TRUE, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client esegue il mapping di tipo per **nchar**. Se il valore della proprietà è VARIANT_FALSE, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client esegue il mapping di tipo per **nvarchar**. In entrambi i casi, DBCOLUMNDESC *ulColumnSize* membro determina la larghezza del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] colonna creata.|  
|DBTYPE_XML|**XML**||  
  
> [!NOTE]  
>  In caso di creazione di una nuova tabella, il provider OLE DB di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client esegue il mapping solo dei valori di enumerazione del tipo di dati OLE DB specificati nella tabella precedente. Il tentativo di creare una tabella con una colonna di qualsiasi altro tipo di dati OLE DB DB genera un errore.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-data-types/data-types-ole-db.md)  
  
  
