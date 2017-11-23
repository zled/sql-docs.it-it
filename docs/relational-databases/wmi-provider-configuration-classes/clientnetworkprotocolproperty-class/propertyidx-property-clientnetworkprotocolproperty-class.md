---
title: "Proprietà PropertyIdx (classe ClientNetworkProtocolProperty) | Documenti Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: wmi
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: PropertyIdx Property (ClientNetworkProtocolProperty Class)
apilocation: sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords: PropertyIdx property
ms.assetid: d7845962-ac68-4435-9c59-70ec450fec88
caps.latest.revision: "29"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5c7cc1311b307fec6cb78137c780f105e2bace24
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="propertyidx-property-clientnetworkprotocolproperty-class"></a>Proprietà PropertyIdx (classe ClientNetworkProtocolProperty)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]Ottiene o imposta il valore della proprietà di indice nella matrice di proprietà a cui fa riferimento il [proprietà Properties (classe ClientNetworkProtocol)](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/properties-property-clientnetworkprotocol-class.md) del [classe ClientNetworkProtocol](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.PropertyIdx [= value]  
```  
  
## <a name="parts"></a>Parti  
 *oggetto*  
 A [classe ClientNetworkProtocolProperty](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/clientnetworkprotocolproperty-class.md) che rappresenta un attributo del protocollo di rete utilizzato dal client di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Valore **uint32** che specifica il valore di indice della matrice della proprietà corrente.  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione di protocolli client](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  
