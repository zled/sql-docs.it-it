---
title: Supporto del Set di caratteri nazionale | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4fceacfd-df4f-40cd-b7a2-5e5e58a5979f
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f143d37911a1375a1eebe9de04c8b509817575ec
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="national-character-set-support"></a>Supporto per set di caratteri nazionali
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Il driver JDBC supporta l'API di JDBC 4.0, che include nuovi metodi API per la conversione dei set di caratteri nazionali. Questo supporto include nuovi metodi di impostazione, richiamo e aggiornamento per **NCHAR**, **NVARCHAR**, **LONGNVARCHAR**, e **NCLOB** tipi JDBC.  
  
 Di seguito sono elencati i nuovi metodi di richiamo, impostazione e aggiornamento per supportare la conversione dei set di caratteri nazionali:  
  
-   [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md): [setNString](../../connect/jdbc/reference/setnstring-method-int-java-lang-string.md), [setNCharacterStream](../../connect/jdbc/reference/setncharacterstream-method-sqlserverpreparedstatement.md), [setNClob](../../connect/jdbc/reference/setnclob-method-sqlserverpreparedstatement.md).  
  
-   [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md): [getNClob](../../connect/jdbc/reference/getnclob-method-sqlservercallablestatement.md), [getNString](../../connect/jdbc/reference/getnstring-method-sqlservercallablestatement.md), [getNCharacterStream](../../connect/jdbc/reference/getncharacterstream-method-sqlservercallablestatement.md), [setNString](../../connect/jdbc/reference/setnstring-method-sqlservercallablestatement.md), [setNCharacterStream](../../connect/jdbc/reference/setncharacterstream-method-sqlservercallablestatement.md), [setNClob](../../connect/jdbc/reference/setnclob-method-sqlservercallablestatement.md).  
  
-   [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md): [getNClob](../../connect/jdbc/reference/getnclob-method-sqlserverresultset.md), [getNString](../../connect/jdbc/reference/getnstring-method-sqlserverresultset.md), [getNCharacterStream](../../connect/jdbc/reference/getncharacterstream-method-sqlserverresultset.md), [updateNClob](../../connect/jdbc/reference/updatenclob-method-sqlserverresultset.md), [updateNString](../../connect/jdbc/reference/updatenstring-method-sqlserverresultset.md), [updateNCharacterStream](../../connect/jdbc/reference/updatencharacterstream-method-sqlserverresultset.md).  
  
> [!NOTE]  
>  Per utilizzare questi metodi nell'applicazione, è necessario impostare il classpath per includere il file sqljdbc4.jar.  
  
 Per inviare parametri String al server in formato Unicode, le applicazioni devono utilizzare i nuovi metodi di caratteri nazionali di JDBC 4.0; o impostare il **sendStringParametersAsUnicode** proprietà di connessione su "**true**" quando si utilizzano i metodi per caratteri non nazionali. Laddove possibile, è consigliabile utilizzare i nuovi metodi per caratteri nazionali di JDBC 4.0. Per ulteriori informazioni sul **sendStringParametersAsUnicode** proprietà di connessione, vedere [impostando le proprietà di connessione](../../connect/jdbc/setting-the-connection-properties.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sui tipi di dati del Driver JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
