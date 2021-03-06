---
title: MoveRecordOptionsEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- MoveRecordOptionsEnum
helpviewer_keywords:
- MoveRecordOptionsEnum enumeration [ADO]
ms.assetid: f53c2ce4-1021-4a45-92b8-775e8bebad99
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eb86b01a42a097210801fd3654ff2af80df24e39
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47701589"
---
# <a name="moverecordoptionsenum"></a>MoveRecordOptionsEnum
Specifica il comportamento dei [Record](../../../ado/reference/ado-api/record-object-ado.md) oggetto [MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md) (metodo).  
  
|Costante|valore|Description|  
|--------------|-----------|-----------------|  
|**adMoveUnspecified**|-1|Valore predefinito. Esegue l'operazione di spostamento predefinito: l'operazione ha esito negativo se il file di destinazione o la directory esiste già e l'operazione Aggiorna i collegamenti ipertestuali.|  
|**adMoveOverWrite**|1|Sovrascrive il file di destinazione o la directory, anche se esiste già.|  
|**adMoveDontUpdateLinks**|2|Modifica il comportamento predefinito della **MoveRecord** metodo aggiornando non collegamenti ipertestuali dell'origine **Record**. Il comportamento predefinito dipende dalle funzionalità del provider. Operazione di spostamento aggiornamenti collegamenti se il provider è in grado di supportare. Se il provider non è possibile correggere collegamenti o se non viene specificato questo valore, quindi lo spostamento ha esito positivo anche quando i collegamenti non sono stati corretti.|  
|**adMoveAllowEmulation**|4|Richiede che il provider tenta di simulare lo spostamento (tramite le operazioni di eliminazione, caricamento e download). Se il tentativo di spostare il **Record** ha esito negativo perché l'URL di destinazione è in un server diverso o serviti da un provider diverso da quello di origine, questo può causare una maggiore latenza o perdita di dati, a causa di funzionalità del provider diversa quando lo spostamento delle risorse tra provider.|  
  
## <a name="adowfc-equivalent"></a>Equivalente di ADO o WFC  
 Queste costanti non dispongono di equivalenti di ADO o WFC.  
  
## <a name="applies-to"></a>Si applica a  
 [Metodo MoveRecord (ADO)](../../../ado/reference/ado-api/moverecord-method-ado.md)
