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
ms.topic: conceptual
ms.assetid: 8fd5b5ef-d939-4b78-b900-5b7b6ddb3eb9
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 33f9c9daa495c26b1a1e35869016f0e7382d9d1a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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
  
  
