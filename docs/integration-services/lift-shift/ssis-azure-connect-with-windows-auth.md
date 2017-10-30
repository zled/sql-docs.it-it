---
title: Connettersi a origini dati locali con autenticazione di Windows | Documenti Microsoft
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-server-2017
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1e3d9736612211038991489a4bd858d1ff89d333
ms.openlocfilehash: 1b60d877c6c75a77dd16fa8cb1704e10baf36bdb
ms.contentlocale: it-it
ms.lasthandoff: 10/19/2017

---
# <a name="connect-to-on-premises-data-sources-with-windows-authentication"></a>Connettersi a origini dati locali con autenticazione di Windows
In questo articolo viene descritto come configurare il catalogo SSIS nel Database di SQL Azure per eseguire i pacchetti che utilizzano l'autenticazione di Windows per connettersi alle origini dati locali.

Le credenziali di dominio fornito quando si esegue la procedura in questo articolo si applicano a tutte le esecuzioni dei pacchetti nell'istanza del Database SQL fino a quando non si modifica o rimuovere le credenziali.

## <a name="prerequisite"></a>Prerequisiti
Prima di configurare le credenziali di dominio per l'autenticazione di Windows, verificare se un computer aggiunto al dominio non può connettersi all'origine dati locale in `runas` modalità.

### <a name="connecting-to-sql-server"></a>Connessione a SQL Server
Per verificare se è possibile connettersi a un Server SQL locale, eseguire le operazioni seguenti:

1.  Per eseguire questo test, ricerca di un computer non appartenenti a un dominio.

2.  Nel computer non appartenenti a un dominio, eseguire il comando seguente per avviare SQL Server Management Studio (SSMS) con le credenziali di dominio che si desidera utilizzare:

    ```cmd
    runas.exe /netonly /user:<domain>\<username> SSMS.exe
    ```

3.  Da SQL Server Management Studio, controllare se è possibile connettersi a SQL Server locale che si desidera utilizzare.

### <a name="connecting-to-a-file-share"></a>Connessione a una condivisione file
Per verificare se è possibile connettersi a una condivisione di file locale, eseguire le operazioni seguenti:

1.  Per eseguire questo test, ricerca di un computer non appartenenti a un dominio.

2.  Nel computer non appartenenti a un dominio, eseguire il comando seguente. Questo comando apre prommpt un comando con le credenziali di dominio che si desidera utilizzare, quindi verifica la connettività alla condivisione di file tramite il recupero di un elenco di directory.

    ```cmd
    runas.exe /netonly /user:<domain>\<username> cmd.exe
    dir \\fileshare
    ```

3.  Controllare se viene restituito l'elenco di directory per on-premise file condivisione che si desidera utilizzare.

## <a name="provide-domain-credentials"></a>Fornire le credenziali di dominio
Per fornire le credenziali di dominio che consentono ai pacchetti di utilizzare l'autenticazione di Windows per connettersi a origini dati locali, eseguire le operazioni seguenti:

1.  Con SQL Server Management Studio (SSMS) o un altro strumento, connettersi al Database SQL che ospita il database del catalogo SSIS (SSISDB). Per altre informazioni, vedere [Connetti al database del catalogo di SSISDB in Azure](ssis-azure-connect-to-catalog-database.md).

2.  Con SSISDB come database corrente, aprire una finestra query.

3.  Eseguire la seguente stored procedure e fornire le credenziali di dominio appropriato:

    ```sql
    catalog.set_execution_credential @user='<your user name>', @domain='<your domain name>', @password='<your password>'
    ```
4.  Eseguire i pacchetti SSIS. I pacchetti utilizzano le credenziali fornite per connettersi a origini dati locali con autenticazione di Windows.

## <a name="view-domain-credentials"></a>Visualizza le credenziali di dominio
Per visualizzare le credenziali di dominio active, eseguire le operazioni seguenti:

1.  Con SQL Server Management Studio (SSMS) o un altro strumento, connettersi al Database SQL che ospita il database del catalogo SSIS (SSISDB).

2.  Con SSISDB come database corrente, aprire una finestra query.

3.  Eseguire la stored procedure seguente e controllare l'output:

    ```sql
    SELECT * 
    FROM catalog.master_properties
    WHERE property_name = 'EXECUTION_DOMAIN' OR property_name = 'EXECUTION_USER'
    ```

## <a name="clear-domain-credentials"></a>Credenziali di dominio non crittografato
Per cancellare e rimuovere le credenziali fornite come descritto in questo articolo, eseguire le operazioni seguenti:

1.  Con SQL Server Management Studio (SSMS) o un altro strumento, connettersi al Database SQL che ospita il database del catalogo SSIS (SSISDB).

2.  Con SSISDB come database corrente, aprire una finestra query.

3.  Eseguire la stored procedure seguente:

    ```sql
    catalog.set_execution_credential @user='', @domain='', @password=''
    ```

## <a name="connect-to-file-shares"></a>Connettersi alle condivisioni file
È possibile utilizzare l'autenticazione di Windows per connettersi alle condivisioni di file nella stessa rete virtuale come il Runtime di integrazione SSIS di Azure in locale e in macchine virtuali di Azure.

Per connettersi a una condivisione file in una macchina virtuale di Azure, effettuare le operazioni seguenti:

1.  Con SQL Server Management Studio (SSMS) o un altro strumento, connettersi al Database SQL che ospita il database del catalogo SSIS (SSISDB).

2.  Con SSISDB come database corrente, aprire una finestra query.

3.  Eseguire la stored procedure seguente:

    ```sql
    catalog.set_execution_credential @domain = N'.', @user = N'username of local account on Azure virtual machine', @password = N'password'
    ```

## <a name="next-steps"></a>Passaggi successivi
- Distribuire un pacchetto. Per altre informazioni, vedere [distribuire un progetto SSIS con SQL Server Management Studio (SSMS)](../ssis-quickstart-deploy-ssms.md).
- Eseguire un pacchetto. Per altre informazioni, vedere [eseguire un pacchetto SSIS con SQL Server Management Studio (SSMS)](../ssis-quickstart-run-ssms.md).
- Pianificare un pacchetto. Per altre informazioni, vedere [del pacchetto SSIS di pianificazione di esecuzione in Azure](ssis-azure-schedule-packages.md)

