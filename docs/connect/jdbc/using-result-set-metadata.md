---
title: Metadati del Set di risultati con | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 5e37529a-30db-48c8-b90a-ae9657d0f6b0
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4ea7ce7da7d5327c12204d60ec5c97ec58793403
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38041417"
---
# <a name="using-result-set-metadata"></a>Utilizzo dei metadati del set di risultati
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Per eseguire una query su un set di risultati e ottenere informazioni sulle colonne in esso contenute, [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] implementa la classe [SQLServerResultSetMetaData](../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md). Questa classe contiene vari metodi che restituiscono informazioni sotto forma di singolo valore.  
  
 Per creare un oggetto SQLServerResultSetMetaData, è possibile usare la [getMetaData](../../connect/jdbc/reference/getmetadata-method-sqlserverresultset.md) metodo per il [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) classe.  
  
 Nell'esempio seguente, una connessione aperta al [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio viene passato alla funzione, viene usato il metodo getMetaData della classe SQLServerResultSet per restituire un oggetto SQLServerResultSetMetaData e quindi vari metodi del Oggetto SQLServerResultSetMetaData consentono di visualizzare informazioni sul tipo di nome e i dati delle colonne contenute nel set di risultati.  
  
 [!code[JDBC#UsingResultSetMetaData1](../../connect/jdbc/codesnippet/Java/using-result-set-metadata_1.java)]  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione dei metadati con il driver JDBC](../../connect/jdbc/handling-metadata-with-the-jdbc-driver.md)  
  
  
