---
title: Connettersi a origini dati locali e condivisioni file di Azure con autenticazione di Windows | Microsoft Docs
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: lift-shift
ms.suite: sql
ms.custom: 
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9235ffd3225e76ee94067519c72e997c451d9893
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="connect-to-on-premises-data-sources-and-azure-file-shares-with-windows-authentication"></a>Connettersi a origini dati locali e condivisioni file di Azure con autenticazione di Windows
In questo articolo viene descritto come configurare il catalogo SSIS nel database SQL di Azure per eseguire pacchetti che usano l'autenticazione di Windows per connettersi a origini dati locali e condivisioni file di Azure.

Le credenziali del dominio specificate quando si esegue la procedura illustrata in questo articolo sono valide per tutte le esecuzioni di pacchetti nell'istanza del database SQL finché non si modificano o rimuovono le credenziali.

## <a name="connect-to-on-premises-data-sources"></a>Connettersi alle origini dati locali

### <a name="prerequisite"></a>Prerequisiti
Prima di configurare le credenziali del dominio per l'autenticazione di Windows, verificare se un computer non aggiunto al dominio è in grado di connettersi all'origine dati locale in modalità `runas`.

#### <a name="connecting-to-sql-server"></a>Connessione a SQL Server
Per verificare se è possibile connettersi a un'istanza di SQL Server locale, eseguire le operazioni seguenti:

1.  Per eseguire questo test, cercare un computer non appartenente al dominio.

2.  Nel computer non appartenente al dominio eseguire il comando riportato di seguito per avviare SQL Server Management Studio (SSMS) con le credenziali del dominio che si vuole usare:

    ```cmd
    runas.exe /netonly /user:<domain>\<username> SSMS.exe
    ```

3.  Controllare da SSMS se è possibile connettersi all'istanza di SQL Server locale che si prevede di usare.

#### <a name="connecting-to-a-file-share"></a>Connessione a una condivisione file
Per verificare se è possibile connettersi a una condivisione file locale, eseguire le operazioni seguenti:

1.  Per eseguire questo test, cercare un computer non appartenente al dominio.

2.  Nel computer non appartenente al dominio eseguire questo comando. Il comando apre una finestra del prompt dei comandi con le credenziali del dominio che si vuole usare, quindi verifica la connettività della condivisione file recuperando un elenco di directory.

    ```cmd
    runas.exe /netonly /user:<domain>\<username> cmd.exe
    dir \\fileshare
    ```

3.  Verificare se viene restituito l'elenco di directory per la condivisione file locale che si vuole usare.

### <a name="provide-domain-credentials"></a>Specificare le credenziali del dominio
Per specificare le credenziali del dominio che consentono ai pacchetti che usano l'autenticazione di Windows di connettersi alle origini dati locali, eseguire le operazioni seguenti:

1.  Con SQL Server Management Studio (SSMS) o un altro strumento connettersi al database SQL che ospita il database del catalogo SSIS (SSISDB). Per altre informazioni, vedere [Connettersi al database del catalogo SSISDB in Azure](ssis-azure-connect-to-catalog-database.md).

2.  Con SSISDB come database corrente, aprire una finestra di query.

3.  Eseguire la seguente stored procedure e specificare le credenziali del dominio appropriate:

    ```sql
    catalog.set_execution_credential @user='<your user name>', @domain='<your domain name>', @password='<your password>'
    ```
4.  Eseguire i pacchetti SSIS. I pacchetti usano le credenziali specificate per connettersi alle origini dati locali con autenticazione di Windows.

### <a name="view-domain-credentials"></a>Visualizzare le credenziali del dominio
Per visualizzare le credenziali del dominio attive, eseguire queste operazioni:

1.  Con SQL Server Management Studio (SSMS) o un altro strumento connettersi al database SQL che ospita il database del catalogo SSIS (SSISDB).

2.  Con SSISDB come database corrente, aprire una finestra di query.

3.  Eseguire la stored procedure seguente e controllare l'output:

    ```sql
    SELECT * 
    FROM catalog.master_properties
    WHERE property_name = 'EXECUTION_DOMAIN' OR property_name = 'EXECUTION_USER'
    ```

### <a name="clear-domain-credentials"></a>Cancellare le credenziali del dominio
Per cancellare e rimuovere le credenziali specificate come descritto in questo articolo, eseguire queste operazioni:

1.  Con SQL Server Management Studio (SSMS) o un altro strumento connettersi al database SQL che ospita il database del catalogo SSIS (SSISDB).

2.  Con SSISDB come database corrente, aprire una finestra di query.

3.  Eseguire la stored procedure seguente:

    ```sql
    catalog.set_execution_credential @user='', @domain='', @password=''
    ```

## <a name="connect-to-file-shares"></a>Connettersi alle condivisioni file
È possibile usare l'autenticazione di Windows per connettersi alle condivisioni file nella stessa rete virtuale del runtime di integrazione SSIS di Azure, sia in locale, sia nelle macchine virtuali di Azure e in File di Azure. Per altre informazioni sui file di Azure, vedere [File di Azure](https://azure.microsoft.com/services/storage/files/).

Per connettersi a una condivisione file in una macchina virtuale di Azure o una condivisione file di Azure, effettuare le operazioni seguenti:

1.  Con SQL Server Management Studio (SSMS) o un altro strumento connettersi al database SQL che ospita il database del catalogo SSIS (SSISDB).

2.  Con SSISDB come database corrente, aprire una finestra di query.

3.  Eseguire la stored procedure `catalog.set_execution_credential` come descritto nelle opzioni seguenti:

    a.  Per connettersi a una condivisione file in una macchina virtuale di Azure, eseguire la seguente stored procedure:

    ```sql
    catalog.set_execution_credential @domain = N'.', @user = N'username of local account on Azure virtual machine', @password = N'password'
    ```

    b.  Per connettersi a una condivisione file di Azure, ovvero in File di Azure, eseguire la seguente stored procedure:

    ```sql
    catalog.set_execution_credential @domain = N'Azure', @user = N'<storage-account-name>', @password = N'<storage-account-key>'
    ```

## <a name="next-steps"></a>Passaggi successivi
- Distribuire un pacchetto. Per altre informazioni, vedere [Distribuire un progetto SSIS con SQL Server Management Studio (SSMS)](../ssis-quickstart-deploy-ssms.md).
- Eseguire un pacchetto. Per altre informazioni, vedere [Eseguire un pacchetto SSIS con SQL Server Management Studio (SSMS)](../ssis-quickstart-run-ssms.md).
- Pianificare un pacchetto. Per altre informazioni, vedere [Pianificare l'esecuzione del pacchetto SSIS in Azure](ssis-azure-schedule-packages.md).
