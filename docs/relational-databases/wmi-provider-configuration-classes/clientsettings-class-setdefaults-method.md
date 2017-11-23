---
title: Metodo SetDefaults (classe ClientSettings) | Documenti Microsoft
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
apiname: SetDefaults Method (ClientSettings Class)
apilocation: sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords: SetDefaults method
ms.assetid: 056508f3-a5c8-467c-a196-dc1ef1f5178f
caps.latest.revision: "28"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b86a8301664f483c339f020cf0a8de5c2803749b
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="clientsettings-class---setdefaults-method"></a>Classe ClientSettings - metodo SetDefaults
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]Imposta tutti i valori predefiniti per l'istanza del [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client con l'opzione per sovrascrivere dati esistenti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.SetDefaults(OverwriteAll)  
```  
  
## <a name="parts"></a>Parti  
 *oggetto*  
 Oggetto **ClientSettings** oggetto che rappresenta un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza del client.  
  
#### <a name="parameters"></a>Parametri  
  
|Parametro|Description|  
|---------------|-----------------|  
|*OverwriteAll*|Un valore booleano che specifica se sovrascrivere valori esistenti sull'istanza del client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. **true** per sovrascrivere dati esistenti; **false** se non devono essere sovrascritti dati esistenti.|  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Valore **uint32** che è 0 se il servizio è stato modificato correttamente, 1 se la richiesta non è supportata e qualsiasi altro numero per indicare un errore.  
  
## <a name="remarks"></a>Osservazioni  
  
