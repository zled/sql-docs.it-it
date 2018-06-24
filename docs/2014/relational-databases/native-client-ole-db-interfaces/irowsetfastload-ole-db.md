---
title: IRowsetFastLoad (OLE DB) | Documenti Microsoft
ms.custom: ''
ms.date: 04/27/2017
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
- IRowsetFastLoad interface
ms.assetid: d19a7097-48d9-409a-aff9-277891b7aca7
caps.latest.revision: 36
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8c6ed5ff1f3cb0d818a25c6bf2a8753e2bb806e2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064668"
---
# <a name="irowsetfastload-ole-db"></a>IRowsetFastLoad (OLE DB)
  Il `IRowsetFastLoad` interfaccia espone il supporto per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] operazioni di copia bulk basate sulla memoria. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider (consumer) utilizzare l'interfaccia per aggiungere rapidamente dati a un oggetto esistente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella.  
  
 Se si imposta SSPROP_ENABLEFASTLOAD su VARIANT_TRUE per una sessione, non è possibile leggere dati dai set di righe restituiti successivamente dalla sessione. Quando SSPROP_ENABLEFASTLOAD è impostato su VARIANT_TRUE, tutti i set di righe creati nella sessione saranno di tipo IRowsetFastLoad. Set di righe iRowsetFastLoad non supportano la funzionalità di recupero di set di righe; Pertanto, non è possibile leggere i dati da questi set di righe.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Metodo|Description|  
|------------|-----------------|  
|[IRowsetFastLoad:: commit &#40;OLE DB&#41;](irowsetfastload-commit-ole-db.md)|Contrassegna la fine di un batch di righe inserite e scrive le righe nella tabella di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[IRowsetFastLoad:: InsertRow &#40;OLE DB&#41;](irowsetfastload-insertrow-ole-db.md)|Aggiunge una riga al set di righe della copia bulk.|  
  
## <a name="see-also"></a>Vedere anche  
 [Le interfacce &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)   
 [Copia bulk di dati mediante IRowsetFastLoad &#40;OLE DB&#41;](../native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md)   
 [Inviare dati BLOB a SQL SERVER utilizzando IROWSETFASTLOAD e ISEQUENTIALSTREAM &#40;OLE DB&#41;](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)  
  
  