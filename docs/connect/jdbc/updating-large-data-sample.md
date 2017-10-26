---
title: Aggiornamento dei dati di grandi dimensioni campione | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76ecc05f-a77d-40a2-bab9-91a7fcf17347
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 40444e396dd6efc166acf8b3a45611a24e40d20e
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="updating-large-data-sample"></a>Esempio di aggiornamento di dati di grandi dimensioni
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Questo [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] applicazione di esempio viene illustrato come aggiornare una colonna di grandi dimensioni in un database.  
  
 Il file di codice per questo esempio è updateLargeData.java ed è disponibile nel seguente percorso:  
  
 \<*directory di installazione*> \sqljdbc_\<*versione*>\\<*language*> \samples\adaptive  
  
## <a name="requirements"></a>Requisiti  
 Per eseguire questa applicazione di esempio, sarà necessario l'accesso per il [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio. nonché impostare il classpath per includere il file sqljdbc4.jar. Se nel classpath manca una voce per il file sqljdbc4.jar, nell'applicazione di esempio verrà generata un'eccezione comune di classe non trovata. Per ulteriori informazioni su come impostare il classpath, vedere [utilizza il Driver JDBC](../../connect/jdbc/using-the-jdbc-driver.md).  
  
> [!NOTE]  
>  Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fornisce sqljdbc.jar, sqljdbc4.jar, sqljdbc41.jar o sqljdbc42.jar classe i file di libreria da utilizzare a seconda delle impostazioni preferite di Java Runtime Environment (JRE). Questo esempio viene utilizzata la [isWrapperFor](../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md) e [unwrap](../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md) metodi, che vengono introdotti nell'API JDBC 4.0, per accedere alla risposta specifici del driver buffering metodi. Per compilare ed eseguire questo esempio, sarà necessaria la libreria di classi sqljdbc4.jar, che fornisce il supporto per JDBC 4.0. Per ulteriori informazioni sui file JAR da scegliere, vedere [requisiti di sistema per il Driver JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente, il codice di esempio stabilisce una connessione per il [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database. Quindi, il codice di esempio crea un oggetto istruzione e utilizza il [isWrapperFor](../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md) metodo per verificare se l'oggetto istruzione è un wrapper per l'oggetto specificato [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) classe. Il [unwrap](../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md) metodo viene utilizzato per accedere alla risposta specifici del driver metodi di memorizzazione nel buffer.  
  
 Quindi, il codice di esempio imposta la modalità di memorizzazione delle risposte "**adattivo**" utilizzando il [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) metodo il [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) classe nonché viene illustrato come ottenere la modalità di buffer adattivo.  
  
 Quindi, viene eseguito l'istruzione SQL e inserisce i dati restituiti vengono posizionati in un aggiornabili [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
 Viene infine eseguita un'iterazione nelle righe di dati incluse nel set di risultati. Se trova un documento vuoto riepilogo, verrà utilizzata la combinazione di [updateString](../../connect/jdbc/reference/updatestring-method-sqlserverresultset.md) e [updateRow](../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md) metodi per aggiornare la riga di dati e renderla di nuovo permanente nel database. Se è già dati, viene utilizzato il [getString](../../connect/jdbc/reference/getstring-method-sqlserverresultset.md) metodo per visualizzare alcuni dei dati in esso contenuti.  
  
 Il comportamento predefinito del driver è "**adattivo.**" Tuttavia, per i set di risultati aggiornabili forward-only e quando i dati nel set di risultati sono maggiori della memoria dell'applicazione, l'applicazione deve impostare la modalità di buffer adattivo in modo esplicito utilizzando il [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) metodo di [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) classe.  
  
 [!code[JDBC#UsingAdaptiveBuffering3](../../connect/jdbc/codesnippet/Java/updating-large-data-sample_1.java)]  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di dati di grandi dimensioni](../../connect/jdbc/working-with-large-data.md)  
  
  

