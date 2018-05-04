---
title: Metodo RemoveCertificate (classe ServerSettings) | Documenti Microsoft
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
- RemoveCertificate Method (ServerSettings Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- RemoveCertificate method
ms.assetid: 9ffdbc39-93f5-48fb-859a-86a3ad545827
caps.latest.revision: 14
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 35104a8d2252b2755940615aff2c6e8294eac3d8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="removecertificate-method-serversettings-class"></a>Metodo RemoveCertificate (classe ServerSettings)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Rimuove il certificato di sicurezza corrente dall'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.RemoveCertificate()  
```  
  
## <a name="parts"></a>Parti  
 *oggetto*  
 Oggetto della [classe ServerSettings](../../../relational-databases/wmi-provider-configuration-classes/serversettings-class/serversettings-class.md) che rappresenta le impostazioni del server in un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Valore u**int32** che è 0 se il servizio è stato modificato correttamente, 1 se la richiesta non è supportata e qualsiasi altro numero per indicare un errore.  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione di protocolli di rete Server e le librerie di rete](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
