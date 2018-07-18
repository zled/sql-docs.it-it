---
title: Programmazione con SQLXML | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4d2cc57c-7293-4d92-b8b1-525e2b35f591
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e5cb6d2d44b9988dda28d5e9bd10db0d96467ff6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="programming-with-sqlxml"></a>Programmazione con SQLXML
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  In questa sezione viene descritto come utilizzare il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] metodi API per archiviare e recuperare un file XML del documento in e da un database relazionale con **SQLXML** oggetti.  
  
 Sono inoltre contenute informazioni sui tipi di oggetti SQLXML e vengono elencate importanti linee guida e limitazioni da prendere in considerazione quando si utilizzano oggetti SQLXML.  
  
## <a name="reading-and-writing-xml-data-with-sqlxml-objects"></a>Lettura e scrittura di dati XML con oggetti SQLXML  
 Nell'elenco seguente viene descritto come utilizzare il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] metodi API per leggere e scrivere dati XML con oggetti SQLXML:  
  
-   Per creare un oggetto SQLXML, utilizzare il [createSQLXML](../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md) metodo il [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) classe. Si noti che questo metodo consente di creare un oggetto SQLXML senza dati. Per aggiungere **xml** dati all'oggetto SQLXML, chiamare uno dei metodi seguenti specificati nell'interfaccia SQLXML: setResult, setCharacterStream, setBinaryStream, o setString.  
  
-   Per recuperare l'oggetto SQLXML stesso, utilizzare i metodi getSQLXML del [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) classe o [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) classe.  
  
-   Per recuperare il **xml** dati da un oggetto SQLXML, utilizzare uno dei metodi seguenti specificati nell'interfaccia SQLXML: getSource getCharacterStream, getBinaryStream, o getString.  
  
-   Per aggiornare il **xml** dati in un oggetto SQLXML, utilizzare il [updateSQLXML](../../connect/jdbc/reference/updatesqlxml-method-sqlserverresultset.md) metodo il [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) classe.  
  
-   Per archiviare un oggetto SQLXML in una colonna della tabella di database di tipo **xml**, utilizzare i metodi setSQLXML del [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) classe o [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)classe.  
  
 Nell'esempio di codice in [esempio tipo di dati SQLXML](../../connect/jdbc/sqlxml-data-type-sample.md) viene illustrato come eseguire queste attività comuni dell'API.  
  
## <a name="readable-and-writable-sqlxml-objects"></a>Oggetti SQLXML accessibili in lettura e scrittura  
 Nella seguente tabella sono elencati i tipi di oggetti SQLXML supportati dai metodi di impostazione, richiamo e aggiornamento forniti dall'API di JDBC. Le colonne della tabella fanno riferimento ai seguenti elementi:  
  
-   Il **nome del metodo** colonna sono elencati i metodi di richiamo, impostazione e aggiornamento supportati nell'API di JDBC.  
  
-   Il **oggetto SQLXML metodo di richiamo** colonna rappresenta un oggetto SQLXML, che viene creato tramite il [getSQLXML](../../connect/jdbc/reference/getsqlxml-method-sqlservercallablestatement.md) metodo il [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) classe o [getSQLXML](../../connect/jdbc/reference/getsqlxml-method-sqlserverresultset.md) metodo il [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) classe.  
  
-   Il **oggetto SQLXML metodo di impostazione** colonna rappresenta un oggetto SQLXML, che viene creato tramite il [createSQLXML](../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md) metodo il [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) classe. Si noti che i metodi di impostazione seguenti accettano solo un oggetto SQLXML creato tramite il [createSQLXML](../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md) metodo.  
  
|Nome metodo|Oggetto SQLXML metodo di richiamo<br /><br /> (accessibile in lettura)|Oggetto SQLXML metodo di impostazione<br /><br /> (accessibile in scrittura)|  
|-----------------|-------------------------------------------|-------------------------------------------|  
|CallableStatement.setSQLXML()|Non supportato|Supported|  
|CallableStatement.setObject()|Non supportato|Supported|  
|PreparedStatement.setSQLXML()|Non supportato|Supported|  
|SetObject|Non supportato|Supported|  
|ResultSet.updateSQLXML()|Non supportato|Supported|  
|ResultSet.updateObject()|Non supportato|Supported|  
|ResultSet.getSQLXML()|Supported|Non supportato|  
|CallableStatement.getSQLXML()|Supported|Non supportato|  
  
 Come illustrato nella tabella precedente, i metodi SQLXML di impostazione non funzionano con gli oggetti SQLXML accessibili in lettura. Analogamente i metodi di richiamo non funzioneranno con gli oggetti SQLXML accessibili in scrittura.  
  
 Se l'applicazione richiama il metodo setObject specificando un parametro di lunghezza o di una scala con un oggetto SQLXML, il parametro di scala o lunghezza viene ignorato.  
  
