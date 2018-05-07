---
title: Utilizzo di un'istruzione SQL con parametri | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3202b88f-ce13-44dd-982c-c6a3b0260378
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 35f23003f62ab9ea0188d54d7c4ad08d094eb440
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="using-an-sql-statement-with-parameters"></a>Utilizzo di istruzioni SQL con parametri
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Per utilizzare i dati in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database utilizzando un'istruzione SQL contenente parametri IN, è possibile utilizzare il [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md) metodo il [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) classe per restituire un [ SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) che conterrà i dati richiesti. A tale scopo, è innanzitutto necessario creare un oggetto SQLServerPreparedStatement utilizzando il [prepareStatement](../../connect/jdbc/reference/preparestatement-method-sqlserverconnection.md) metodo il [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) classe.  
  
 Quando si costruisce l'istruzione SQL, i parametri IN sono specificati utilizzando il carattere ? (punto interrogativo), il quale funge da segnaposto per i valori dei parametri che verranno successivamente passati all'istruzione SQL. Per specificare un valore per un parametro, è possibile utilizzare uno dei metodi setter della classe SQLServerPreparedStatement. Il metodo Set da utilizzare dipende dal tipo di dati del valore che si desidera passare all'istruzione SQL.  
  
 Quando si passa un valore al metodo Set, è necessario specificare non solo il valore effettivo da utilizzare nell'istruzione SQL, ma anche la posizione ordinale del parametro nell'istruzione stessa. Ad esempio, se l'istruzione SQL contiene un singolo parametro, il valore ordinale sarà 1. Se l'istruzione contiene due parametri, il primo valore ordinale sarà 1, mentre il secondo valore ordinale sarà 2.  
  
 Nell'esempio seguente, una connessione aperta per la [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio viene passato alla funzione, un'istruzione SQL preparata viene costruita ed eseguita con un singolo valore di parametro di stringa e quindi i risultati vengono letti dal set di risultati.  
  
 [!code[JDBC#UsingSQLWithParams1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-w_1_1.java)]  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di istruzioni con SQL](../../connect/jdbc/using-statements-with-sql.md)  
  
  
