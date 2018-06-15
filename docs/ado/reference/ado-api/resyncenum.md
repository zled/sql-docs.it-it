---
title: ResyncEnum | Documenti Microsoft
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
- ResyncEnum
helpviewer_keywords:
- ResyncEnum enumeration [ADO]
ms.assetid: d3df2c90-e570-4c40-a79a-25b3448a009c
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3b974d00ecb1fb4d0d9d7e431f28df16f945d778
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35281360"
---
# <a name="resyncenum"></a>ResyncEnum
Specifica se i valori sottostanti vengono sovrascritti da una chiamata a [Resync](../../../ado/reference/ado-api/resync-method.md).  
  
|Costante|valore|Description|  
|--------------|-----------|-----------------|  
|**adResyncAllValues**|2|Valore predefinito. Sovrascrive i dati e gli aggiornamenti in sospeso vengono annullate.|  
|**adResyncUnderlyingValues**|1|Non sovrascrivere i dati e gli aggiornamenti in sospeso non vengono annullate.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Package: **com.ms.wfc.data**  
  
|Costante|  
|--------------|  
|AdoEnums.Resync.ALLVALUES|  
|AdoEnums.Resync.UNDERLYINGVALUES|  
  
## <a name="applies-to"></a>Si applica a  
 [Metodo Resync](../../../ado/reference/ado-api/resync-method.md)
