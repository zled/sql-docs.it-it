---
title: Proprietà DisplayName (classe SqlService) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- DisplayName Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- DisplayName property
ms.assetid: 49c408aa-6eb4-45cd-8d5c-60f065f24f5c
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 5438ccd554023f6a942f56b81d1c0ec0d9120bec
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48124561"
---
# <a name="displayname-property-sqlservice-class"></a>Proprietà DisplayName (classe SqlService)
  Ottiene il nome visualizzato del servizio.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object  
.DisplayName [= value]  
```  
  
## <a name="parts"></a>Parti  
 *object*  
 Oggetto della [classe SqlService](sqlservice-class.md) che rappresenta il servizio.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Valore string che specifica il nome visualizzato del servizio.  
  
## <a name="remarks"></a>Note  
 La lunghezza massima della stringa è di 256 caratteri. In Gestione configurazione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] viene mantenuta la distinzione tra maiuscole e minuscole per il nome. Tuttavia, i nomi visualizzati vengono sempre confrontati senza distinzione tra maiuscole e minuscole.  
  
## <a name="example"></a>Esempio  
  
```  
mysqlservice.DisplayName = "Atdisk"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Avvio e arresto di servizi](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
