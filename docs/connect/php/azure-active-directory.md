---
title: Azure Active Directory | Microsoft Docs
ms.date: 07/13/2017
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
author: david-puglielli
ms.author: v-dapugl
manager: v-hakaka
ms.openlocfilehash: 67f32c2c48188b3bcff50e22ca66bf2f563b1704
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47814829"
---
# <a name="connect-using-azure-active-directory-authentication"></a>Connessione con l'autenticazione di Azure Active Directory
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-whatis) (Azure AD) è una tecnologia di gestione ID utente centrale che opera come alternativa alla [autenticazione di SQL Server](../../connect/php/how-to-connect-using-sql-server-authentication.md). Azure AD consente le connessioni al Database SQL di Microsoft Azure e SQL Data Warehouse con le identità federate in Azure AD usando un nome utente e password, autenticazione integrata di Windows o un token di accesso di Azure AD; il driver PHP per SQL Server offre il supporto parziale per queste funzionalità.

Per usare Azure AD, usare il **autenticazione** (parola chiave). I valori che **autenticazione** può richiedere via sono illustrati nella tabella seguente.

|Parola chiave|Valori|Descrizione|
|-|-|-|
|**Autenticazione**|Non impostato (valore predefinito)|Modalità di autenticazione determinata da altre parole chiave. Per altre informazioni, vedere [Connection Options](../../connect/php/connection-options.md). |
||`SqlPassword`|L'autenticazione diretta a un'istanza di SQL Server, che può essere un'istanza di Azure, usando un nome utente e password. Il nome utente e la password deve essere passati nella stringa di connessione usando il **UID** e **PWD** parole chiave. |
||`ActiveDirectoryPassword`|Eseguire l'autenticazione con un'identità di Azure Active Directory usando un nome utente e password. Il nome utente e la password deve essere passati nella stringa di connessione usando il **UID** e **PWD** parole chiave. |

Il **autenticazione** (parola chiave) riguarda le impostazioni di sicurezza della connessione. Se è impostato nella stringa di connessione, quindi per impostazione predefinita il **Encrypt** parola chiave viene impostata su true, in modo che il client richiederà la crittografia. Inoltre, il certificato del server verrà da convalidare indipendentemente dall'impostazione di crittografia, a meno che **TrustServerCertificate** è impostato su true. Questa operazione si differenzia dal precedente e meno sicuro, metodo di accesso, in cui il certificato del server non viene convalidato, a meno che la crittografia è specificamente richiesta nella stringa di connessione.

Prima di usare Azure AD con il driver PHP per SQL Server in Windows, assicurarsi di aver installato il [Microsoft Online Services Sign-In Assistant](https://www.microsoft.com/download/details.aspx?id=41950) (non necessario per Linux e MacOS).

#### <a name="limitations"></a>Limitazioni

In Windows, il driver ODBC sottostante supporta un maggior valore per il **autenticazione** parola chiave **ActiveDirectoryIntegrated**, ma il driver PHP non supportano questo valore su qualsiasi piattaforma e pertanto anche non supportano l'autenticazione basata su token Azure AD.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato come connettersi usando **SqlPassword** e **ActiveDirectoryPassword**.

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

Nell'esempio seguente esegue la stessa come sopra con il driver PDO_SQLSRV.

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
[Uso di Azure Active Directory con ODBC Driver](https://docs.microsoft.com/sql/connect/odbc/using-azure-active-directory)
