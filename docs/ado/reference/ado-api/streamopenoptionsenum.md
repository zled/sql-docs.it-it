---
title: StreamOpenOptionsEnum | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- StreamOpenOptionsEnum
helpviewer_keywords:
- StreamOpenOptionsEnum enumeration [ADO]
ms.assetid: 85b6c57f-47ed-46ba-bd92-07882ae9e9d2
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5aca6380229e55ed29c99ea51592e1e618ce0058
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35282620"
---
# <a name="streamopenoptionsenum"></a>StreamOpenOptionsEnum
Specifica le opzioni per aprire un [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetto. I valori possono essere combinati con un'operazione OR.  
  
|Costante|valore|Description|  
|--------------|-----------|-----------------|  
|**adOpenStreamAsync**|1|Apre il **flusso** oggetto in modalità asincrona.|  
|**adOpenStreamFromRecord**|4|Identifica il contenuto di *origine* parametro sia un già aperto [Record](../../../ado/reference/ado-api/record-object-ado.md) oggetto. Il comportamento predefinito consiste nel considerare *origine* come un URL che punta direttamente a un nodo in una struttura ad albero. Viene aperto il flusso predefinito associato a tale nodo.|  
|**adOpenStreamUnspecified**|-1|Valore predefinito. Specifica l'apertura di **flusso** oggetto con le opzioni predefinite.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Queste costanti non dispongono di equivalenti ADO/WFC.  
  
## <a name="applies-to"></a>Si applica a  
 [Metodo Open (flusso ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)
