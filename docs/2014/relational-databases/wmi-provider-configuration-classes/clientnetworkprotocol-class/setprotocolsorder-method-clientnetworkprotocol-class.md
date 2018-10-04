---
title: Metodo SetProtocolsOrder (classe ClientNetworkProtocol) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- SetProtocolsOrder Method (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetProtocolsOrder method
ms.assetid: b86d98b9-aae4-4e74-b4da-1ec984d5c8b4
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: f78bb32e4e6a4cf7cc6f84fd6737900ea07d03c4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48075761"
---
# <a name="setprotocolsorder-method-clientnetworkprotocol-class"></a>Metodo SetProtocolsOrder (classe ClientNetworkProtocol)
  Modifica l'ordine dell'elenco di protocolli.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object  
.SetProtocolsOrder(  
ProtocolOrderList  
)  
  
```  
  
## <a name="parts"></a>Parti  
 *object*  
 A [classe ClientNetworkProtocol](clientnetworkprotocol-class.md) che rappresenta il protocollo di rete utilizzato dal client di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
#### <a name="parameters"></a>Parametri  
  
|Parametro|Description|  
|---------------|-----------------|  
|*ProtocolOrderList*|Matrice string[] che elenca i protocolli di rete del client nel nuovo ordine.|  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Valore `uint32` che è 0 se il servizio è stato modificato correttamente, 1 se la richiesta non è supportata e qualsiasi altro numero per indicare un errore.  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione di protocolli Client](http://technet.microsoft.com/library/ms181035.aspx)   
 [Configurazione di protocolli di rete Client e le librerie di rete](http://technet.microsoft.com/library/ms181035.aspx)  
  
  
