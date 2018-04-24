---
title: ObjectStateEnum | Documenti Microsoft
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
- ObjectStateEnum
helpviewer_keywords:
- ObjectStateEnum enumeration [ADO]
ms.assetid: 32746558-097b-4749-989e-519aadf7e3f4
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2027cd4b7f034333d383f570860fddf841097b7d
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="objectstateenum"></a>ObjectStateEnum
Specifica se un oggetto è aperto o chiuso, la connessione a un'origine dati, l'esecuzione di un comando o il recupero dei dati.  
  
|Costante|Value|Description|  
|--------------|-----------|-----------------|  
|**adStateClosed**|0|Indica che l'oggetto viene chiuso.|  
|**adStateOpen**|1|Indica che l'oggetto è aperto.|  
|**adStateConnecting**|2|Indica che si connette l'oggetto.|  
|**adStateExecuting**|4|Indica che l'oggetto sta eseguendo un comando.|  
|**adStateFetching**|8|Indica che le righe dell'oggetto vengono recuperate.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Package: **com.ms.wfc.data**  
  
|Costante|  
|--------------|  
|AdoEnums.ObjectState.CLOSED|  
|AdoEnums.ObjectState.OPEN|  
|AdoEnums.ObjectState.CONNECTING|  
|AdoEnums.ObjectState.EXECUTING|  
|AdoEnums.ObjectState.FETCHING|  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Proprietà State (ADO MD)](../../../ado/reference/ado-md-api/state-property-ado-md.md)|[Proprietà State (ADO)](../../../ado/reference/ado-api/state-property-ado.md)|
