---
title: Metodo updateNClob (int, java.sql.NClob) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6e9bca18-f64e-46a4-8541-2c9c39b393b5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bd3bf43488ee033969d2d74e66960b729440eed6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47811239"
---
# <a name="updatenclob-method-int-javasqlnclob"></a>Metodo updateNClob (int, java.sql.NClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiorna la colonna designata con un valore **NClob**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void updateNClob(int columnIndex,  
                        java.sql.NClob nClob)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnIndex*  
  
 Valore **int** che indica l'indice di colonna.  
  
 *nClob*  
  
 Un oggetto NClob.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo updateNClob viene specificato dal metodo updateNClob nell'interfaccia ResultSet.  
  
 Questo metodo è supportato solo sul **nvarchar (max)**, **ntext**, e **xml** colonne. L'utilizzo di questo metodo su qualsiasi altro tipo di dati genererà un'eccezione.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo updateNClob &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatenclob-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
