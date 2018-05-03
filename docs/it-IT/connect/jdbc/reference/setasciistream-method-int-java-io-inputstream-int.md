---
title: Metodo setAsciiStream (int, Java.IO. InputStream, int) | Documenti Microsoft
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
- SQLServerPreparedStatement.setAsciiStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9436c39f-f1a1-484a-a75b-776a72ca70f4
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 18d3dd269f8713305559994d15a76ab324a2c412
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="setasciistream-method-int-javaioinputstream-int"></a>Metodo setAsciiStream (int, java.io.InputStream, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il numero di parametro designato sull'oggetto InputStream specificato con il numero specificato di byte.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final void setAsciiStream(int n,  
                                 java.io.InputStream x,  
                                 int length)  
```  
  
#### <a name="parameters"></a>Parametri  
 *n*  
  
 Un **int** che indica il numero di parametro.  
  
 *x*  
  
 Un oggetto InputStream.  
  
 *lunghezza*  
  
 Numero di byte.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setAsciiStream viene specificato dal metodo setAsciiStream nell'interfaccia Java.SQL. PreparedStatement.  
  
 Se la lunghezza del flusso è diversa rispetto a quella specificata nel *lunghezza* parametro, il driver JDBC genera un'eccezione quando viene inserita o aggiornata la riga.  
  
 Se la lunghezza del flusso è sconosciuta, il *lunghezza* parametro può essere impostato su -1 per indicare che il driver deve accettare il flusso indipendentemente dalla lunghezza. Con sqljdbc4.jar, si consiglia di utilizzare il metodo di JDBC 4.0 [metodo setAsciiStream &#40;int. InputStream&#41; ](../../../connect/jdbc/reference/setasciistream-method-int-java-io-inputstream.md) se l'applicazione è richiesto aggiornare la colonna da un flusso la cui lunghezza è sconosciuta.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo setAsciiStream &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setasciistream-method-sqlserverpreparedstatement.md)   
 [Membri di SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
