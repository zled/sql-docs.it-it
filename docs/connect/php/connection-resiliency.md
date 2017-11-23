---
title: Resilienza delle connessioni inattive
ms.date: 07/13/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.suite: sql
ms.custom: 
ms.technology: drivers
ms.topic: article
author: david-puglielli
ms.author: v-dapugl
manager: v-hakaka
ms.workload: Inactive
ms.openlocfilehash: 6c36086404c8767ea30c85b2ebd77340d11732ab
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="idle-connection-resiliency"></a>Resilienza delle connessioni inattive
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[Resilienza di connessione](https://msdn.microsoft.com/library/dn632678.aspx) è il principio che può essere ristabilita una connessione inattiva interrotta, entro determinati vincoli. Se una connessione a Microsoft SQL Server non riesce, resilienza di connessione consente al client tentano automaticamente di ristabilire la connessione. Resilienza di connessione è una proprietà dell'origine dati. solo i Database SQL di Azure e SQL Server 2014 e versioni successive supporta la resilienza di connessione.

Resilienza di connessione viene implementata con due parole chiave di connessione che possono essere aggiunto a stringhe di connessione: **ConnectRetryCount** e **ConnectRetryInterval**.

|Parola chiave|Valori|Valore predefinito|Description|
|-|-|-|-|
|**ConnectRetryCount**| Numero intero compreso tra 0 e 255 (inclusivo)|1|Il numero massimo di tentativi per ristabilire una connessione interrotta prima di rinunciare. Per impostazione predefinita, un singolo tenta di ristabilire una connessione quando vengono interrotti. Un valore pari a 0 indica che la riconnessione non verrà tentato di eseguire.|
|**ConnectRetryInterval**| Numero intero compreso tra 1 e 60 (inclusi)|1| Tempo, in secondi, tra i tentativi per ristabilire una connessione. L'applicazione tenterà di riconnettersi immediatamente al rilevamento di una connessione interrotta e verrà quindi attendere **ConnectRetryInterval** secondi prima di riprovare. Questa parola chiave viene ignorata se **ConnectRetryCount** è uguale a 0.

Se il prodotto di **ConnectRetryCount** moltiplicato per **ConnectRetryInterval** è maggiore di **LoginTimeout**, quindi il client viene interrotta sta tentando di connettersi una volta  **LoginTimeout** viene raggiunto; in caso contrario, continuerà a tentare di riconnettersi finché **ConnectRetryCount** viene raggiunto.

#### <a name="remarks"></a>Osservazioni

Resilienza di connessione si applica quando la connessione rimane inattiva. Gli errori che si verificano durante l'esecuzione di una transazione, ad esempio, non attiva i tentativi di riconnessione: hanno esito negativo come in caso contrario potrebbe essere previsto. Le situazioni seguenti, note come gli stati di sessione non recuperabili, non comporta tentativi di riconnessione:

* Tabelle temporanee
* Cursori locali e globali
* Contesto di transazione e sessione il livello di blocchi di transazione
* Blocchi dell'applicazione
* EXECUTE AS / ripristinare il contesto di sicurezza
* Handle di automazione OLE
* Handle XML preparati
* Flag di traccia

## <a name="example"></a>Esempio

Il codice seguente si connette a un database ed esegue una query. La connessione viene interrotta per la terminazione della sessione e viene tentata una nuova query utilizzando la connessione interrotta. Questo esempio viene utilizzato il [AdventureWorks](https://msdn.microsoft.com/library/ms124501%28v=sql.100%29.aspx) database di esempio.

In questo esempio, si specifica un cursore memorizzato nel buffer prima di interrompere la connessione. Se non si specifica un cursore memorizzato nel buffer, la connessione verrà ristabilita non perché non vi sarà un cursore sul lato server attivo ed è quindi la connessione non inattiva se interrotto. Tuttavia, in tal caso è possibile chiamare sqlsrv_free_stmt() prima di interrompere la connessione per liberare il cursore e potrebbe essere ristabilita la connessione.

```php
<?php
// This function breaks the connection by determining its session ID and killing it.
// A separate connection is used to break the main connection because a session
// cannot kill itself. The sleep() function ensures enough time has passed for KILL
// to finish ending the session.
function BreakConnection( $conn, $conn_break )
{
    $stmt1 = sqlsrv_query( $conn, "SELECT @@SPID" );
    if ( sqlsrv_fetch( $stmt1 ) )
    {
        $spid=sqlsrv_get_field( $stmt1, 0 );
    }

    $stmt2 = sqlsrv_prepare( $conn_break, "KILL ".$spid );
    sqlsrv_execute( $stmt2 );
    sleep(1);
}

// Connect to the local server using Windows authentication and specify
// AdventureWorks as the database in use. Specify values for
// ConnectRetryCount and ConnectRetryInterval as well.
$databaseName = 'AdventureWorks2014';
$serverName = '(local)';
$connectionInfo = array( "Database"=>$databaseName, "ConnectRetryCount"=>10, "ConnectRetryInterval"=>10 );

$conn = sqlsrv_connect( $serverName, $connectionInfo );
if( $conn === false)  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}

// A separate connection that will be used to break the main connection $conn
$conn_break = sqlsrv_connect( $serverName, array( "Database"=>$databaseName) );

// Create a statement to retrieve the contents of a table
$stmt1 = sqlsrv_query( $conn, "SELECT * FROM HumanResources.Employee",
                       array(), array( "Scrollable"=>"buffered" ) );
if( $stmt1 === false )
{
     echo "Error in statement 1.\n";
     die( print_r( sqlsrv_errors(), true ));
}
else
{
    echo "Statement 1 successful.\n";
    $rowcount = sqlsrv_num_rows( $stmt1 );
    echo $rowcount." rows in result set.\n";
}

// Now break the connection $conn
BreakConnection( $conn, $conn_break );

// Create another statement. The connection will be reestablished.
$stmt2 = sqlsrv_query( $conn, "SELECT * FROM HumanResources.Department",
                       array(), array( "Scrollable"=>"buffered" ) );
if( $stmt2 === false )
{
     echo "Error in statement 2.\n";
     die( print_r( sqlsrv_errors(), true ));
}
else
{
    echo "Statement 2 successful.\n";
    $rowcount = sqlsrv_num_rows( $stmt2 );
    echo $rowcount." rows in result set.\n";
}

sqlsrv_close( $conn );
sqlsrv_close( $conn_break );
?>
```
Output previsto:
```
Statement 1 successful.
290 rows in result set.
Statement 2 successful.
16 rows in result set.
```

## <a name="see-also"></a>Vedere anche
[Resilienza di connessione nel driver ODBC di Windows](https://docs.microsoft.com/en-us/sql/connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver)
