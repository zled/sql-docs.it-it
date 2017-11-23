---
title: Metodo SetDefaults (classe CInstance) | Documenti Microsoft
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
apiname: SetDefaults Method (CInstance Class)
apilocation: sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords: SetDefaults method
ms.assetid: ed9e99c2-3e28-4ee8-bc20-61ca05984973
caps.latest.revision: "32"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 744bfa80ab7207dc8b9178f4266b58ce7328d1c5
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="cinstance-class---setdefaults-method"></a>Classe CInstance - metodo SetDefaults
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]Imposta tutti i valori predefiniti per l'istanza del [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client con l'opzione per sovrascrivere dati esistenti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.SetDefaults(OverwriteAll)  
```  
  
## <a name="parts"></a>Parti  
 *oggetto*  
 Oggetto della [classe CInstance](../../relational-databases/wmi-provider-configuration-classes/cinstance-class.md) che rappresenta un'istanza del client di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
#### <a name="parameters"></a>Parametri  
  
|Parametro|Description|  
|---------------|-----------------|  
|*OverwriteAll*|Un valore booleano che specifica se sovrascrivere valori esistenti nell'istanza del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client: **true** per sovrascrivere dati esistenti, o **false** se non devono essere sovrascritti dati esistenti.|  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Valore **uint32** che è 0 se il servizio è stato modificato correttamente, 1 se la richiesta non è supportata e qualsiasi altro numero per indicare un errore.  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione di protocolli client](http://technet.microsoft.com/library/ms181035.aspx)  
  
  
