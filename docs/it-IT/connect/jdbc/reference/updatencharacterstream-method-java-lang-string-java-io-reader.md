---
title: Metodo updateNCharacterStream (lang, Java.IO. Reader) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 504d7d06-0227-45e1-8b01-899c3e6006e8
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f60fdb2b8c2465916f403447f6dcb32377236753
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="updatencharacterstream-method-javalangstring-javaioreader"></a>Metodo updateNCharacterStream (java.lang.String, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiorna la colonna designata con un valore del flusso di caratteri.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void updateNCharacterStream(java.lang.String columnLabel,  
                                  java.io.Reader reader)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnLabel*  
  
 Oggetto **stringa** che contiene l'etichetta di colonna.  
  
 *Lettore*  
  
 Un oggetto del lettore.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo updateNCharacterStream viene specificato dal metodo updateNCharacterStream nell'interfaccia Java.SQL. ResultSet.  
  
 Questo metodo passa caratteri Unicode da un oggetto lettore selezionare **nchar**, **nvarchar (max)**, **ntext** e **xml** colonne. L'utilizzo di questo metodo su colonne con altri tipi di dati genererà un'eccezione.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo updateNCharacterStream &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatencharacterstream-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
