---
title: Esempio del tipo di dati SQLXML | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8f2ff25b-71fd-46d7-b6de-d656095d2aad
caps.latest.revision: 21
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 35259e7c9f6bc0129933117b0202b4ec61e52010
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlxml-data-type-sample"></a>Esempio di tipo di dati SQLXML
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Questo [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] applicazione di esempio illustra come archiviare dati XML in un database relazionale, come recuperare i dati XML da un database e come analizzare i dati XML con il **SQLXML** tipo di dati Java.  
  
 Negli esempi di codice di questa sezione viene utilizzato un parser Simple API for XML (SAX). SAX è uno standard sviluppato pubblicamente per l'analisi di documenti XML basata su eventi, che offre inoltre un'API per la gestione dei dati XML. Si noti che nelle applicazioni è possibile utilizzare anche altri parser XML, ad esempio Document Object Model (DOM), Streaming API for XML (StAX) o altri.  
  
 DOM fornisce una rappresentazione a livello di programmazione di documenti, frammenti, nodi e set di nodi XML, che offre inoltre un'API per la gestione dei dati XML. Analogamente, StAX è un'API basata su Java per l'analisi di tipo pull di codice XML.  
  
> [!IMPORTANT]  
>  Per poter utilizzare l'API del parser SAX, è necessario importare l'implementazione standard di SAX dal pacchetto javax.xml.  
  
 Il file di codice per questo esempio è sqlxmlExample.java ed è disponibile nel seguente percorso:  
  
 \<*directory di installazione*> \sqljdbc_\<*versione*>\\<*language*> \samples\datatypes  
  
## <a name="requirements"></a>Requisiti  
 Per eseguire questa applicazione di esempio, è necessario impostare il classpath per includere il file sqljdbc4.jar. Se nel classpath manca una voce per il file sqljdbc4.jar, nell'applicazione di esempio verrà generata un'eccezione di classe non trovata. Per ulteriori informazioni su come impostare il classpath, vedere [utilizza il Driver JDBC](../../../connect/jdbc/using-the-jdbc-driver.md).  
  
 Inoltre, occorre accedere il [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] database di esempio per eseguire questa applicazione di esempio.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente, il codice di esempio stabilisce una connessione per il [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] del database e quindi richiama il metodo createSampleTables.  
  
 Il metodo createSampleTables elimina le eventuali tabelle di test TestTable1 e TestTable2 esistenti, quindi inserisce due righe in TestTable1.  
  
 L'esempio di codice include inoltre i tre metodi seguenti e una classe aggiuntiva denominata ExampleContentHandler.  
  
 La classe ExampleContentHandler implementa un gestore di contenuto personalizzato che definisce i metodi per gli eventi del parser.  
  
 Il metodo showGetters indica come analizzare i dati dell'oggetto SQLXML utilizzando SAX, ContentHandler e XMLReader. Nell'esempio di codice viene innanzitutto creata un'istanza del gestore di contenuto personalizzato ExampleContentHandler. Viene quindi creata ed eseguita un'istruzione SQL che restituisce un set di dati da TestTable1. Viene infine ottenuto un parser SAX e vengono analizzati i dati XML.  
  
 Il metodo showsetters indica di seguito viene illustrato come impostare il **xml** colonna utilizzando SAX, ContentHandler e ResultSet. Viene innanzitutto creato un oggetto SQLXML vuoto utilizzando il [createSQLXML](../../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md) metodo della classe di connessione. Viene quindi ottenuta un'istanza di un gestore di contenuto per scrivere i dati nell'oggetto SQLXML e i dati vengono successivamente scritti in TestTable1. Infine, scorrere le righe di dati contenuti nel set di risultati, il codice di esempio e Usa il [getSQLXML](../../../connect/jdbc/reference/getsqlxml-method-sqlserverresultset.md) metodo per leggere i dati XML.  
  
 Il metodo showTransformer indica come ottenere i dati XML da una tabella e inserirli in un'altra tabella utilizzando SAX e Transformer. Viene innanzitutto recuperato l'oggetto SQLXML di origine da TestTable1. Quindi, viene creato un oggetto SQLXML di destinazione vuoto utilizzando il [createSQLXML](../../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md) metodo della classe di connessione. Viene quindi aggiornato l'oggetto SQLXML di destinazione e i dati XML vengono scritti in TestTable2. Infine, scorrere le righe di dati contenuti nel set di risultati, il codice di esempio e Usa il [getSQLXML](../../../connect/jdbc/reference/getsqlxml-method-sqlserverresultset.md) metodo per leggere i dati XML in TestTable2.  
  
 [!code[JDBC#UsingSQLXML1](../../../connect/jdbc/codesnippet/Java/sqlxml-data-type-sample_1.java)]  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo dei tipi di dati di &#40;JDBC&#41;](../../../connect/jdbc/working-with-data-types-jdbc.md)  
  
  
