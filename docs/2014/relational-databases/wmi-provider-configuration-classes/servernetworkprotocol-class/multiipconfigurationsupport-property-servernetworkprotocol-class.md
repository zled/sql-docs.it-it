---
title: Proprietà MultiIpConfigurationSupport (classe ServerNetworkProtocol) | Documenti Microsoft
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
- MultiIpConfigurationSupport Property (ServerNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- MultiIpConfigurationSupport property
ms.assetid: 442c6133-4038-42db-a67d-2631285ac76b
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 86dbd66d4923520942f2a1196fcb4d6d9bb4d1f2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36158822"
---
# <a name="multiipconfigurationsupport-property-servernetworkprotocol-class"></a>Proprietà MultiIpConfigurationSupport (classe ServerNetworkProtocol)
  Ottiene la proprietà booleana che specifica se più indirizzi IP sono supportati da un protocollo di rete del server.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object  
.MultiIpConfigurationSupport [= value]  
```  
  
## <a name="parts"></a>Parti  
 *object*  
 Un [proprietà ProtocolName (classe ServerNetworkProtocol)](servernetworkprotocol-class.md) oggetto che rappresenta il protocollo di rete utilizzato dall'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Valore booleano che specifica se più indirizzi IP sono supportati dal protocollo di rete del server. `true` se più indirizzi IP sono supportati dal protocollo di rete del server; `false` se più indirizzi IP non sono supportati dal protocollo di rete del server.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione di protocolli di rete Server e librerie di rete](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  