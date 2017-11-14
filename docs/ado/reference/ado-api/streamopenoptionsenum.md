---
title: StreamOpenOptionsEnum | Documenti Microsoft
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
- StreamOpenOptionsEnum
helpviewer_keywords:
- StreamOpenOptionsEnum enumeration [ADO]
ms.assetid: 85b6c57f-47ed-46ba-bd92-07882ae9e9d2
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 268d495d2163d03244a6bec57762b93a26ab32ea
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="streamopenoptionsenum"></a>StreamOpenOptionsEnum
Specifica le opzioni per aprire un [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetto. I valori possono essere combinati con un'operazione OR.  
  
|Costante|Valore|Description|  
|--------------|-----------|-----------------|  
|**adOpenStreamAsync**|1|Apre il **flusso** oggetto in modalità asincrona.|  
|**adOpenStreamFromRecord**|4|Identifica il contenuto di *origine* parametro sia un già aperto [Record](../../../ado/reference/ado-api/record-object-ado.md) oggetto. Il comportamento predefinito consiste nel considerare *origine* come un URL che punta direttamente a un nodo in una struttura ad albero. Viene aperto il flusso predefinito associato a tale nodo.|  
|**adOpenStreamUnspecified**|-1|Valore predefinito. Specifica l'apertura di **flusso** oggetto con le opzioni predefinite.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Queste costanti non dispongono di equivalenti ADO/WFC.  
  
## <a name="applies-to"></a>Si applica a  
 [Open (metodo) (flusso ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)

