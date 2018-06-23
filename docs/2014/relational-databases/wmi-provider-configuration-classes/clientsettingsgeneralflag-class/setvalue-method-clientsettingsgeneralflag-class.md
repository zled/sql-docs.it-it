---
title: Metodo SetValue (classe ClientSettingsGeneralFlag) | Documenti Microsoft
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
- SetValue Method (ClientSettingsGeneralFlag Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetValue method
ms.assetid: 34443689-a0e0-4668-a811-17532c6fd271
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3548492e83a9e9273901d9107ec2a1cd6fc8e80b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36054298"
---
# <a name="setvalue-method-clientsettingsgeneralflag-class"></a>Metodo SetValue (classe ClientSettingsGeneralFlag)
  Imposta tutti i valori del flag a cui si fa riferimento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object  
.SetValue(  
Value  
)  
  
```  
  
## <a name="parts"></a>Parti  
 *object*  
 Oggetto della [classe ClientSettingsGeneralFlag](clientsettingsgeneralflag-class.md) che rappresenta un flag generale per le impostazioni del server.  
  
#### <a name="parameters"></a>Parametri  
  
|Parametro|Description|  
|---------------|-----------------|  
|*Valore*|Valore booleano che specifica il valore del flag.|  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Valore `uint32` che è 0 se il servizio è stato modificato correttamente, 1 se la richiesta non è supportata e qualsiasi altro numero per indicare un errore.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione di protocolli client](http://technet.microsoft.com/library/ms181035.aspx)  
  
  