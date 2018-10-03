---
title: Proprietà ErrorControl (classe SqlService) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- ErrorControl Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ErrorControl property
ms.assetid: cbb1e0fa-5bfc-4b1b-a6ed-f7d5cfad4d73
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 83955510a18a2fbc77be5aeb7005704852f0e4a0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48135881"
---
# <a name="errorcontrol-property-sqlservice-class"></a>Proprietà ErrorControl (classe SqlService)
  Ottiene o imposta la gravità dell'errore se il servizio non viene avviato durante l'avvio del computer.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object  
.ErrorControl [= value]  
```  
  
## <a name="parts"></a>Parti  
 *object*  
 Oggetto della [classe SqlService](sqlservice-class.md) che rappresenta il servizio.  
  
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
  
## <a name="remarks"></a>Note  
 Il valore indica l'azione intrapresa dal programma di avvio in caso di errore. Tutti gli errori vengono registrati dal computer.  
  
## <a name="see-also"></a>Vedere anche  
 [Avvio e arresto di servizi](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
