---
title: Metodo getScale (SQLServerParameterMetaData) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerParameterMetaData.getScale
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7b8d8d9c-74aa-4e6e-88f1-2fc5c74004ae
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e77c6dcfd46b6fbb522312738bd24c9f4ac94fe0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32836926"
---
# <a name="getscale-method-sqlserverparametermetadata"></a>Metodo getScale (SQLServerParameterMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il numero di cifre a destra del separatore decimale per il parametro designato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int getScale(int param)  
```  
  
#### <a name="parameters"></a>Parametri  
 *param*  
  
 Un **int** che indica l'indice del parametro.  
  
## <a name="return-value"></a>Valore restituito  
 In **int** che indica la scala del parametro designato.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getScale viene specificato dal metodo getScale nell'interfaccia Java.SQL. parametermetadata.  
  
 Questo metodo ottiene le cifre della colonna a destra del separatore decimale. Per tipi che non dispongono di un separatore decimale, questo metodo restituisce "0".  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-methods.md)   
 [Membri di SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [Classe SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
