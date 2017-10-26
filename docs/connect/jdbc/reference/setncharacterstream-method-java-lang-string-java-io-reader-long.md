---
title: Metodo setNCharacterStream all'oggetto lettore - lungo | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af9a1ba8-7980-43fa-88e5-14f6cc5e897c
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f47eb454958dce0e41a3f864c54581b202f44e1c
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="setncharacterstream-method-javalangstring-javaioreader-long"></a>Metodo setNCharacterStream (java.lang.String, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il parametro designato per l'oggetto Reader specificato, ovvero il numero specificato di caratteri.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final void setNCharacterStream(java.lang.String parameterName,  
                     java.io.Reader value,  
                     long length)  
```  
  
#### <a name="parameters"></a>Parametri  
 *parameterName*  
  
 Oggetto **stringa** che indica il nome del parametro.  
  
 *Valore*  
  
 Un oggetto del lettore.  
  
 *length*  
  
 Oggetto **lungo** che indica il numero di caratteri nel flusso.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setNCharacterStream viene specificato dal metodo setNCharacterStream nell'interfaccia Java.SQL. CallableStatement.  
  
 Questo metodo deve essere utilizzato per **NCHAR**, **NVARCHAR**, **NTEXT**, e **XML** tipi di dati.  
  
 Se la lunghezza del flusso è diversa rispetto a quello specificato nel *lunghezza* parametro, il driver JDBC genera un'eccezione quando viene inserita o aggiornata la riga.  
  
 Se la lunghezza del flusso è sconosciuta, il *lunghezza* parametro può essere impostato su -1 per indicare che il driver deve accettare il flusso indipendentemente dalla lunghezza. Con sqljdbc4.jar, si consiglia di utilizzare il metodo di JDBC 4.0 [setNCharacterStream metodo &#40;java.lang.String, Java.IO. Reader &#41;](../../../connect/jdbc/reference/setncharacterstream-method-java-lang-string-java-io-reader.md) quando l'applicazione deve aggiornare la colonna da un flusso la cui lunghezza è sconosciuto.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo setNCharacterStream &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/setncharacterstream-method-sqlservercallablestatement.md)   
 [Membri di SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  

