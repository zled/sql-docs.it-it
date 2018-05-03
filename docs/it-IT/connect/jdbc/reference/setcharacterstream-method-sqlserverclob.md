---
title: Metodo setCharacterStream (SQLServerClob) | Documenti Microsoft
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
apiname:
- SQLServerClob.setCharacterStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c02778f2-6681-4a84-a58b-2bcfac4233e4
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0e511d31aaef8dbd550472b1f9e3ebf9393643fe
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="setcharacterstream-method-sqlserverclob"></a>Metodo setCharacterStream (SQLServerClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce un flusso da utilizzare per scrivere un flusso di caratteri Unicode nell'oggetto CLOB, a partire dalla posizione specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.io.Writer setCharacterStream(long pos)  
```  
  
#### <a name="parameters"></a>Parametri  
 *POS*  
  
 Posizione in corrispondenza della quale iniziare la scrittura nell'oggetto CLOB.  
  
## <a name="return-value"></a>Valore restituito  
 Flusso in cui possono essere scritti i caratteri Unicode.  
  
## <a name="exceptions"></a>Eccezioni  
 java.sql.SQLException  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setCharacterStream viene specificato dal metodo setCharacterStream nell'interfaccia Java.SQL. Clob.  
  
 I dati di tipo carattere nell'oggetto CLOB vengono sovrascritti dal writer a partire dalla posizione specificata e possono superare la lunghezza iniziale di tale oggetto. Se si specifica un valore posizione+1, verranno aggiunti caratteri. Se si specifica un valore posizione+2 o superiore (o zero o inferiore) verrà generato un errore di posizione.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [Membri di SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [Classe SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
