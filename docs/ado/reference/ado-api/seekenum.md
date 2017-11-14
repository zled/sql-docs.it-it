---
title: SeekEnum | Documenti Microsoft
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
- SeekEnum
helpviewer_keywords:
- SeekEnum enumeration [ADO]
ms.assetid: f0ec0c92-8253-47c6-9a14-e5dbccbad219
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 051f4e1c300796e2777e9b06a1514c9ce00b9b02
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="seekenum"></a>SeekEnum
Specifica il tipo di [Seek](../../../ado/reference/ado-api/seek-method.md) da eseguire.  
  
|Costante|Valore|Description|  
|--------------|-----------|-----------------|  
|**adSeekFirstEQ**|1|Cerca la prima chiave uguale a *KeyValues*.|  
|**adSeekLastEQ**|2|Cerca l'ultima chiave uguale a *KeyValues*.|  
|**adSeekAfterEQ**|4|Cerca una chiave uguale a *KeyValues* o subito dopo dove sarebbero state eseguite corrispondenti.|  
|**adSeekAfter**|8|Cerca una chiave subito dopo la posizione in cui una corrispondenza con *KeyValues* sarebbero state eseguite.|  
|**adSeekBeforeEQ**|16|Cerca una chiave uguale a *KeyValues*o appena prima dove sarebbero state eseguite corrispondenti.|  
|**adSeekBefore**|32|Cerca immediatamente prima di una chiave in cui una corrispondenza con *KeyValues* sarebbero state eseguite.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Pacchetto: **com.ms. wfc.**  
  
|Costante|  
|--------------|  
|AdoEnums.Seek.FIRSTEQ|  
|AdoEnums.Seek.LASTEQ|  
|AdoEnums.Seek.AFTEREQ|  
|AdoEnums.Seek.AFTER|  
|AdoEnums.Seek.BEFOREEQ|  
|AdoEnums.Seek.BEFORE|  
  
## <a name="applies-to"></a>Si applica a  
 [Il metodo di ricerca](../../../ado/reference/ado-api/seek-method.md)

