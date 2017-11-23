---
title: "Proprietà AcceptStop (classe SqlService) | Documenti Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: wmi
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: AcceptStop Property (SqlService Class)
apilocation: sqlmgmproviderxpsp2up.mof
helpviewer_keywords: AcceptStop property
ms.assetid: bf8ffe79-4f4c-4a2d-82e5-2ae8f5d466c5
caps.latest.revision: "35"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b23092b3e4e395f0dfc4e391808b295677648029
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="acceptstop-property-sqlservice-class"></a>Proprietà AcceptStop (classe SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]Ottiene il valore della proprietà booleana che specifica se il servizio può essere arrestato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.AcceptStop [= value]  
```  
  
## <a name="parts"></a>Parti  
 *oggetto*  
 Oggetto [classe SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) oggetto che rappresenta il servizio  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Un valore booleano che specifica se il servizio può essere arrestato: **true** se il servizio può essere arrestato, o **false** se il servizio non può essere arrestato.  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="see-also"></a>Vedere anche  
 [Avvio e arresto di servizi](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
