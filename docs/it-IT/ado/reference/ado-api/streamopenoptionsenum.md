---
title: StreamOpenOptionsEnum | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
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
ms.openlocfilehash: ca4119ac853ec6586c65f8648440ddf02fabb4a4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="streamopenoptionsenum"></a>StreamOpenOptionsEnum
Specifica le opzioni per aprire un [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetto. I valori possono essere combinati con un'operazione OR.  
  
|Costante|Value|Description|  
|--------------|-----------|-----------------|  
|**adOpenStreamAsync**|1|Apre il **flusso** oggetto in modalità asincrona.|  
|**adOpenStreamFromRecord**|4|Identifica il contenuto di *origine* parametro sia un già aperto [Record](../../../ado/reference/ado-api/record-object-ado.md) oggetto. Il comportamento predefinito consiste nel considerare *origine* come un URL che punta direttamente a un nodo in una struttura ad albero. Viene aperto il flusso predefinito associato a tale nodo.|  
|**adOpenStreamUnspecified**|-1|Valore predefinito. Specifica l'apertura di **flusso** oggetto con le opzioni predefinite.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Queste costanti non dispongono di equivalenti ADO/WFC.  
  
## <a name="applies-to"></a>Si applica a  
 [Metodo Open (flusso ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)
