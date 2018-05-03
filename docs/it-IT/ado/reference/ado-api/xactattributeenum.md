---
title: XactAttributeEnum | Documenti Microsoft
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
- XactAttributeEnum
helpviewer_keywords:
- XactAttributeEnum enumeration [ADO]
ms.assetid: e7dcecd3-7dc7-445c-b922-f700c3067fbc
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 33b3ac42f0e0e175e2dc2571c77f6dbaa962922f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="xactattributeenum"></a>XactAttributeEnum
Specifica gli attributi della transazione di un [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto.  
  
|Costante|Value|Description|  
|--------------|-----------|-----------------|  
|**adXactAbortRetaining**|262144|Esegue interruzioni senza perdita chiamando [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) per avviare automaticamente una nuova transazione. Non tutti i provider supportano questa funzionalità.|  
|**adXactCommitRetaining**|131072|Esegue commit conservazione chiamando [CommitTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) per avviare automaticamente una nuova transazione. Non tutti i provider supportano questa funzionalità.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Package: **com.ms.wfc.data**  
  
|Costante|  
|--------------|  
|AdoEnums.XactAttribute.ABORTRETAINING|  
|AdoEnums.XactAttribute.COMMITRETAINING|  
  
## <a name="applies-to"></a>Si applica a  
 [Proprietà attributi (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)
