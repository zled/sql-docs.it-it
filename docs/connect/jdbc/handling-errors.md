---
title: Gestione degli errori | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8fd5b5ef-d939-4b78-b900-5b7b6ddb3eb9
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eee315022a94795dd27ae8ae7fee6cc784912bec
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 08/14/2018
ms.locfileid: "42785644"
---
# <a name="handling-errors"></a>Gestione degli errori
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Quando si usa [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], tutte le condizioni di errore del database vengono restituite all'applicazione Java come eccezioni tramite la classe [SQLServerException](../../connect/jdbc/reference/sqlserverexception-class.md). I metodi seguenti della classe SQLServerException sono ereditati da java.sql.SQLException e java.lang.Throwable. Possono essere usati per restituire informazioni specifiche sull'errore di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che si è verificato:  
  
-   getSQLState restituisce il codice di stato standard X/Open o SQL99 dell'eccezione.  
  
-   getErrorCode restituisce il numero di errore del database specifico.  
  
-   getMessage restituisce il testo completo dell'eccezione. Nel testo del messaggio di errore viene descritto il problema e spesso sono inclusi i segnaposto per le informazioni, ad esempio i nomi degli oggetti, che sono inseriti nel messaggio di errore quando viene visualizzato.  
  
-   getNextException restituisce l'oggetto SQLServerException successivo o null se non sono presenti più oggetti eccezione da restituire.  
  
 Nell'esempio seguente viene passata alla funzione una connessione aperta al database di esempio [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e viene costruita un'istruzione SQL in formato non corretto che non contiene la clausola FROM. L'istruzione viene quindi eseguita con conseguente elaborazione di un'eccezione SQL.  
  
 [!code[JDBC#HandlingErrors1](../../connect/jdbc/codesnippet/Java/handling-errors_1.java)]  
  
## <a name="see-also"></a>Vedere anche  
 [Diagnosi dei problemi relativi al driver JDBC](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  
