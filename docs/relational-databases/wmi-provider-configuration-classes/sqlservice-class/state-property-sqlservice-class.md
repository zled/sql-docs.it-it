---
title: Lo stato delle proprietà (classe SqlService) | Documenti Microsoft
ms.custom: ''
ms.date: 03/04/2017
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
- State Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- State property
ms.assetid: 9e09f419-947c-4d4b-9a49-2d3396c847cd
caps.latest.revision: 36
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 11f9b33244435343156fac8abb9df8d9a765ce62
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="state-property-sqlservice-class"></a>Proprietà State (classe SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Ottiene o imposta lo stato corrente del servizio.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.State [= value]  
```  
  
## <a name="parts"></a>Parti  
 *oggetto*  
 Oggetto della [classe SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) che rappresenta il servizio.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Valore uint32 che specifica lo stato del servizio.  
  
 I valori possibili sono i seguenti:  
  
 1  
 Arrestato. Il servizio è stato arrestato.  
  
 2  
 In attesa dell'avvio. Il servizio è in attesa di essere avviato.  
  
 3  
 In attesa dell'arresto. Il servizio è in attesa di essere arrestato.  
  
 4  
 In esecuzione. Il servizio è in esecuzione.  
  
 5  
 In attesa della ripresa. Il servizio è in attesa di essere ripreso.  
  
 6  
 In attesa della sospensione. Il servizio è in attesa di essere sospeso.  
  
 7  
 (sospeso) Il servizio è stato sospeso.  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="see-also"></a>Vedere anche  
 [Avvio e arresto di servizi](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
