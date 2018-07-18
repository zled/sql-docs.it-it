---
title: Metodo SetDefaults (classe CInstance) | Microsoft Docs
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
- SetDefaults Method (CInstance Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDefaults method
ms.assetid: ed9e99c2-3e28-4ee8-bc20-61ca05984973
caps.latest.revision: 32
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: c17a12c4fa35594482599491071f8342c2118ccf
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37157992"
---
# <a name="setdefaults-method-cinstance-class"></a>Metodo SetDefaults (classe CInstance)
  Imposta tutti i valori predefiniti per l'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client con l'opzione per sovrascrivere dati esistenti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object  
.SetDefaults(  
OverwriteAll  
)  
  
```  
  
## <a name="parts"></a>Parti  
 *object*  
 Oggetto della [classe CInstance](cinstance-class.md) che rappresenta un'istanza del client di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
#### <a name="parameters"></a>Parametri  
  
|Parametro|Description|  
|---------------|-----------------|  
|*OverwriteAll*|Valore booleano che specifica se sovrascrivere i valori esistenti nell'istanza del client di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. `true` per sovrascrivere i dati esistenti; `false` se i dati esistenti non devono essere sovrascritti.|  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Valore `uint32` che è 0 se il servizio è stato modificato correttamente, 1 se la richiesta non è supportata e qualsiasi altro numero per indicare un errore.  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione di protocolli client](http://technet.microsoft.com/library/ms181035.aspx)  
  
  
