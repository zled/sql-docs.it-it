---
title: Oggetti BLOB e OLE | Documenti Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-ole-db-blobs
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- BLOBs, OLE objects
- BLOBs
- storage object [OLE DB]
- SQL Server Native Client OLE DB provider, BLOBs
- large data, OLE objects
ms.assetid: 767fa2f6-9cd2-436f-add5-e760bed29a58
caps.latest.revision: 43
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 9f5ec924883f046991c9eba6e62c79b9bec7a6fc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="blobs-and-ole-objects"></a>Oggetti BLOB e OLE
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client espone la **ISequentialStream** interfaccia per supportare i consumer di accedere a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **ntext**, **testo**, **immagine**, **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, e i tipi di dati xml come binari oggetti di grandi dimensioni (BLOB). Il **lettura** metodo **ISequentialStream** consente al consumer di recuperare una quantità di dati in blocchi gestibili.  
  
 Per un esempio che illustri questa caratteristica, vedere [impostare dati di grandi dimensioni & #40; OLE DB & #41;](../../relational-databases/native-client-ole-db-how-to/set-large-data-ole-db.md).  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client è possibile utilizzare un consumer implementato **IStorage** interfaccia quando il consumer fornisce il puntatore di interfaccia in una funzione di accesso associato per la modifica dei dati.  
  
 Per i tipi di dati di valori di grandi dimensioni, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client verifica presupposti di dimensioni di tipo in **IRowset** e le interfacce DDL. Le colonne con **varchar**, **nvarchar**, e **varbinary** tipi di dati con dimensione massima è impostata su un valore illimitato verranno rappresentati come ISLONG mediante le interfacce di restituzione di tipi di dati di colonna e il set di righe dello schema.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client espone la **varchar (max)**, **varbinary (max)** e **nvarchar (max)** tipi rispettivamente come DBTYPE_STR, DBTYPE_BYTES e DBTYPE_WSTR.  
  
 In un'applicazione è possibile utilizzare questi tipi nei modi seguenti:  
  
-   Eseguire l'associazione come tipo (DBTYPE_STR, DBTYPE_BYTES, DBTYPE_WSTR). Se le dimensioni de buffer non sono sufficienti, si verificherà il troncamento, esattamente come accade per questi tipi nelle release precedenti, anche se ora sono disponibili valori più grandi.  
  
-   Eseguire l'associazione come tipo e specificare DBTYPE_BYREF.  
  
-   Eseguire l'associazione come DBTYPE_IUNKNOWN e utilizzare il flusso.  
  
 Se si esegue l'associazione a DBTYPE_IUNKNOWN, viene utilizzata la funzionalità di flusso di ISequentialStream. Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client supporta i parametri di output di associazione come DBTYPE_IUNKNOWN per i tipi di dati di valori di grandi dimensioni semplificare gli scenari in cui una stored procedure restituisce questi dati tipi come valori restituiti che verranno esposti come DBTYPE_IUNKNOWN al client.  
  
## <a name="storage-object-limitations"></a>Limitazioni degli oggetti di archiviazione  
  
-   Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client può supportare solo un oggetto di archiviazione aperto. Tenta di aprire più di un oggetto di archiviazione (per ottenere un riferimento in più di uno **ISequentialStream** puntatore a interfaccia) restituiscono DBSTATUS_E_CANTCREATE.  
  
-   Nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client, il valore predefinito della proprietà di sola lettura DBPROP_BLOCKINGSTORAGEOBJECTS è VARIANT_TRUE. Tale valore indica che se un oggetto di archiviazione è attivo, alcuni metodi (diversi da quelli degli oggetti di archiviazione) non riusciranno e verrà restituito E_UNEXPECTED.  
  
-   La lunghezza dei dati presentati da un oggetto di archiviazione implementato consumer deve essere resa nota per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client quando viene creata la funzione di accesso di riga che fa riferimento all'oggetto di archiviazione. Il consumer deve associare un indicatore di lunghezza nella struttura DBBINDING utilizzata per la creazione della funzione di accesso.  
  
-   Se una riga contiene più di un valore di dati di grandi dimensioni e DBPROP_ACCESSORDER non è DBPROPVAL_AO_RANDOM, il consumer deve usare un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rowset supportato dal cursore provider OLE DB Native Client per recuperare i dati di riga o elaborare tutti i valori di dati di grandi dimensioni prima di recuperare altri valori di riga. Se DBPROP_ACCESSORDER è DBPROPVAL_AO_RANDOM, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client memorizza nella cache tutti i tipi di dati xml come oggetti binari di grandi dimensioni (BLOB) in modo che sia accessibile in qualsiasi ordine.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [Recupero di dati di grandi dimensioni](../../relational-databases/native-client-ole-db-blobs/getting-large-data.md)  
  
-   [Impostazione dati di grandi dimensioni](../../relational-databases/native-client-ole-db-blobs/setting-large-data.md)  
  
-   [Supporto dello streaming per i parametri di Output BLOB](../../relational-databases/native-client-ole-db-blobs/streaming-support-for-blob-output-parameters.md)  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Native Client & #40; OLE DB & #41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)   
 [Utilizzo di tipi di valori di grandi dimensioni](../../relational-databases/native-client/features/using-large-value-types.md)  
  
  
