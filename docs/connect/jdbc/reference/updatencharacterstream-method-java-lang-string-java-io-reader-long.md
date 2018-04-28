---
title: Metodo stringa - lettore - lunga updateNCharacterStream) | Documenti Microsoft
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
ms.topic: article
ms.assetid: db0a96a8-248f-4664-9c13-f480f309ab91
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 42ea39aef5d6fe2284dbd3bf56bf4c64ef304922
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="updatencharacterstream-method-javalangstring-javaioreader-long"></a>Metodo updateNCharacterStream (java.lang.String, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiorna la colonna designata con un valore del flusso di caratteri, che conterrà il numero di byte specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void updateNCharacterStream(java.lang.String columnLabel,  
                                    java.io.Reader reader,  
                                    long length)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnLabel*  
  
 Oggetto **stringa** che contiene l'etichetta di colonna.  
  
 *Lettore*  
  
 Un oggetto del lettore.  
  
 *lunghezza*  
  
 Lunghezza del flusso.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo updateNCharacterStream viene specificato dal metodo updateNCharacterStream nell'interfaccia Java.SQL. ResultSet.  
  
 Questo metodo passa caratteri Unicode da un oggetto lettore selezionare **nchar**, **nvarchar (max)**, **ntext**, e **xml** colonne. L'utilizzo di questo metodo su colonne con altri tipi di dati genererà un'eccezione.  
  
 Se la lunghezza del flusso è diversa rispetto a quello specificato nel *lunghezza* parametro, il driver JDBC genera un'eccezione quando viene inserita o aggiornata la riga.  
  
 Se la lunghezza del flusso è sconosciuta, il *lunghezza* parametro può essere impostato su -1 per indicare che il driver deve accettare il flusso indipendentemente dalla lunghezza. Con sqljdbc4.jar, si consiglia di utilizzare il metodo di JDBC 4.0 [metodo updateNCharacterStream &#40;lang. String, java.io.Reader&#41; ](../../../connect/jdbc/reference/updatencharacterstream-method-java-lang-string-java-io-reader.md) se l'applicazione è richiesto aggiornare la colonna da un flusso la cui lunghezza è sconosciuto.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo updateNCharacterStream &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatencharacterstream-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
