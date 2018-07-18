---
title: Proprietà NumberOfProps (classe ClientNetworkProtocol) | Documenti Microsoft
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
- NumberOfProps Property (ClientNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- NumberOfProps property
ms.assetid: 9c508bc5-c7a4-4db1-b3bf-c7098c66435a
caps.latest.revision: 34
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 77baccff2e4748929ab4751f4080a164311543c5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33012708"
---
# <a name="numberofprops-property-clientnetworkprotocol-class"></a>Proprietà NumberOfProps (classe ClientNetworkProtocol)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Ottiene il numero di proprietà del client specificato dal protocollo di rete di [metodo SetOrderValue (classe ClientNetworkProtocol)](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/setordervalue-method-clientnetworkprotocol-class.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.NumberOfProps [= value]  
```  
  
## <a name="parts"></a>Parti  
 *oggetto*  
 Oggetto della [classe ClientNetworkProtocol](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md) che rappresenta il protocollo di rete utilizzato dal client di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Valore uint32 che specifica il numero di proprietà del protocollo di rete del client.  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare i protocolli client](http://technet.microsoft.com/library/ms181035.aspx)  
  
  
