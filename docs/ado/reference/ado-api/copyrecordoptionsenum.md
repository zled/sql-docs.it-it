---
title: CopyRecordOptionsEnum uguale al | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CopyRecordOptionsEnum
helpviewer_keywords:
- CopyRecordOptionsEnum enumeration [ADO]
ms.assetid: 2fa4eec5-d50b-4fd3-8ae7-40af441ba12b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fe0b12053b9ac7203253e81fa3300d2e4109a129
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47681565"
---
# <a name="copyrecordoptionsenum"></a>CopyRecordOptionsEnum
Specifica il comportamento dei [CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md) (metodo).  
  
|Costante|valore|Description|  
|--------------|-----------|-----------------|  
|**adCopyAllowEmulation**|4|Indica che il *origine* provider tenta di simulare la copia con il download e operazioni di caricamento se questo metodo ha esito negativo a causa dell'errore *destinazione*si trova in un altro server o viene servito da un altro provider rispetto *origine*. Si noti che diverse funzionalità del provider possono ostacolare le prestazioni o perdita di dati.|  
|**adCopyNonRecursive**|2|Copia nella directory corrente, ma nessuna delle relative sottodirectory, nella destinazione. L'operazione di copia non è ricorsiva.|  
|**adCopyOverWrite**|1|Sovrascrive il file o la directory se il *destinazione* punta a un file o directory esistente.|  
|**adCopyUnspecified**|-1|Valore predefinito. Esegue l'operazione di copia predefinito: l'operazione non riesce se il file di destinazione o la directory esiste già e le copie di operazione in modo ricorsivo.|  
  
## <a name="adowfc-equivalent"></a>Equivalente di ADO o WFC  
 Queste costanti non dispongono di equivalenti di ADO o WFC.  
  
## <a name="applies-to"></a>Si applica a  
 [Metodo CopyRecord (ADO)](../../../ado/reference/ado-api/copyrecord-method-ado.md)
