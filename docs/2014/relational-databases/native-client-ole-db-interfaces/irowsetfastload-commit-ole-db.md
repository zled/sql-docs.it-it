---
title: 'IRowsetFastLoad:: Commit (OLE DB) | Documenti Microsoft'
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
api_name:
- IRowsetFastLoad::Commit (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- Commit method
ms.assetid: 19de9128-b91a-4626-847f-af721edaa24e
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 553f3aaaceae23944ae9b2d0be7d8129a22c0dd1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069156"
---
# <a name="irowsetfastloadcommit-ole-db"></a>IRowsetFastLoad::Commit (OLE DB)
  Contrassegna la fine di un batch di righe inserite e scrive le righe nella tabella di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per esempi, vedere [Bulk copia i dati mediante IRowsetFastLoad &#40;OLE DB&#41; ](irowsetfastload-ole-db.md) e [inviare dati BLOB a SQL SERVER utilizzando IROWSETFASTLOAD e ISEQUENTIALSTREAM &#40;OLE DB&#41;](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
HRESULT Commit(  
BOOL   
fDone  
);  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *fDone*[in]  
 Se impostato su FALSE, il set di righe resta valido e può essere utilizzato dal consumer per l'inserimento di altre righe. Se impostato su TRUE, il set di righe non è più valido e il consumer non può inserire altre righe.  
  
## <a name="return-code-values"></a>Valori restituiti  
 S_OK  
 Il metodo è riuscito e tutti i dati inseriti sono stati scritti nella tabella [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 E_FAIL  
 Si è verificato un errore specifico del provider. Recuperare informazioni relative al testo dell'errore specifico dal provider.  
  
 E_UNEXPECTED  
 Il metodo è stato chiamato su un set di righe copia bulk precedentemente invalidato dal **IRowsetFastLoad:: commit** metodo.  
  
## <a name="remarks"></a>Remarks  
 Oggetto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] set di righe copia bulk del provider OLE DB Native Client si comporta come un set di righe di modalità di aggiornamento ritardato. Quando l'utente inserisce i dati di riga nel set di righe, le righe inserite vengono trattate nello stesso modo come inserimenti in sospeso di un set di righe che supportano **IRowsetUpdate**.  
  
 Il consumer deve chiamare il **Commit** (metodo) nel set di righe di copia bulk per scrivere le righe inserite il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella esattamente come il **IRowsetUpdate:: Update** metodo viene utilizzato per inviare le righe a in sospeso un istanza di SQL Server.  
  
 Se il consumer rilascia il riferimento al set di righe di copia bulk senza chiamare il **Commit** (metodo), inserita tutte le righe non scritte in precedenza andranno perse.  
  
 Il consumer può raggruppare le righe inserite chiamando il **Commit** metodo con il *fDone* argomento impostato su FALSE. Quando si *fDone*è impostata su TRUE, il set di righe diventa non valido. Un set di righe copia bulk non valido supporta solo il **ISupportErrorInfo** interfaccia e **IRowsetFastLoad:: Release** metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IRowsetFastLoad &#40;OLE DB&#41;](irowsetfastload-ole-db.md)  
  
  