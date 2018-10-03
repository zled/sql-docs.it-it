---
title: Usando un'istruzione SQL senza parametri | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4b0728bd-059b-4b71-895c-999335bc7427
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 041a0119425e6469a394420469b14f47f3b84a81
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47674839"
---
# <a name="using-an-sql-statement-with-no-parameters"></a>Utilizzo di un'istruzione SQL senza parametri

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Per usare i dati di un database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mediante un'istruzione SQL che non contiene parametri, è possibile usare il metodo [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) della classe [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) per restituire un set di risultati [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) contenente i dati richiesti. A tale scopo, è necessario innanzitutto creare un oggetto SQLServerStatement usando il metodo [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) della classe [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md).

Nell'esempio seguente viene passata alla funzione una connessione aperta al database di esempio di [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)], viene costruita ed eseguita un'istruzione SQL, quindi i risultati vengono letti dal set di risultati.

[!code[JDBC#UsingSQLWithNoParams1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-w_0_1.java)]

Per altre informazioni sull'uso di set di risultati, vedere [gestione dei set di risultati con il Driver JDBC](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md).

## <a name="see-also"></a>Vedere anche

[Uso di istruzioni con SQL](../../connect/jdbc/using-statements-with-sql.md)
