---
title: Supporto FILESTREAM | Documenti Microsoft
description: Supporto di FILESTREAM nel Driver OLE DB per SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- FILESTREAM [SQL Server], OLE DB Driver for SQL Server
- OLE DB Driver for SQL Server [FILESTREAM support]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: ffb296ea9c64890293a924c135d2674f04e216a7
ms.sourcegitcommit: 354ed9c8fac7014adb0d752518a91d8c86cdce81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/14/2018
ms.locfileid: "35611573"
---
# <a name="filestream-support"></a>Supporto FILESTREAM
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

A partire da [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], il Driver OLE DB per SQL Server supporta la caratteristica FILESTREAM avanzata. Per esempi, vedere [Filestream e OLE DB](../../oledb/ole-db-how-to/filestream/filestream-and-ole-db.md).  

FILESTREAM consente di archiviare e accedere a valori binari di grandi dimensioni mediante [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] o accesso diretto al file system di Windows. Un valore binario di grandi dimensioni è un valore superiore a 2 gigabyte (GB). Per ulteriori informazioni sul supporto FILESTREAM avanzato, vedere [FILESTREAM &#40;SQL Server&#41;](../../../relational-databases/blob/filestream-sql-server.md).  
  
Quando viene aperta una connessione al database, **@@TEXTSIZE**  verrà impostato su -1 ("unlimited"), per impostazione predefinita.  
  
È anche possibile accedere alle colonne FILESTREAM e aggiornarle utilizzando l'API del file system di Windows.  
  
Per altre informazioni, vedere [accesso ai dati FILESTREAM con OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md)  
  
## <a name="querying-for-filestream-columns"></a>Esecuzione di una query sulle colonne FILESTREAM  
I set di righe degli schemi in OLE DB non indicano se una colonna è di tipo FILESTREAM. ITableDefinition in OLE DB non può essere utilizzato per creare una colonna FILESTREAM.    
  
Per creare colonne FILESTREAM o per rilevare le colonne esistenti sono colonne FILESTREAM, è possibile utilizzare il **is_filestream** colonna il [Columns](../../../relational-databases/system-catalog-views/sys-columns-transact-sql.md) vista del catalogo.  
  
Di seguito è riportato un esempio:  
  
```sql  
-- Create a table with a FILESTREAM column.  
CREATE TABLE Bob_01 (GuidCol1 uniqueidentifier ROWGUIDCOL NOT NULL UNIQUE DEFAULT NEWID(), IntCol2 int, varbinaryCol3 varbinary(max) FILESTREAM);  
  
-- Find FILESTREAM columns.  
SELECT name FROM sys.columns WHERE is_filestream=1;  
  
-- Determine whether a column is a FILESTREAM column.  
SELECT is_filestream FROM sys.columns WHERE name = 'varbinaryCol3' AND object_id IN (SELECT object_id FROM sys.tables WHERE name='Bob_01');  
```  
  
## <a name="down-level-compatibility"></a>Compatibilità con le versioni precedenti  
Se il client è stato compilato utilizzando il Driver OLE DB per SQL Server e l'applicazione si connette a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]), quindi **varbinary (max)** comportamento sarà compatibile con il comportamento dovuti [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Questo significa che i dati restituiti avranno come dimensione massima 2 GB. Per valori di dimensioni superiori a 2 GB, si verificherà il troncamento e verrà restituito un avviso di "stringa dati troncamento a destra". 
  
Quando la compatibilità con il tipo di dati è impostata su 80, il comportamento client sarà coerente con il comportamento del client legacy.  
  
Per i client che utilizzano SQLOLEDB o altri provider rilasciati prima la [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], **varbinary (max)** verrà eseguito il mapping all'immagine.  
  
## <a name="comments"></a>Commenti
- Per inviare e ricevere **varbinary (max)** valori maggiori di 2 GB, un'applicazione utilizza **DBTYPE_IUNKNOWN** nelle associazioni di parametro e il risultato. Per i parametri il provider deve chiamare IUnknown:: QueryInterface per ISequentialStream e per ottenere risultati che restituiscono ISequentialStream.  

-  Per OLE DB, il controllo correlato ai valori ISequentialStream è assoluto. Quando *wType* è **DBTYPE_IUNKNOWN** nel **DBBINDING** struct, controllo della lunghezza può essere disabilitata omettendo **DBPART_LENGTH** da *dwPart* o impostando la lunghezza dei dati (offset *obLength* nel buffer di dati) a ~ 0. In questo caso, il provider non controllerà la lunghezza del valore e richiederà e restituirà tutti i dati disponibili tramite il flusso. Questa modifica verrà applicata a tutti i tipi LOB (Large Object) e XML, ma solo in caso di connessione a server [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] o versione successiva. In questo modo, gli sviluppatori disporranno di maggiore flessibilità, mantenendo la coerenza e la compatibilità con le versioni precedenti per applicazioni esistenti e server legacy.  Questa modifica interessa tutte le interfacce che trasferiscono i dati, principalmente IRowset:: GetData ICommand:: Execute e IRowsetFastLoad:: InsertRow.
 

## <a name="see-also"></a>Vedere anche  
 [Driver OLE DB per funzionalità di SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