## <a name="guidelines-and-limitations-when-using-sqlxml-objects"></a>Linee guida e limitazioni relative all'utilizzo di oggetti SQLXML  
 Le applicazioni possono utilizzare gli oggetti SQLXML per leggere e scrivere i dati da e nel database. Nel seguente elenco vengono fornite informazioni su limitazioni e linee guida specifiche da adottare quando si utilizzano oggetti SQLXML:  
  
-   Un oggetto SQLXML può essere valido solo per la durata della transazione in cui è stato creato.  
  
-   Un oggetto SQLXML ricevuto da un metodo di richiamo può essere utilizzato solo per leggere dati.  
  
-   Un oggetto SQLXML creato dall'oggetto connessione può essere utilizzato solo per scrivere dati.  
  
-   Per leggere i dati, l'applicazione può richiamare un solo metodo di richiamo su un oggetto SQLXML accessibile in lettura. Dopo aver richiamato il metodo di richiamo, tutti gli altri metodi di richiamo o impostazione sullo stesso oggetto SQLXML non verranno eseguiti.  
  
-   L'applicazione può richiamare solo il metodo disponibile per l'oggetto SQLXML dopo l'operazione di lettura o scrittura. È tuttavia possibile elaborare l'origine o il flusso restituito purché la colonna o il parametro sottostante sia attivo. Se la colonna o il parametro sottostante diventa inattivo, l'origine o il flusso associato all'oggetto SQLXML verrà chiuso. Se la colonna o il parametro sottostante non è più valido, i dati sottostanti non saranno più disponibili per i metodi di richiamo Stream, Simple API for XML (SAX) e Streaming API for XML (StAX).  
  
-   L'applicazione può richiamare un solo metodo di impostazione su un oggetto SQLXML accessibile in scrittura. Dopo aver richiamato il metodo di impostazione, tutti gli altri metodi di impostazione o richiamo sullo stesso oggetto SQLXML non verranno eseguiti.  
  
-   Per impostare i dati sull'oggetto SQLXML, l'applicazione deve utilizzare il metodo di impostazione appropriato e le funzioni dell'oggetto restituito.  
  
-   I metodi getSQLXML del [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) classe e [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) classe restituisce **null** dati se la colonna sottostante è **null**.  
  
-   Gli oggetti del metodo di impostazione sono validi per la durata della connessione in cui sono stati creati.  
  
-   Le applicazioni non sono consentite per impostare un **null** valore utilizzando i metodi setter forniti dall'interfaccia SQLXML. Le applicazioni possono impostare una stringa vuota ("") utilizzando i metodi di impostazione forniti nell'interfaccia SQLXML. Per impostare un **null** valore, le applicazioni devono chiamare uno dei seguenti:  
  
    -   I metodi setNull del [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) classe e [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) classe.  
  
    -   I metodi setObject del [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) classe e [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) classe.  
  
    -   I metodi setSQLXML del [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) classe e [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) classe con un **null** valore del parametro.  
  
-   Per prestazioni ottimali durante la modifica di documenti XML è consigliabile utilizzare i parser Simple API for XML (SAX) e Streaming API for XML (StAX) anziché i parser Document Object Model (DOM).  
  
 I parser XML non gestiscono i valori vuoti. SQL Server consente tuttavia alle applicazioni di recuperare e archiviare valori vuoti da e nelle colonne del database del tipo di dati XML. Se pertanto durante l'analisi dei dati XML il valore sottostante è vuoto, il parser genererà un'eccezione. Per gli output DOM il driver JDBC rileverà l'eccezione e genererà un errore. Per gli output SAX e StAX l'errore deriverà direttamente dal parser.  
  
## <a name="adaptive-buffering-and-sqlxml-support"></a>Supporto del buffer adattivo con SQLXML  
 I flussi di caratteri e binari restituiti dall'oggetto SQLXML rispettano le modalità di buffer adattivo o completo. Se invece i parser XML non sono flussi, non rispetteranno le impostazioni del buffer adattivo o completo. Per ulteriori informazioni sul buffer adattivo, vedere [utilizzando il buffer adattivo](../../connect/jdbc/using-adaptive-buffering.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto di dati XML](../../connect/jdbc/supporting-xml-data.md)  
  
  
