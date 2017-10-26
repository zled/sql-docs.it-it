---
title: sqlsrv_connect | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- sqlsrv_connect
apitype: NA
helpviewer_keywords:
- connecting to the server
- API Reference, sqlsrv_connect
- connection pooling support
- sqlsrv_connect
ms.assetid: 37836b49-258e-45ce-9549-b8bd85d6952d
caps.latest.revision: 67
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8e9491e2b0721f7c7a2ca6b5ed37c52135a4c760
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsrvconnect"></a>sqlsrv_connect
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Crea una risorsa di connessione e apre una connessione. Per impostazione predefinita, viene eseguito un tentativo di connessione usando l'autenticazione di Windows.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sqlsrv_connect( string $serverName [, array $connectionInfo])  
```  
  
#### <a name="parameters"></a>Parametri  
*$serverName*: stringa che specifica il nome del server con cui viene stabilita la connessione. Nella stringa può essere incluso un nome di istanza (ad esempio, "myServer\instanceName") o un numero di porta (ad esempio, "myServer, 1521"). Per una descrizione completa delle opzioni disponibili per questo parametro, vedere la parola chiave Server nella sezione Parole chiave delle stringhe di connessione per il driver ODBC di [Utilizzo delle parole chiave delle stringhe di connessione con SQL Server Native Client](http://go.microsoft.com/fwlink/?LinkId=105504).  
  
A partire dalla versione 3.0 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]è inoltre possibile specificare un'istanza di LocalDB con `"(localdb)\instancename"`. Per altre informazioni, vedere [PHP Driver for SQL Server Support for LocalDB](../../connect/php/php-driver-for-sql-server-support-for-localdb.md).  
  
In più, a partire dalla versione 3.0 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], è possibile specificare un nome di rete virtuale per connettersi a un gruppo di disponibilità AlwaysOn. Per altre informazioni sul supporto dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] per [!INCLUDE[ssHADR](../../includes/sshadr_md.md)], vedere [PHP Driver for SQL Server Support for High Availability, Disaster Recovery (Driver PHP per il supporto di SQL Server per il ripristino di emergenza a disponibilità elevata)](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).  
  
*$connectionInfo* [facoltativo]: associativa **matrice** che contiene gli attributi di connessione (ad esempio, **matrice**("Database" = > "AdventureWorks")). Vedere [Connection Options](../../connect/php/connection-options.md) per un elenco delle chiavi supportate per la matrice.  
  
## <a name="return-value"></a>Valore restituito  
Una risorsa di connessione PHP. Se non è possibile creare e aprire correttamente una connessione, verrà restituito **false** .  
  
## <a name="remarks"></a>Osservazioni  
Se i valori per le chiavi *UID* e *PWD* non sono specificati nel parametro *$connectionInfo* facoltativo, verrà eseguito un tentativo di connessione viene usando l'autenticazione di Windows. Per altre informazioni sulla connessione al server, vedere [How to: Connect Using Windows Authentication](../../connect/php/how-to-connect-using-windows-authentication.md) e [How to: Connect Using SQL Server Authentication](../../connect/php/how-to-connect-using-sql-server-authentication.md).  
  
## <a name="example"></a>Esempio  
L'esempio seguente permette di creare e aprire una connessione usando l'autenticazione di Windows. Nell'esempio si presuppone che SQL Server e il database [AdventureWorks](http://www.codeplex.com/SqlServerSamples) siano installati nel computer locale. Quando si esegue l'esempio dalla riga di comando, tutto l'output viene scritto nella console.  
  
```  
<?php  
/*  
Connect to the local server using Windows Authentication and specify  
the AdventureWorks database as the database in use. To connect using  
SQL Server Authentication, set values for the "UID" and "PWD"  
 attributes in the $connectionInfo parameter. For example:  
$connectionInfo = array("UID" => $uid, "PWD" => $pwd, "Database"=>"AdventureWorks");  
*/  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
  
if( $conn )  
{  
     echo "Connection established.\n";  
}  
else  
{  
     echo "Connection could not be established.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
//-----------------------------------------------  
// Perform operations with connection.  
//-----------------------------------------------  
  
/* Close the connection. */  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Riferimento all'API del driver SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
[Connecting to the Server](../../connect/php/connecting-to-the-server.md)  
[Informazioni sugli esempi di codice nella documentazione](../../connect/php/about-code-examples-in-the-documentation.md)  
  

