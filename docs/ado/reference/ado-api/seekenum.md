---
title: SeekEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- SeekEnum
helpviewer_keywords:
- SeekEnum enumeration [ADO]
ms.assetid: f0ec0c92-8253-47c6-9a14-e5dbccbad219
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a6e044c4a2cda01fcc9cbba2667beaae75a12caf
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47772729"
---
# <a name="seekenum"></a>SeekEnum
Specifica il tipo della [Seek](../../../ado/reference/ado-api/seek-method.md) da eseguire.  
  
|Costante|valore|Description|  
|--------------|-----------|-----------------|  
|**adSeekFirstEQ**|1|Cerca la prima chiave uguale a *KeyValues*.|  
|**adSeekLastEQ**|2|Cerca la chiave dell'ultimo uguale a *KeyValues*.|  
|**adSeekAfterEQ**|4|Cerca una chiave uguale a *KeyValues* o subito dopo in cui sarebbe state eseguite se tale corrispondenza.|  
|**adSeekAfter**|8|Cerca una chiave subito dopo la posizione in cui una corrispondenza con *KeyValues* sarebbero state eseguite.|  
|**adSeekBeforeEQ**|16|Cerca una chiave uguale a *KeyValues*o appena prima dove sarebbe state eseguite se tale corrispondenza.|  
|**adSeekBefore**|32|Cerca immediatamente prima di una chiave in cui una corrispondenza con *KeyValues* sarebbero state eseguite.|  
  
## <a name="adowfc-equivalent"></a>Equivalente di ADO o WFC  
 Package: **com.ms.wfc.data**  
  
|Costante|  
|--------------|  
|AdoEnums.Seek.FIRSTEQ|  
|AdoEnums.Seek.LASTEQ|  
|AdoEnums.Seek.AFTEREQ|  
|AdoEnums.Seek.AFTER|  
|AdoEnums.Seek.BEFOREEQ|  
|AdoEnums.Seek.BEFORE|  
  
## <a name="applies-to"></a>Si applica a  
 [Metodo Seek](../../../ado/reference/ado-api/seek-method.md)
