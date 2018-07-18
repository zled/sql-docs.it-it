---
title: Proprietà StartMode (classe SqlService) | Documenti Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: wmi
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- StartMode Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- StartMode property
ms.assetid: c0c2c7f8-d4ae-44f2-ad8e-aecfcb7c2878
caps.latest.revision: 36
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: d5f9ba82b7ef75fa9b2a6fff80dab8e0180d59f5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33011418"
---
# <a name="startmode-property-sqlservice-class"></a>Proprietà StartMode (classe SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Ottiene la modalità di avvio del servizio.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.StartMode [= value]  
```  
  
## <a name="parts"></a>Parti  
 *oggetto*  
 Oggetto della [classe SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) che rappresenta il servizio.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Valore uint32 che specifica la modalità del servizio.  
  
 I valori possibili sono i seguenti:  
  
 Avvio  
 Valore = 0. Servizio avviato dal caricatore del sistema operativo. Questa opzione è valida solo per i servizi del driver.  
  
 Sistema  
 Valore = 1. Servizio avviato dal **IoInitSystem** metodo. Questa opzione è valida solo per i servizi del driver.  
  
 Automatico  
 Valore = 2. Servizio da avviare automaticamente da Gestione controllo servizi durante l'avvio del sistema.  
  
 Manual  
 Valore = 3. Servizio avviato da Gestione Computer quando un processo chiama il **StartService** metodo.  
  
 Disabilitata  
 Valore = 4. Impossibile avviare il servizio.  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="see-also"></a>Vedere anche  
 [Avvio e arresto di servizi](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
