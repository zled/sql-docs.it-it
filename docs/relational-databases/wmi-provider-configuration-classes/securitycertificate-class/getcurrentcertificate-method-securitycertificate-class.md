---
title: Metodo GetCurrentCertificate (classe SecurityCertificate) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
apiname:
- GetCurrentCertificate Method (SecurityCertificate Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- GetCurrentCertificate method
ms.assetid: 987a2671-1801-45c4-93e6-29f883c58720
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: c0415981ff65d6ec996de2089d52548a63bb8f71
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47621579"
---
# <a name="getcurrentcertificate-method-securitycertificate-class"></a>Metodo GetCurrentCertificate (classe SecurityCertificate)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Ottiene il certificato di sicurezza corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.GetCurrentCertificate(SHA , SQLInstance)  
```  
  
## <a name="parts"></a>Parti  
 *object*  
 Oggetto della [classe SecurityCertificate](../../../relational-databases/wmi-provider-configuration-classes/securitycertificate-class/securitycertificate-class.md) che rappresenta un certificato di sicurezza.  
  
#### <a name="parameters"></a>Parametri  
  
|Parametro|Description|  
|---------------|-----------------|  
|*SHA*|Valore string (parametro di output) che specifica l'identificazione digitale SHA del certificato di sicurezza corrente dopo il completamento del metodo.|  
|*SQLInstance*|Valore string che specifica l'istanza per la quale viene richiesto il certificato.|  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Valore **uint32** che è 0 se il servizio è stato modificato correttamente, 1 se la richiesta non è supportata e qualsiasi altro numero per indicare un errore.  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione di protocolli di rete Server e le librerie di rete](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
