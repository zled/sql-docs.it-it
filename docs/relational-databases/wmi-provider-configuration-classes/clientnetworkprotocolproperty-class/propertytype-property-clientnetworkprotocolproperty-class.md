---
title: Proprietà PropertyType (classe ClientNetworkProtocolProperty) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
apiname:
- PropertyType Property (ClientNetworkProtocolProperty Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- PropertyType property
ms.assetid: fc0e4725-979f-4517-a8f5-25436b87f5c2
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 62e398c91d8752877d6417065a0a39af4e1505f0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47776779"
---
# <a name="propertytype-property-clientnetworkprotocolproperty-class"></a>Proprietà PropertyType (classe ClientNetworkProtocolProperty)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Ottiene il tipo della proprietà a cui fanno riferimento le [proprietà PropertyIdx (classe ClientNetworkProtocolProperty)](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/propertyidx-property-clientnetworkprotocolproperty-class.md) valore.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.PropertyType [= value]  
```  
  
## <a name="parts"></a>Parti  
 *object*  
 A [classe ClientNetworkProtocolProperty](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/clientnetworkprotocolproperty-class.md) che rappresenta un attributo del protocollo di rete utilizzato dal client di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Oggetto **uint32** valore che specifica il tipo della proprietà.  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione di protocolli client](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  
