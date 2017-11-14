---
title: MoveRecordOptionsEnum | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
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
- MoveRecordOptionsEnum
helpviewer_keywords:
- MoveRecordOptionsEnum enumeration [ADO]
ms.assetid: f53c2ce4-1021-4a45-92b8-775e8bebad99
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: dc684d2c38347251c1f7af843a105f13989e5f8a
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="moverecordoptionsenum"></a>MoveRecordOptionsEnum
Specifica il comportamento del [Record](../../../ado/reference/ado-api/record-object-ado.md) oggetto [MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md) metodo.  
  
|Costante|Valore|Description|  
|--------------|-----------|-----------------|  
|**adMoveUnspecified**|-1|Valore predefinito. Esegue l'operazione di spostamento predefinito: l'operazione non riesce se il file di destinazione o la directory esiste già, e l'operazione Aggiorna i collegamenti ipertestuali.|  
|**adMoveOverWrite**|1|Sovrascrive il file di destinazione o la directory, anche se esiste già.|  
|**adMoveDontUpdateLinks**|2|Modifica il comportamento predefinito di **MoveRecord** metodo non aggiornando i collegamenti ipertestuali dell'origine **Record**. Il comportamento predefinito dipende dalle funzionalità del provider. Operazione di spostamento Aggiorna collegamenti se il provider è in grado di supportare. Se il provider non è possibile correggere collegamenti o se questo valore non è specificato, quindi il passaggio ha esito positivo anche quando i collegamenti non sono stati corretti.|  
|**adMoveAllowEmulation**|4|Richiede che il provider tenterà di simulare lo spostamento (tramite le operazioni di eliminazione, caricamento e download). Se il tentativo di spostare il **Record** ha esito negativo perché l'URL di destinazione è in un server diverso o serviti da un provider diverso da quello di origine, può causare un aumento latenza o perdita di dati, grazie a funzionalità di un provider diverso quando lo spostamento delle risorse tra provider.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Queste costanti non dispongono di equivalenti ADO/WFC.  
  
## <a name="applies-to"></a>Si applica a  
 [Metodo MoveRecord (ADO)](../../../ado/reference/ado-api/moverecord-method-ado.md)

