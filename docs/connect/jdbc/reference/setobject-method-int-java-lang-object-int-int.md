---
title: Metodo setObject (int, java.lang.Object, int, int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setObject (int, java.lang.Object, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d190ee20-d669-4c6f-a081-d5cfec2f72ca
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: da06abf7222931551ca1ef9b441687837b2c65f0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47787539"
---
# <a name="setobject-method-int-javalangobject-int-int"></a>Metodo setObject (int, java.lang.Object, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il valore del parametro designato tramite l'oggetto, il tipo di destinazione e la scala specificati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final void setObject(int n,  
                            java.lang.Object obj,  
                            int targetSqlType,  
                            int scale)  
```  
  
#### <a name="parameters"></a>Parametri  
 *n*  
  
 Valore **int** che indica il numero di parametro.  
  
 *obj*  
  
 Oggetto.  
  
 *targetSqlType*  
  
 Valore **int** che indica il tipo di destinazione come definito in java.sql.Types.  
  
 *scala*  
  
 Valore **int** che indica il numero di cifre a destra del separatore decimale. Questo parametro viene ignorato per tutti i tipi diversi da NUMERIC e DECIMAL.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo setObject viene specificato dal metodo setObject nell'interfaccia java.sql.PreparedStatement.  
  
 A partire [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Driver JDBC 3.0, il comportamento di questo metodo viene modificato per il **sendTimeAsDatetime** proprietà di connessione ([impostando le proprietà di connessione](../../../connect/jdbc/setting-the-connection-properties.md)) e [ Setsendtimeasdatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md).  
  
 Per altre informazioni, vedere [Java configurazione come valori vengono inviati al Server](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo setObject &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md)   
 [Membri di SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Classe SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
