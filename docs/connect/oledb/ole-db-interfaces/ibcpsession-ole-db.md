---
title: IBCPSession (OLE DB) | Microsoft Docs
description: Interfaccia IBCPSession (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apitype: COM
helpviewer_keywords:
- IBCPSession interface
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 96603d7dcb6215513d67d4db5d29f8a762d57ea8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47764925"
---
# <a name="ibcpsession-ole-db"></a>IBCPSession (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  L'interfaccia **IBCPSession** espone il supporto per le operazioni di copia bulk basate su file [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il **IBCPSession** interfaccia viene esposta nel Driver OLE DB per SQL Server con lo stesso livello di sessioni. Nel driver OLE DB per SQL Server, gli oggetti origine dati sono factory per gli oggetti Session e le operazioni di copia bulk vengono specificate nella proprietà di connessione SSPROP_ENABLEBULKCOPY. Inoltre, la proprietà SSPROP_ENABLEFASTLOAD deve essere impostata su True.  
  
 La chiamata al metodo **IDBCreateSession::CreateSession** comporterà quindi la creazione di un oggetto **BulkCopySession**. Tutti i metodi di copia bulk basati su file esposti tramite l'oggetto **IBCPSession** possono essere quindi chiamati con firme molto simili sull'interfaccia **IBCPSession** di questo oggetto **IBCPSession**.  
  
> [!NOTE]  
>  Il driver OLE DB per SQL Server supporta operazioni di copia bulk basate sulla memoria tramite l'interfaccia [IRowsetFastLoad](../../oledb/ole-db-interfaces/irowsetfastload-ole-db.md).  
  
 Per altre informazioni sull'utilizzo del Driver OLE DB per SQL Server per operazioni di copia bulk, vedere [esecuzione di operazioni di copia Bulk](../../oledb/features/performing-bulk-copy-operations.md).  
  
 Per un esempio che illustra come usare il **IBCPSession** l'interfaccia, vedere [IBCPSession::BCPDone &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpdone-ole-db.md).  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Ibcpsession:: BCPColFmt &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md)|Crea un'associazione tra variabili di programma e colonne di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[Ibcpsession:: BCPColumns &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md)|Imposta il numero di campi da associare alle colonne di una tabella di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[Ibcpsession:: Bcpcontrol &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md)|Imposta le opzioni per un'operazione di copia bulk.|  
|[IBCPSession::BCPDone &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpdone-ole-db.md)|Esegue il commit delle righe restanti da inviare a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[Ibcpsession:: BCPExec &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpexec-ole-db.md)|Esegue l'operazione di copia bulk.|  
|[Ibcpsession:: BCPInit &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpinit-ole-db.md)|Inizializza la struttura della copia bulk, esegue alcune operazioni di controllo degli errori, verifica che i dati e i nomi dei file di formato siano corretti, quindi li apre.|  
|[Ibcpsession:: Bcpreadfmt &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md)|Legge le informazioni sul formato per ogni colonna dal file di formato.|  
|[Ibcpsession:: Bcpwritefmt &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md)|Scrive informazioni sul formato per ogni colonna nel file di formato.|  
  
## <a name="see-also"></a>Vedere anche  
 [Le interfacce &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md)  
  
  
