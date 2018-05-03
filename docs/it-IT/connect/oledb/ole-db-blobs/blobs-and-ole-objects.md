---
title: Oggetti BLOB e OLE | Documenti Microsoft
description: Oggetti BLOB e OLE
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-blobs
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- BLOBs, OLE objects
- BLOBs
- storage object [OLE DB]
- OLE DB Driver for SQL Server, BLOBs
- large data, OLE objects
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 81cbe599c0845d839975fc51c32d4b14b69ea321
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="blobs-and-ole-objects"></a>Oggetti BLOB e OLE
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Il Driver OLE DB per SQL Server espone il **ISequentialStream** interfaccia per supportare l'accesso consumer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **ntext**, **text**, **immagine** , **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, e oggetti come binari di grandi dimensioni (BLOB) i tipi di dati xml. Il **lettura** metodo **ISequentialStream** consente al consumer di recuperare una quantità di dati in blocchi gestibili.  
  
 Per un esempio che illustri questa caratteristica, vedere [impostare dati di grandi dimensioni & #40; OLE DB & #41;](../../oledb/ole-db-how-to/set-large-data-ole-db.md).  
  
 Il Driver OLE DB per SQL Server è possibile utilizzare un consumer implementato **IStorage** interfaccia quando il consumer fornisce il puntatore di interfaccia in una funzione di accesso associata per la modifica dei dati.  
  
 Per i tipi di dati di valori di grandi dimensioni, il Driver OLE DB per SQL Server cerca presupposti per le dimensioni tipo in **IRowset** e le interfacce DDL. Le colonne contenenti **varchar**, **nvarchar**, e **varbinary** tipi di dati e dimensione massima è impostata su un valore illimitato verranno rappresentate come ISLONG tramite i set di righe dello schema e tramite interfacce che restituiscono tipi di dati di colonna.  
  
 Il Driver OLE DB per SQL Server espone il **varchar (max)**, **varbinary (max)** e **nvarchar (max)** tipi rispettivamente come DBTYPE_STR, DBTYPE_BYTES e DBTYPE_WSTR.  
  
 In un'applicazione è possibile utilizzare questi tipi nei modi seguenti:  
  
-   Eseguire l'associazione come tipo (DBTYPE_STR, DBTYPE_BYTES, DBTYPE_WSTR). Se il buffer non è grande abbastanza verificherà il troncamento, esattamente come accade per questi tipi nelle versioni precedenti (anche se i valori maggiori sono ora disponibili).  
  
-   Eseguire l'associazione come tipo e specificare DBTYPE_BYREF.  
  
-   Eseguire l'associazione come DBTYPE_IUNKNOWN e utilizzare il flusso.  
  
 Se si esegue l'associazione a DBTYPE_IUNKNOWN, viene utilizzata la funzionalità di flusso di ISequentialStream. Il Driver OLE DB per SQL Server supporta i parametri di output di associazione come DBTYPE_IUNKNOWN per i tipi di dati di valori di grandi dimensioni. Si tratta per supportare scenari in cui una stored procedure restituisce questi tipi di dati come valori restituiti, che verranno restituiti come DBTYPE_IUNKNOWN al client.  
  
## <a name="storage-object-limitations"></a>Limitazioni degli oggetti di archiviazione  
  
-   Il Driver OLE DB per SQL Server può supportare solo un oggetto di archiviazione aperto singolo. Tenta di aprire più di un oggetto di archiviazione (per ottenere un riferimento in più di uno **ISequentialStream** puntatore a interfaccia) restituiscono DBSTATUS_E_CANTCREATE.  
  
-   Nel Driver OLE DB per SQL Server, il valore predefinito della proprietà di sola lettura DBPROP_BLOCKINGSTORAGEOBJECTS è VARIANT_TRUE. Pertanto, se un oggetto di archiviazione è attivo, alcuni metodi (diversi da metodi degli oggetti di archiviazione) avrà esito negativo con E_UNEXPECTED.  
  
-   La lunghezza dei dati presentati da un oggetto di archiviazione implementato consumer deve essere reso nota per il Driver OLE DB per SQL Server quando viene creata la funzione di accesso di riga che fa riferimento all'oggetto di archiviazione. Il consumer deve associare un indicatore di lunghezza nella struttura DBBINDING utilizzata per la creazione della funzione di accesso.  
  
-   Se una riga contiene più di un valore di dati di grandi dimensioni e DBPROP_ACCESSORDER non è DBPROPVAL_AO_RANDOM, il consumer deve utilizzare un Driver OLE DB per SQL Server supportato dal cursore set di righe per recuperare i dati di riga o elaborare tutti i valori di dati di grandi dimensioni prima di recuperare altri valori di riga. Se DBPROP_ACCESSORDER è DBPROPVAL_AO_RANDOM, il Driver OLE DB per SQL Server memorizza nella cache tutti i tipi di dati xml come oggetti binari di grandi dimensioni (BLOB) in modo che possano accedervi in qualsiasi ordine.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
-   [Recupero di dati di grandi dimensioni](../../oledb/ole-db-blobs/getting-large-data.md)  
  
-   [Impostazione dati di grandi dimensioni](../../oledb/ole-db-blobs/setting-large-data.md)  
  
-   [Supporto dello streaming per i parametri di Output BLOB](../../oledb/ole-db-blobs/streaming-support-for-blob-output-parameters.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Driver OLE DB per la programmazione di SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)        
 [Utilizzo di tipi di valori di grandi dimensioni](../../oledb/features/using-large-value-types.md)  
  
  
