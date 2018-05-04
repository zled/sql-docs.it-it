---
title: Proprietà ProtocolDLL (classe ClientNetworkProtocol) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: wmi
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ProtocolDLL Property (ClientNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ProtocolDLL property
ms.assetid: fe8650d5-7b9d-46f8-bf74-baf1d9d2a06a
caps.latest.revision: 35
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 895086e2164f6766cc6c83d63521c95c062321c6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="protocoldll-property-clientnetworkprotocol-class"></a>Proprietà ProtocolDLL (classe ClientNetworkProtocol)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Ottiene il nome del file con estensione dll richiesto dal protocollo di rete specificato dalla [configurazione di protocolli client](http://technet.microsoft.com/library/ms181035.aspx).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.ProtocolDLL [= value]  
```  
  
## <a name="parts"></a>Parti  
 *oggetto*  
 A [classe ClientNetworkProtocol](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md) che rappresenta il protocollo di rete utilizzato dal client di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Valore string che specifica il file con estensione dll del protocollo richiesto dal protocollo di rete del client.  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione di protocolli di rete Client e le librerie di rete](http://technet.microsoft.com/library/ms181035.aspx)  
  
  
