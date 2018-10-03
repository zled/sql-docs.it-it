---
title: Proprietà AcceptPause (classe SqlService) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- AcceptPause Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- AcceptPause property
ms.assetid: 4339e903-35ee-4395-b005-ca58b3a24a84
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: a0efdc0cf758bf57ea46932e54ccbd7150713483
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48173131"
---
# <a name="acceptpause-property-sqlservice-class"></a>Proprietà AcceptPause (classe SqlService)
  Ottiene il valore della proprietà booleana che specifica se il servizio può essere sospeso.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object  
.AcceptPause [= value]  
```  
  
## <a name="parts"></a>Parti  
 *object*  
 Oggetto della [classe SqlService](sqlservice-class.md) che rappresenta il servizio.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Un valore booleano che specifica se il servizio può essere sospeso. `true` se il servizio può essere sospeso; `false` se il servizio non può essere sospeso.  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Avvio e arresto di servizi](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
