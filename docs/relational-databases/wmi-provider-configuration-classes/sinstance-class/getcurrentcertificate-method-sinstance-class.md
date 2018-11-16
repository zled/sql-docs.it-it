---
title: Metodo GetCurrentCertificate (classe SInstance) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- GetCurrentCertificate Method (SInstance Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- GetCurrentCertificate method
ms.assetid: 9d2b72df-cb21-414a-abef-917f13d4de62
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 044573e2cfd6cc9851ad7af5d850dc9b089c9363
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51666010"
---
# <a name="getcurrentcertificate-method-sinstance-class"></a>Metodo GetCurrentCertificate (classe SInstance)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Ottiene il certificato di sicurezza corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.GetCurrentCertificate(SHA)  
```  
  
## <a name="parts"></a>Parti  
 *object*  
 Oggetto della [classe SInstance](../../../relational-databases/wmi-provider-configuration-classes/sinstance-class/sinstance-class.md) che rappresenta le impostazioni del server in un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
#### <a name="parameters"></a>Parametri  
  
|Parametro|Description|  
|---------------|-----------------|  
|*SHA*|Valore oggetto stringa (parametro di output) che specifica il certificato di sicurezza corrente dopo il completamento del metodo.|  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Valore **uint32** che è 0 se il servizio è stato modificato correttamente, 1 se la richiesta non è supportata e qualsiasi altro numero per indicare un errore.  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione di protocolli di rete Server e le librerie di rete](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
