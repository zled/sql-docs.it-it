---
title: Proprietà SupportAlias (classe ClientNetworkProtocol) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- SupportAlias Property (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SupportAlias property
ms.assetid: 1e7a2e87-c356-40a6-a6d9-e492467629f9
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 2bfb677ba05bc5303c706d65dd2dda70eb67d23d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48082571"
---
# <a name="supportalias-property-clientnetworkprotocol-class"></a>Proprietà SupportAlias (classe ClientNetworkProtocol)
  Ottiene la proprietà booleana che specifica se l'oggetto corrente protocollo di rete specificato per il [metodo SetOrderValue (classe ClientNetworkProtocol)](clientnetworkprotocol-class.md) supporta gli alias.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object  
.SupportAlias [= value]  
```  
  
## <a name="parts"></a>Parti  
 *object*  
 Oggetto della [classe ClientNetworkProtocol](clientnetworkprotocol-class.md) che rappresenta il protocollo di rete utilizzato dal client di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Valore booleano che specifica se il protocollo di rete del client supporta gli alias.  
  
 Se True, il protocollo di rete del client supporta gli alias.  
  
 Se False, il protocollo di rete del client non supporta gli alias.  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione di protocolli client](http://technet.microsoft.com/library/ms181035.aspx)  
  
  
