---
title: Lettura di dati di grandi dimensioni campione | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6c986144-3854-4352-8331-e79eccbefc28
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d75c6fcf4148a4aa27dee51300d41a8c42e80acf
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="reading-large-data-sample"></a>Esempio di lettura di dati di grandi dimensioni
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Questo [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] applicazione di esempio viene illustrato come recuperare un valore di colonna singola di grandi dimensioni da un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] database utilizzando il [getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md) metodo.  
  
 Il file di codice per questo esempio è readLargeData.java ed è disponibile nel seguente percorso:  
  
 \<*directory di installazione*> \sqljdbc_\<*versione*>\\<*language*> \samples\adaptive  
  
## <a name="requirements"></a>Requisiti  
 Per eseguire questa applicazione di esempio, sarà necessario l'accesso per il [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] database di esempio. nonché impostare il classpath per includere il file sqljdbc.jar o sqljdbc4.jar. Se nel classpath manca una voce per il file sqljdbc.jar o sqljdbc4.jar, nell'applicazione di esempio verrà generata un'eccezione comune di classe non trovata. Per ulteriori informazioni su come impostare il classpath, vedere [utilizza il Driver JDBC](../../../connect/jdbc/using-the-jdbc-driver.md).  
  
> [!NOTE]  
>  Il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] fornisce sqljdbc.jar e sqljdbc4.jar file della libreria di classe da utilizzare a seconda delle impostazioni preferite di Java Runtime Environment (JRE). Per ulteriori informazioni sui file JAR da scegliere, vedere [requisiti di sistema per il Driver JDBC](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente, il codice di esempio stabilisce una connessione per il [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] database. Tramite il codice di esempio vengono quindi creati i dati di esempio e viene aggiornata la tabella Production.Document utilizzando una query con parametri.  
  
 Inoltre, il codice di esempio viene illustrato come ottenere la modalità di buffer adattivo utilizzando il [getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md) metodo il [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) classe. A partire da Microsoft JDBC Driver versione 2.0, il valore predefinito della proprietà di connessione responseBuffering è "adaptive".  
  
 Quindi, usando un'istruzione SQL con il [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) dell'oggetto, il codice di esempio esegue l'istruzione SQL e inserisce i dati restituiti vengono posizionati in un [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
 Infine, scorrere le righe di dati contenuti nel set di risultati, il codice di esempio e Usa il [getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md) metodo per accedere ad alcuni dei dati in esso contenuti.  
  
 [!code[JDBC#UsingAdaptiveBuffering1](../../../connect/jdbc/codesnippet/Java/reading-large-data-sample_1.java)]  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di dati di grandi dimensioni](../../../connect/jdbc/working-with-large-data.md)  
  
  
