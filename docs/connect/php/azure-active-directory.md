---
title: Azure Active Directory | Documenti Microsoft
ms.date: 07/13/2017
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.suite: sql
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
author: david-puglielli
ms.author: v-dapugl
manager: v-hakaka
ms.openlocfilehash: bfb4c78f7a32c1205256f7a0d44bd9526fabdc27
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="connect-using-azure-active-directory-authentication"></a>Connessione tramite l'autenticazione di Azure Active Directory
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-whatis) (Azure AD) è una tecnologia di gestione di ID utente centrale che funziona come un'alternativa al [autenticazione di SQL Server](../../connect/php/how-to-connect-using-sql-server-authentication.md). Azure AD consente le connessioni al Database SQL di Microsoft Azure e SQL Data Warehouse con identità federative in Azure AD utilizzando un nome utente e password, autenticazione integrata di Windows o un token di accesso di Azure AD. i driver PHP per SQL Server offrono il supporto parziale per queste funzionalità.

Per usare Azure AD, usare il **autenticazione** (parola chiave). I valori che **autenticazione** può accettare nella sono illustrati nella tabella seguente.

|Parola chiave|Valori|Description|
|-|-|-|
|**Autenticazione**|Non è impostato (impostazione predefinita)|Modalità di autenticazione base a parole chiave. Per altre informazioni, vedere [Connection Options](../../connect/php/connection-options.md). |
||`SqlPassword`|L'autenticazione direttamente a un'istanza di SQL Server (che può essere un'istanza di Azure) usando un nome utente e password. Il nome utente e la password deve essere passati nella stringa di connessione usando il **UID** e **PWD** parole chiave. |
||`ActiveDirectoryPassword`|Eseguire l'autenticazione con un'identità di Azure Active Directory utilizzando un nome utente e password. Il nome utente e la password deve essere passati nella stringa di connessione usando il **UID** e **PWD** parole chiave. |

Il **autenticazione** (parola chiave) interessa le impostazioni di sicurezza della connessione. Se è impostato nella stringa di connessione, quindi per impostazione predefinita il **Encrypt** parola chiave è impostata su true, pertanto il client richiederà la crittografia. Inoltre, verrà convalidato il certificato del server indipendentemente dall'impostazione di crittografia a meno che non **TrustServerCertificate** è impostata su true. Questa operazione si differenzia dal precedente e meno sicura, metodo di accesso, in cui il certificato del server non viene convalidato, a meno che la crittografia specificamente richiesto nella stringa di connessione.

Prima di usare Azure AD con i driver PHP per SQL Server in Windows, assicurarsi di aver installato il [Microsoft Online Services Sign-In Assistant](https://www.microsoft.com/download/details.aspx?id=41950) (non per Linux e Mac OS).

#### <a name="limitations"></a>Limitazioni

In Windows, il driver ODBC sottostante supporta un maggior valore per il **autenticazione** (parola chiave), **ActiveDirectoryIntegrated**, ma i driver PHP non supportano questo valore su qualsiasi piattaforma e pertanto anche non supportano l'autenticazione basata su token di Azure AD.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato come connettere utilizzando **SqlPassword** e **ActiveDirectoryPassword**.

```php
    <?php
    // First connect to a local SQL Server instance by setting Authentication to SqlPassword
    $serverName = "myserver.mydomain";

    $connectionInfo = array( "UID"=>$myusername, "PWD"=>$mypassword, "Authentication"=>'SqlPassword' );

    $conn = sqlsrv_connect( $serverName, $connectionInfo );
    if( $conn === false )
    {
        echo "Could not connect with Authentication=SqlPassword.\n";
        print_r( sqlsrv_errors() );
    }
    else
    {
        echo "Connected successfully with Authentication=SqlPassword.\n";
        sqlsrv_close( $conn );
    }

    // Now connect to an Azure SQL database by setting Authentication to ActiveDirectoryPassword
    $azureServer = "myazureserver.database.windows.net";
    $azureDatabase = "myazuredatabase";
    $azureUsername = "myuid";
    $azurePassword = "mypassword";
    $connectionInfo = array( "Database"=>$azureDatabase, "UID"=>$azureUsername, "PWD"=>$azurePassword,
                             "Authentication"=>'ActiveDirectoryPassword' );

    $conn = sqlsrv_connect( $azureServer, $connectionInfo );
    if( $conn === false )
    {
        echo "Could not connect with Authentication=ActiveDirectoryPassword.\n";
        print_r( sqlsrv_errors() );
    }
    else
    {
        echo "Connected successfully with Authentication=ActiveDirectoryPassword.\n";
        sqlsrv_close( $conn );
    }

    ?>
```

Nell'esempio seguente viene eseguita la stessa operazione sopra con il driver PDO_SQLSRV.

```php
    <?php
    // First connect to a local SQL Server instance by setting Authentication to SqlPassword
    $serverName = "myserver.mydomain";

    $connectionInfo = "Database = $databaseName; Authentication = SqlPassword;";

    try
    {
        $conn = new PDO( "sqlsrv:server = $serverName ; $connectionInfo", $myusername, $mypassword );
        echo "Connected successfully with Authentication=SqlPassword.\n";
        $conn = null;
    }
    catch( PDOException $e )
    {
        echo "Could not connect with Authentication=SqlPassword.\n";
        print_r( $e->getMessage() );
        echo "\n";
    }

    // Now connect to an Azure SQL database by setting Authentication to ActiveDirectoryPassword
    $azureServer = "myazureserver.database.windows.net";
    $azureDatabase = "myazuredatabase";
    $azureUsername = "myuid";
    $azurePassword = "mypassword";
    $connectionInfo = "Database = $azureDatabase; Authentication = ActiveDirectoryPassword;";

    try
    {
        $conn = new PDO( "sqlsrv:server = $azureServer ; $connectionInfo", $azureUsername, $azurePassword );
        echo "Connected successfully with Authentication=ActiveDirectoryPassword.\n";
        $conn = null;
    }
    catch( PDOException $e )
    {
        echo "Could not connect with Authentication=ActiveDirectoryPassword.\n";
        print_r( $e->getMessage() );
        echo "\n";
    }

    ?>
```
## <a name="see-also"></a>Vedere anche  
[Uso di Azure Active Directory con ODBC Driver](https://docs.microsoft.com/en-us/sql/connect/odbc/using-azure-active-directory)
