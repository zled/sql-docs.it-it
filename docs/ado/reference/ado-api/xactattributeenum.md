---
title: XactAttributeEnum | Documenti Microsoft
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
- XactAttributeEnum
helpviewer_keywords:
- XactAttributeEnum enumeration [ADO]
ms.assetid: e7dcecd3-7dc7-445c-b922-f700c3067fbc
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c99e449171b347290f832950f265c6579ba6a630
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35283210"
---
# <a name="xactattributeenum"></a>XactAttributeEnum
Specifica gli attributi della transazione di un [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto.  
  
|Costante|valore|Description|  
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
