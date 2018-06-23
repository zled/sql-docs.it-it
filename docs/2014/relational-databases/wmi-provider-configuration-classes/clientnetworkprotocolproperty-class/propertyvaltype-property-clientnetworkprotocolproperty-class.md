---
title: Proprietà PropertyValType (classe ClientNetworkProtocolProperty) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- PropertyValType Property (ClientNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- PropertyValType property
ms.assetid: 624b9bdd-ed93-4140-bd4e-00d714a2558c
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fd4238a43c5bc8a31e33bae9993c52b05e9e750b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063543"
---
# <a name="propertyvaltype-property-clientnetworkprotocolproperty-class"></a>Proprietà PropertyValType (classe ClientNetworkProtocolProperty)
  Ottiene il tipo di dati del valore archiviato nella proprietà a cui fa riferimento il valore della [proprietà PropertyIdx (classe ClientNetworkProtocolProperty)](clientnetworkprotocolproperty-class.md) .  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object  
.PropertyValType [= value]  
```  
  
## <a name="parts"></a>Parti  
 *object*  
 A [classe ClientNetworkProtocolProperty](clientnetworkprotocolproperty-class.md) che rappresenta un attributo del protocollo di rete utilizzato dal client di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Valore `uint32` che specifica il tipo di dati del valore della proprietà.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione di protocolli client](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  