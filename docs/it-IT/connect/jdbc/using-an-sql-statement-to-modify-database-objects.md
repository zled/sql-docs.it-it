---
title: Utilizzo di un'istruzione SQL per modificare gli oggetti di Database | Documenti Microsoft
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
ms.assetid: f49ea499-df3c-4e85-9fc7-450fb99622a6
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 809ad678f6257e7e2cdc4af5915f5d4902a5c144
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="using-an-sql-statement-to-modify-database-objects"></a>Utilizzo di un'istruzione SQL per modificare gli oggetti di database
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Per modificare [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oggetti di database utilizzando un'istruzione SQL, è possibile utilizzare il [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md) metodo il [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) classe. Il metodo executeUpdate verrà passerà l'istruzione SQL al database per l'elaborazione e quindi restituire un valore pari a 0, perché nessuna riga è interessata.  
  
 A tale scopo, è innanzitutto necessario creare un oggetto SQLServerStatement utilizzando il [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) metodo il [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) classe.  
  
> [!NOTE]  
>  Le istruzioni SQL che modificano gli oggetti presenti in un database vengono definite istruzioni DDL (Data Definition Language) e includono, ad esempio, CREATE TABLE, DROP TABLE, CREATE INDEX e DROP INDEX. Per ulteriori informazioni sui tipi di istruzioni DDL supportati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], vedere [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione in linea.  
  
 Nell'esempio seguente, una connessione aperta per la [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio viene passato alla funzione, viene costruita un'istruzione SQL che creerà l'oggetto semplice TestTable nel database, quindi viene eseguita l'istruzione e viene visualizzato il valore restituito.  
  
 [!code[JDBC#UsingSQLToModifyDBObjects1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-t_0_1.java)]  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di istruzioni con SQL](../../connect/jdbc/using-statements-with-sql.md)  
  
  
