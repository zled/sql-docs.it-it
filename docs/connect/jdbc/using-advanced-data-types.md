---
title: Utilizzo di tipi di dati avanzati | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b39461d3-48d6-4048-8300-1a886c00756d
caps.latest.revision: 58
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b74ed587d91e351f91db2e3ef2a45c41edf37918
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="using-advanced-data-types"></a>Utilizzo di tipi di dati avanzati
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] JDBC avanzati di tipi di dati vengono utilizzati per convertire il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipi di dati in un formato che può essere riconosciuto di Java linguaggio di programmazione.  
  
## <a name="remarks"></a>Osservazioni  
 Nella tabella seguente sono elencati i mapping predefiniti tra avanzate [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], tipi di dati del linguaggio di programmazione Java e JDBC.  
  
|Tipi di SQL Server|Tipi JDBC (java.sql.Types)|Tipi del linguaggio Java|  
|----------------------|-----------------------------------|-------------------------|  
|varbinary(max)<br /><br /> image|LONGVARBINARY|Matrice di byte \(predefinito), Blob, InputStream, stringa|  
|text<br /><br /> varchar(max)|LONGVARCHAR|String (default), Clob, InputStream|  
|ntext<br /><br /> nvarchar(max)|LONGVARCHAR<br /><br /> LONGNVARCHAR (Java SE 6.0)|String (default), Clob, NClob (Java SE 6.0)|  
|xml|LONGVARCHAR<br /><br /> SQLXML (Java SE 6.0)|String (default), InputStream, Clob, byte[],Blob, SQLXML (Java SE 6.0)|  
|Tipo definito dall'utente<sup>1</sup>|VARBINARY|String (default), byte[], InputStream|  
  
 <sup>1</sup> il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] supporta l'invio e recupero di tipi definiti dall'utente CLR come dati binari, ma non supporta la manipolazione dei metadati CLR.  
  
 Nelle sezioni seguenti vengono forniti esempi di come sia possibile utilizzare il driver JDBC e i tipi di dati avanzati.  
  
## <a name="blob-and-clob-and-nclob-data-types"></a>Tipi di dati BLOB, CLOB e NCLOB  
 Nel driver JDBC sono implementati tutti i metodi delle interfacce java.sql.Blob, java.sql.Clob e java.sql.NClob.  
  
> [!NOTE]  
>  Valori CLOB possono essere utilizzati con [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)] (o versione successiva) i tipi di dati di valori di grandi dimensioni. In particolare, i tipi CLOB possono essere utilizzati con il **varchar (max)** e **nvarchar (max)** tipi di dati, i tipi BLOB possono essere utilizzati con **varbinary (max)** e **immagine ** tipi di dati, mentre i tipi NCLOB possono essere utilizzato con **ntext** e **nvarchar (max)**.  
  
## <a name="large-value-data-types"></a>Tipi di dati per valori di grandi dimensioni  
 Nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], l'utilizzo con tipi dati di valori di grandi dimensioni richiede una gestione speciale. I tipi di dati per valori di grandi dimensioni sono quelli che superano le dimensioni di riga massime di 8 KB. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]introduce un identificatore max per **varchar**, **nvarchar**, e **varbinary** tipi di dati per consentire l'archiviazione dei valori di dimensioni pari a 2 ^ 31 byte. Colonne della tabella e [!INCLUDE[tsql](../../includes/tsql_md.md)] possono specificare variabili **varchar (max)**, **nvarchar (max)**, o **varbinary (max)** tipi di dati.  
  
 Gli scenari principali di utilizzo di tipi per valori di grandi dimensioni riguardano il recupero di tali tipi di dati da un database o l'aggiunta degli stessi a un database. Nelle sezioni seguenti vengono descritti i diversi approcci adottabili per eseguire queste attività.  
  
### <a name="retrieving-large-value-types-from-a-database"></a>Recupero di tipi per valori di grandi dimensioni da un database  
 Quando si recupera un tipo di dati per valori di grandi dimensioni non binario, ad esempio il **varchar (max)** tipo di dati, ovvero da un database, un approccio consiste nel leggere i dati come flusso di caratteri. Nell'esempio seguente, il [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) metodo il [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) classe viene utilizzata per recuperare dati dal database e restituire come set di risultati. Il [getCharacterStream](../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md) metodo il [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) classe viene utilizzata per leggere i dati di valori di grandi dimensioni dal set di risultati.  
  
