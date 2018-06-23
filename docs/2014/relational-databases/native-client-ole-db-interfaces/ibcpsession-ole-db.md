---
title: IBCPSession (OLE DB) | Documenti Microsoft
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- IBCPSession interface
ms.assetid: 00d0311f-8b71-4ad6-824d-0e89119347a3
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7ccd40edb997ae3e45fd705a8a6543c8f3895b6f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36167237"
---
# <a name="ibcpsession-ole-db"></a>IBCPSession (OLE DB)
  Il **IBCPSession** interfaccia espone il supporto per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le operazioni di copia bulk basate su file. Il **IBCPSession** interfaccia viene esposta nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client nello stesso livello come le sessioni. Nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client, gli oggetti origine dati sono factory per oggetti di sessione e operazioni di copia bulk vengono specificate nella proprietà di connessione SSPROP_ENABLEBULKCOPY. Inoltre, la proprietà SSPROP_ENABLEFASTLOAD deve essere impostata su True.  
  
 La chiamata di **IDBCreateSession:: CreateSession** metodo comporterà quindi la creazione di un **BulkCopySession** oggetto. Tutti i metodi di copia bulk basate su file esposti tramite il **IBCPSession** oggetto vengono quindi chiamati con firme molto simili su questo **IBCPSession** dell'oggetto **IBCPSession**interfaccia.  
  
> [!NOTE]  
>  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client supporta operazioni di copia bulk basate sulla memoria tramite il [IRowsetFastLoad](irowsetfastload-ole-db.md) interfaccia.  
  
 Per ulteriori informazioni sull'utilizzo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client per operazioni di copia bulk, vedere [l'esecuzione di operazioni di copia Bulk](../native-client/features/performing-bulk-copy-operations.md).  
  
 Per un esempio che illustra come utilizzare il **IBCPSession** interfaccia, vedere [IBCPSession::BCPDone &#40;OLE DB&#41;](ibcpsession-bcpdone-ole-db.md).  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Metodo|Description|  
|------------|-----------------|  
|[Ibcpsession:: BCPColFmt &#40;OLE DB&#41;](ibcpsession-bcpcolfmt-ole-db.md)|Crea un'associazione tra variabili di programma e colonne di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Ibcpsession:: BCPColumns &#40;OLE DB&#41;](ibcpsession-bcpcolumns-ole-db.md)|Imposta il numero di campi da associare alle colonne di una tabella di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Ibcpsession:: Bcpcontrol &#40;OLE DB&#41;](ibcpsession-bcpcontrol-ole-db.md)|Imposta le opzioni per un'operazione di copia bulk.|  
|[IBCPSession::BCPDone &#40;OLE DB&#41;](ibcpsession-bcpdone-ole-db.md)|Esegue il commit delle righe restanti da inviare a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Ibcpsession:: BCPExec &#40;OLE DB&#41;](ibcpsession-bcpexec-ole-db.md)|Esegue l'operazione di copia bulk.|  
|[Ibcpsession:: BCPInit &#40;OLE DB&#41;](ibcpsession-bcpinit-ole-db.md)|Inizializza la struttura della copia bulk, esegue alcune operazioni di controllo degli errori, verifica che i dati e i nomi dei file di formato siano corretti, quindi li apre.|  
|[Ibcpsession:: Bcpreadfmt &#40;OLE DB&#41;](ibcpsession-bcpreadfmt-ole-db.md)|Legge le informazioni sul formato per ogni colonna dal file di formato.|  
|[Ibcpsession:: Bcpwritefmt &#40;OLE DB&#41;](ibcpsession-bcpwritefmt-ole-db.md)|Scrive informazioni sul formato per ogni colonna nel file di formato.|  
  
## <a name="see-also"></a>Vedere anche  
 [Le interfacce &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  