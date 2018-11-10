---
title: Proprietà (classe ServerNetworkProtocol) Enabled | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- Enabled Property (ServerNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- Enabled property
ms.assetid: a514822a-91f1-4aca-9175-2b96cff29700
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 0295185734443d1bd1e66d1a07543fa4fc2f0b34
ms.sourcegitcommit: 6c9d35d03c1c349bc82b9ed0878041d976b703c6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2018
ms.locfileid: "51217839"
---
# <a name="enabled-property-servernetworkprotocol-class"></a>Proprietà Enabled (classe ServerNetworkProtocol)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Ottiene la proprietà booleana che specifica se il protocollo di rete del server è abilitato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.Enabled [= value]  
```  
  
## <a name="parts"></a>Parti  
 *object*  
 A [classe ServerNetworkProtocol](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocol-class/servernetworkprotocol-class.md) che rappresenta il protocollo di rete utilizzato dall'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Valore booleano che specifica se il protocollo di rete del server è abilitato. **true** se il protocollo di rete del server è abilitato; **false** se il protocollo di rete del server è disabilitato.  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione di protocolli di rete Server e le librerie di rete](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
