---
title: Metodo SaveToFile | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Stream::raw_SaveToFile
- _Stream::SaveToFile
helpviewer_keywords:
- SaveToFile method [ADO]
ms.assetid: 8a8594f2-422b-4d2e-94f8-7fe337445900
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 64fa2093400ac9c003397659be3d9d6f4251eee2
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="savetofile-method"></a>Metodo SaveToFile
Salva il contenuto binario di un [flusso](../../../ado/reference/ado-api/stream-object-ado.md) in un file.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Stream.SaveToFile FileName, SaveOptions  
```  
  
#### <a name="parameters"></a>Parametri  
 *FileName*  
 A **stringa** valore contenente il nome completo del file in cui il contenuto del **flusso** verranno salvate. È possibile salvare in qualsiasi percorso locale valido, o qualsiasi posizione, è possibile accedere tramite un valore di tipo UNC.  
  
 *SaveOptions*  
 Oggetto [SaveOptionsEnum](../../../ado/reference/ado-api/saveoptionsenum.md) valore che specifica se deve essere creato un nuovo file da **SaveToFile**, se non esiste già. Valore predefinito è **adSaveCreateNotExists**. Con queste opzioni è possibile specificare che si verifica un errore se il file specificato non esiste. È inoltre possibile specificare che **SaveToFile** sovrascrive il contenuto corrente di un file esistente.  
  
> [!NOTE]
>  Se si sovrascrive un file esistente (quando **adSaveCreateOverwrite** è impostata), **SaveToFile** tronca i byte da un file esistente originale che seguono il nuovo [fine del flusso](../../../ado/reference/ado-api/eos-property.md).  
  
## <a name="remarks"></a>Osservazioni  
 **SaveToFile** può essere utilizzato per copiare il contenuto di un **flusso** oggetto in un file locale. Non è stata modificata nel contenuto o le proprietà del **flusso** oggetto. Il **flusso** oggetto deve essere aperto prima di chiamare **SaveToFile**.  
  
 Questo metodo non modifica l'associazione del **flusso** oggetto alla relativa origine sottostante. Il **flusso** oggetto continuerà a essere associato con l'URL originale o **Record** che è stata la relativa origine all'apertura.  
  
 Dopo un **SaveToFile** operazione, la posizione corrente ([posizione](../../../ado/reference/ado-api/position-property-ado.md)) nel flusso è impostata sull'inizio del flusso (0).  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Open (metodo) (flusso ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [Metodo Save](../../../ado/reference/ado-api/save-method.md)
