---
title: Gestione degli errori | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8fd5b5ef-d939-4b78-b900-5b7b6ddb3eb9
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: cfcb29aa70f9bfb56c793f6fa5d1d8b31d45f8bf
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="handling-errors"></a>Gestione degli errori
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Quando si utilizza il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], tutte le condizioni di errore di database vengono restituite all'applicazione Java come eccezioni utilizzando la [SQLServerException](../../connect/jdbc/reference/sqlserverexception-class.md) classe. I seguenti metodi della classe SQLServerException sono ereditati da Java.SQL. SqlException e java.lang.Throwable; e può essere utilizzati per restituire informazioni specifiche sui [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] errore che si è verificato:  
  
-   getSQLState restituisce standard X / Open o SQL99 codice di stato dell'eccezione.  
  
-   getErrorCode restituisce il numero di errore di database specifico.  
  
-   getMessage restituisce il testo completo dell'eccezione. Nel testo del messaggio di errore viene descritto il problema e spesso sono inclusi i segnaposto per le informazioni, ad esempio i nomi degli oggetti, che sono inseriti nel messaggio di errore quando viene visualizzato.  
  
-   getNextException restituisce l'oggetto SQLServerException successivo o null se non sono più disponibili oggetti eccezione da restituire.  
  
 Nell'esempio seguente, una connessione aperta per la [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio viene passato alla funzione e viene costruita un'istruzione SQL in formato non corretto che non dispone di una clausola FROM. L'istruzione viene quindi eseguita con conseguente elaborazione di un'eccezione SQL.  
  
 [!code[JDBC#HandlingErrors1](../../connect/jdbc/codesnippet/Java/handling-errors_1.java)]  
  
## <a name="see-also"></a>Vedere anche  
 [La diagnosi di problemi con il Driver JDBC](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  
