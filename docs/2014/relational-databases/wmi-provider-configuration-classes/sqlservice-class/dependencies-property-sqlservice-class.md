---
title: Proprietà Dependencies (classe SqlService) | Microsoft Docs
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
- Dependencies Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- Dependencies property
ms.assetid: 92d54b7e-de2f-4978-b601-0196e37cbb41
caps.latest.revision: 35
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 837b115d1a5d6eee357ae214ced6fd71b140b2d0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37255933"
---
# <a name="dependencies-property-sqlservice-class"></a>Proprietà Dependencies (classe SqlService)
  Ottiene un elenco di servizi che dipendono dal servizio a cui si fa riferimento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object  
.Dependencies [= value]  
```  
  
## <a name="parts"></a>Parti  
 *object*  
 Oggetto della [classe SqlService](sqlservice-class.md) che rappresenta il servizio.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Matrice string[] che contiene un elenco di servizi che dipendono dal servizio a cui si fa riferimento.  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Avvio e arresto di servizi](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
