---
title: Proprietà ErrorControl (classe SqlService) | Documenti Microsoft
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
- ErrorControl Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ErrorControl property
ms.assetid: cbb1e0fa-5bfc-4b1b-a6ed-f7d5cfad4d73
caps.latest.revision: 34
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4a5dc8a89c6f29045281d33d3c60fdbf1f515e9b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="errorcontrol-property-sqlservice-class"></a>Proprietà ErrorControl (classe SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Ottiene o imposta la gravità dell'errore se il servizio non viene avviato durante l'avvio del computer.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.ErrorControl [= value]  
```  
  
## <a name="parts"></a>Parti  
 *oggetto*  
 Oggetto della [classe SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) che rappresenta il servizio.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Valore string che specifica la gravità dell'errore riportato se il servizio non viene avviato durante l'avvio del computer. Nella tabella seguente sono illustrati i possibili valori.  
  
 Ignore  
 L'utente non viene notificato.  
  
 Normale  
 L'utente viene notificato.  
  
 Severe  
 Il sistema viene riavviato con l'ultima configurazione valida nota.  
  
 Critico  
 Il sistema tenta un riavvio con una configurazione valida.  
  
 Unknown  
 La gravità è sconosciuta.  
  
## <a name="remarks"></a>Osservazioni  
 Il valore indica l'azione intrapresa dal programma di avvio in caso di errore. Tutti gli errori vengono registrati dal computer.  
  
## <a name="see-also"></a>Vedere anche  
 [Avvio e arresto di servizi](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