```  
ResultSet rs = stmt.executeQuery("SELECT TOP 1 * FROM Test1");  
rs.next();  
Reader reader = rs.getCharacterStream(2);  
```  
  
> [!NOTE]  
>  Questo stesso approccio può essere utilizzato anche per il **testo**, **ntext**, e **nvarchar (max)** tipi di dati.  
  
 Quando si recupera un tipo di dati binari di valori di grandi dimensioni, ad esempio il **varbinary (max)** tipo di dati, ovvero da un database, sono disponibili diversi approcci che è possibile eseguire. L'approccio più efficace consiste nel leggere i dati come flusso binario, come nell'esempio seguente:  
  
```  
ResultSet rs = stmt.executeQuery("SELECT photo FROM mypics");  
rs.next();  
InputStream is = rs.getBinaryStream(2);  
```  
  
 È inoltre possibile utilizzare il [getBytes](../../connect/jdbc/reference/getbytes-method-sqlserverresultset.md) metodo per leggere i dati come matrice di byte, come illustrato di seguito:  
  
```  
ResultSet rs = stmt.executeQuery("SELECT photo FROM mypics");  
rs.next();  
byte [] b = rs.getBytes(2);  
```  
  
> [!NOTE]  
>  È inoltre possibile leggere i dati come BLOB. Tuttavia, questo metodo è meno efficace dei due precedenti.  
  
### <a name="adding-large-value-types-to-a-database"></a>Aggiunta di tipi per valori di grandi dimensioni a un database  
 Il caricamento di dati di grandi dimensioni con il driver JDBC funziona bene per i dati di dimensioni pari a quelle della memoria, e nel caso di dati di dimensioni maggiori di quelle della memoria, l'opzione principale è rappresentata dall'utilizzo di flussi. Tuttavia, il modo più efficace per caricare dati di grandi dimensioni è mediante interfacce di flusso.  
  
 È però possibile utilizzare anche stringhe o byte, come nell'esempio seguente:  
  
```  
PreparedStatement pstmt = con.prepareStatement("INSERT INTO test1 (c1_id, c2_vcmax) VALUES (?, ?)");  
pstmt.setInt(1, 1);  
pstmt.setString(2, htmlStr);  
pstmt.executeUpdate();  
```  
  
> [!NOTE]  
>  Questo approccio può essere utilizzato anche per i valori archiviati in **testo**, **ntext**, e **nvarchar (max)** colonne.  
  
 Se si dispone di una libreria di immagini nel server e necessario caricare il file di immagine binari intera per un **varbinary (max)** colonna, il metodo più efficiente con il driver JDBC consiste nell'utilizzare direttamente flussi, come illustrato di seguito:  
  
```  
PreparedStatement pstmt = con.prepareStatement("INSERT INTO test1 (Col1, Col2) VALUES(?,?)");  
File inputFile = new File("CLOBFile20mb.jpg");  
FileInputStream inStream = new FileInputStream(inputFile);  
int id = 1;  
pstmt.setInt(1,id);  
pstmt.setBinaryStream(2, inStream);  
pstmt.executeUpdate();  
inStream.close();  
```  
  
> [!NOTE]  
>  L'utilizzo del metodo Clob o Blob non rappresenta un modo efficace di caricamento di dati di grandi dimensioni.  
  
### <a name="modifying-large-value-types-in-a-database"></a>Modifica di tipi per valori di grandi dimensioni in un database  
 Nella maggior parte dei casi, il metodo consigliato per aggiornare o modificare i valori di grandi dimensioni nel database consiste nel passare parametri mediante la [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) e [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) classi utilizzando [!INCLUDE[tsql](../../includes/tsql_md.md)] comandi quali UPDATE, WRITE e SUBSTRING.  
  
 Se è necessario sostituire l'istanza di una parola in un file di testo di grandi dimensioni, ad esempio un file HTML archiviato, è possibile utilizzare un oggetto Clob, come illustrato di seguito:  
  
