---
title: Metodo setXopenStates (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setXopenStates
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9723591f-e987-426f-b70a-07f5c70dc094
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 65fde7feacb27f8c3b7fb2d809de4f75bc7e899c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47695869"
---
# <a name="setxopenstates-method-sqlserverdatasource"></a>Metodo setXopenStates (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta un valore **Boolean** che indica se la conversione di stati SQL in stati conformi a XOPEN è abilitata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setXopenStates(boolean xopenStates)  
```  
  
#### <a name="parameters"></a>Parametri  
 *xopenStates*  
  
 **true** se la conversione di stati SQL in stati conformi a XOPEN è abilitata. In caso contrario, **false**.  
  
## <a name="remarks"></a>Remarks  
 Se la proprietà xopenStates è impostata su **true**, gli stati SQL vengono convertiti in stati conformi a XOPEN da [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. L'impostazione predefinita è **false** e determina la generazione dei codici di stato SQL 99 da parte del driver JDBC. Se la proprietà xopenStates non è impostata, il metodo [getXopenStates](../../../connect/jdbc/reference/getxopenstates-method-sqlserverdatasource.md) restituisce il valore predefinito **false**.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
