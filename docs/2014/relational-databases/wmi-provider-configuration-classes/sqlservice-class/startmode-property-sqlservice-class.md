---
title: Proprietà StartMode (classe SqlService) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- StartMode Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- StartMode property
ms.assetid: c0c2c7f8-d4ae-44f2-ad8e-aecfcb7c2878
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: dbdf2e807f5f36cf8814be95cb98ec53bb813790
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48128441"
---
# <a name="startmode-property-sqlservice-class"></a>Proprietà StartMode (classe SqlService)
  Ottiene la modalità di avvio del servizio.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object  
.StartMode [= value]  
```  
  
## <a name="parts"></a>Parti  
 *object*  
 Oggetto della [classe SqlService](sqlservice-class.md) che rappresenta il servizio.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Valore uint32 che specifica la modalità del servizio.  
  
 I valori possibili sono i seguenti:  
  
 Avvio  
 Valore = 0. Servizio avviato dal caricatore del sistema operativo. Questa opzione è valida solo per i servizi del driver.  
  
 Di sistema  
 Valore = 1. Servizio avviato dal metodo `IoInitSystem`. Questa opzione è valida solo per i servizi del driver.  
  
 Automatico  
 Valore = 2. Servizio da avviare automaticamente da Gestione controllo servizi durante l'avvio del sistema.  
  
 Manuale  
 Valore = 3. Servizio da avviare da Gestione computer quando un processo chiama il metodo `StartService`.  
  
 Disabilitata  
 Valore = 4. Impossibile avviare il servizio.  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Avvio e arresto di servizi](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
