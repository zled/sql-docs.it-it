---
title: Gestione degli errori | Documenti Microsoft
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
ms.assetid: 8fd5b5ef-d939-4b78-b900-5b7b6ddb3eb9
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4a5a30d85dedb8de9d5cbfcff1714731c04fcd66
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
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
 [Diagnosi dei problemi relativi al driver JDBC](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  