```  
String SQL = "SELECT * FROM test1;";  
Statement stmt = con.createStatement(ResultSet.TYPE_SCROLL_SENSITIVE, ResultSet.CONCUR_UPDATABLE);  
ResultSet rs = stmt.executeQuery(SQL);  
rs.next();  
  
Clob clob = rs.getClob(2);  
long pos = clob.position("dog", 1);  
clob.setString(pos, "cat");  
rs.updateClob(2, clob);  
rs.updateRow();  
```  
  
 Inoltre, è possibile eseguire tutte le operazioni sul server e quindi passare solo i parametri a un'istruzione UPDATE preparata.  
  
 Per ulteriori informazioni sui tipi per valori di grandi dimensioni, vedere la sezione relativa all'utilizzo di tipi per valori di grandi dimensioni nella Documentazione online di SQL Server.  
  
## <a name="xml-data-type"></a>Tipo di dati XML  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]fornisce un **xml** tipo di dati che consente di archiviare documenti XML e frammenti un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database. Il **xml** tipo di dati è un tipo di dati incorporati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ed è simile ad altri tipi predefiniti, quali **int** e **varchar**. Come con altri tipi predefiniti, è possibile usare il **xml** tipo di dati come tipo di colonna quando si crea una tabella, come un tipo di variabile, un tipo di parametro o un tipo restituito di funzione o in [!INCLUDE[tsql](../../includes/tsql_md.md)] funzioni CAST e CONVERT.  
  
 Nel driver JDBC, il **xml** tipo di dati può essere eseguito come una stringa, matrice di byte, flusso, l'oggetto CLOB, BLOB oppure SQLXML. Il mapping predefinito è come stringa. A partire da Microsoft JDBC Driver versione 2.0, il driver JDBC offre il supporto per l'API di JDBC 4.0, in cui viene presentata l'interfaccia SQLXML. Tale interfaccia definisce i metodi per interagire e modificare i dati XML. Il **SQLXML** esegue il mapping al tipo di dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **xml** tipo di dati. Per ulteriori informazioni su come leggere e scrivere dati XML da e in un database relazionale con il **SQLXML** del tipo di dati Java, vedere [supporto dati XML](../../connect/jdbc/supporting-xml-data.md).  
  
 L'implementazione del **xml** il tipo di dati nel driver JDBC fornisce supporto per le operazioni seguenti:  
  
-   Accesso al codice XML come stringa UTF-16 Java standard per la maggior parte degli scenari di programmazione comuni  
  
-   Input di codice XML in formato UTF-8 e con altri tipi di codifica a 8 bit  
  
-   Accesso al codice XML come matrice di byte, con un indicatore dell'ordine di byte (BOM) iniziale in caso di codifica in formato UTF-16 per l'interscambio con altri processori e file su disco XML  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]richiede un indicatore ordine byte iniziale per il codice XML con codifica UTF-16. Questo elemento deve essere fornito dall'applicazione quando i valori dei parametri XML vengono forniti come matrici di byte. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Restituisce sempre i valori XML come UTF-16 stringhe Nessun indicatore ordine byte né dichiarazione di codifica incorporata. Quando vengono recuperati valori XML come byte[], BinaryStream o Blob, un BOM UTF-16 viene anteposto al valore.  
  
 Per ulteriori informazioni sul **xml** del tipo di dati, vedere "tipo di dati xml" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione in linea.  
  
## <a name="user-defined-data-type"></a>Tipo di dati definito dall'utente  
 L'introduzione di tipi definiti dall'utente (UDT) in [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)] estende il sistema di tipi SQL consentendo di archiviare oggetti e strutture di dati personalizzati in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database. I tipi definiti dall'utente possono contenere più tipi di dati e possono assumere comportamenti, differenziandoli dai tipi di dati alias tradizionali costituiti da un singolo tipo di dati di sistema [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. I tipi di dati UDT vengono definiti utilizzando uno qualsiasi dei linguaggi supportati dalla funzionalità CLR (Common Language Runtime) di Microsoft .NET in grado di produrre codice verificabile, tra cui Microsoft Visual C# e Visual Basic .NET. I dati vengono esposti come campi e proprietà di una classe o una struttura basata su .NET Framework e i comportamenti vengono definiti dai metodi della classe o della struttura in questione.  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], un tipo definito dall'utente può essere utilizzato come definizione di colonna di una tabella, come una variabile in un [!INCLUDE[tsql](../../includes/tsql_md.md)] batch, o come un argomento di un [!INCLUDE[tsql](../../includes/tsql_md.md)] stored procedure o funzione.  
  
 Per ulteriori informazioni sui tipi di dati definito dall'utente, vedere "Utilizzo e modifica delle istanze dei tipi definiti dall'utente" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione in linea.  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sui tipi di dati del Driver JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  

