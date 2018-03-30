---
title: Supporto FILESTREAM | Documenti Microsoft
description: Supporto di FILESTREAM nel Driver OLE DB per SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- FILESTREAM [SQL Server], OLE DB Driver for SQL Server
- OLE DB Driver for SQL Server [FILESTREAM support]
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d528a05cd30024d2ff865a99acae1a11f187dbfc
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2018
---
# <a name="filestream-support"></a>Supporto FILESTREAM
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  FILESTREAM consente di archiviare e accedere a valori binari di grandi dimensioni mediante [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] o accesso diretto al file system di Windows. Un valore binario di grandi dimensioni è un valore superiore a 2 gigabyte (GB). Per ulteriori informazioni sul supporto FILESTREAM avanzato, vedere [FILESTREAM &#40;SQL Server&#41;](../../../relational-databases/blob/filestream-sql-server.md).  
  
 Quando viene aperta una connessione al database, **@@TEXTSIZE**  verrà impostato su -1 ("unlimited"), per impostazione predefinita.  
  
 È anche possibile accedere alle colonne FILESTREAM e aggiornarle utilizzando l'API del file system di Windows.  
  
 Per altre informazioni, vedere gli argomenti seguenti:  
  
-   [Supporto FILESTREAM &#40;OLE DB&#41;](../../oledb/ole-db/filestream-support-ole-db.md)    
  
-   [Accesso ai dati FILESTREAM con OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md)  
  
## <a name="querying-for-filestream-columns"></a>Esecuzione di una query sulle colonne FILESTREAM  
 I set di righe degli schemi in OLE DB non indicano se una colonna è di tipo FILESTREAM. ITableDefinition in OLE DB non può essere utilizzato per creare una colonna FILESTREAM.    
  
 Per creare colonne FILESTREAM o per rilevare le colonne esistenti sono colonne FILESTREAM, è possibile utilizzare il **is_filestream** colonna il [Columns](../../../relational-databases/system-catalog-views/sys-columns-transact-sql.md) vista del catalogo.  
  
 Di seguito è riportato un esempio:  
  
```  
-- Create a table with a FILESTREAM column.  
CREATE TABLE Bob_01 (GuidCol1 uniqueidentifier ROWGUIDCOL NOT NULL UNIQUE DEFAULT NEWID(), IntCol2 int, varbinaryCol3 varbinary(max) FILESTREAM);  
  
-- Find FILESTREAM columns.  
SELECT name FROM sys.columns WHERE is_filestream=1;  
  
-- Determine whether a column is a FILESTREAM column.  
SELECT is_filestream FROM sys.columns WHERE name = 'varbinaryCol3' AND object_id IN (SELECT object_id FROM sys.tables WHERE name='Bob_01');  
```  
  
## <a name="down-level-compatibility"></a>Compatibilità con le versioni precedenti  
 Se il client è stato compilato utilizzando il Driver OLE DB per SQL Server e l'applicazione si connette a [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], **varbinary (max)** comportamento sarà compatibile con [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Questo significa che i dati restituiti avranno come dimensione massima 2 GB. Per valori di dimensioni superiori a 2 GB, si verificherà il troncamento e verrà restituito un avviso di "stringa dati troncamento a destra".  
  
 Quando la compatibilità con il tipo di dati è impostata su 80, il comportamento client sarà coerente con il comportamento del client legacy.  
  
 Per i client che utilizzano SQLOLEDB o altri provider rilasciati prima la [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], **varbinary (max)** verrà eseguito il mapping all'immagine.  
  
## <a name="see-also"></a>Vedere anche  
 [Driver OLE DB per la funzionalità di SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
