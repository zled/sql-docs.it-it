---
title: Proprietà PropertyValType (classe ServerNetworkProtocolProperty) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: wmi
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PropertyValType Property (ServerNetworkProtocolProperty Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- PropertyValType property
ms.assetid: fbd42e8e-0642-4a19-b3c8-6ce88345145f
caps.latest.revision: 30
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 382f8eefd2bdc19021c561edc07aba29eaade38b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="propertyvaltype-property-servernetworkprotocolproperty-class"></a>Proprietà PropertyValType (classe ServerNetworkProtocolProperty)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Ottiene il tipo di dati del valore archiviato nella proprietà a cui si fa riferimento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.PropertyValType [= value]  
```  
  
## <a name="parts"></a>Parti  
 *oggetto*  
 A [classe ServerNetworkProtocolProperty](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocolproperty-class/servernetworkprotocolproperty-class.md) che rappresenta un attributo del protocollo di rete nell'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Valore **uint32** che specifica il tipo di dati del valore della proprietà. Viene restituito 0 per un valore string e 1 per un tipo numerico.  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione di protocolli di rete Server e le librerie di rete](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
