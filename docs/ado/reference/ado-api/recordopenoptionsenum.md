---
title: RecordOpenOptionsEnum | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RecordOpenOptionsEnum
helpviewer_keywords:
- RecordOpenOptionsEnum enumeration [ADO]
ms.assetid: 9028aba4-90fc-4dfc-88e4-fa8a7b6fedee
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c7372e17fb7e18cec3cbb25a1850433e41e918a7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="recordopenoptionsenum"></a>RecordOpenOptionsEnum
Specifica le opzioni per aprire un [Record](../../../ado/reference/ado-api/record-object-ado.md). Questi valori possono essere combinati con o.  
  
|Costante|Value|Description|  
|--------------|-----------|-----------------|  
|**adDelayFetchFields**|0x8000|Indica al provider che i campi associati di **Record** non devono essere recuperati inizialmente, ma può essere recuperato al primo tentativo di accedere al campo. È il comportamento predefinito, indicato dall'assenza di questo flag, per recuperare tutti i **Record** i campi dell'oggetto.|  
|**adDelayFetchStream**|0x4000|Indica al provider che il flusso predefinito viene associato il **Record** non devono essere recuperati inizialmente. È il comportamento predefinito, indicato dall'assenza di questo flag, per recuperare il flusso predefinito associato con il **Record** oggetto.|  
|**adOpenAsync**|0x1000|Indica che il **Record** oggetto viene aperto in modalità asincrona.|  
|**adOpenExecuteCommand**|0x10000|Indica che la stringa di origine contiene testo del comando che deve essere eseguito. Questo valore è equivalente al **adCmdText** opzione **Open**.|  
|**adOpenRecordUnspecified**|-1|Valore predefinito. Indica che viene specificata alcuna opzione.|  
|**adOpenOutput**|0x800000|Che indica se l'origine punta a un nodo che contiene uno script eseguibile (ad esempio un. La pagina ASP), quindi aperto **Record** conterrà i risultati dello script eseguito. Questo valore è valido solo con i record non di raccolta.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Queste costanti non dispongono di equivalenti ADO/WFC.  
  
## <a name="applies-to"></a>Si applica a  
 [Metodo Open (record ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)
