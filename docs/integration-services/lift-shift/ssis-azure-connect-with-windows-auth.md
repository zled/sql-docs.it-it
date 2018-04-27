---
title: Connettersi a origini dati e condivisioni file con autenticazione di Windows | Microsoft Docs
ms.date: 02/05/2018
ms.topic: article
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: lift-shift
ms.suite: sql
ms.custom: ''
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c4e70d0ce14b4205c19140fc952a53725894679a
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="connect-to-on-premises-data-sources-and-azure-file-shares-with-windows-authentication"></a>Connettersi a origini dati locali e condivisioni file di Azure con autenticazione di Windows
In questo articolo viene descritto come configurare il catalogo SSIS nel database SQL di Azure per eseguire pacchetti che usano l'autenticazione di Windows per connettersi a origini dati locali e condivisioni file di Azure. È possibile usare l'autenticazione di Windows per connettersi alle origini dati nella stessa rete virtuale del runtime di integrazione SSIS di Azure, sia in locale che nelle macchine virtuali di Azure e in File di Azure.

> [!WARNING]
> Se non si specificano credenziali di dominio valide per l'autenticazione di Windows eseguendo `catalog`.`set_execution_credential` come descritto in questo articolo, i pacchetti che dipendono dall'autenticazione di Windows non possono connettersi alle origini dati e restituiscono errori in fase di esecuzione.

## <a name="you-can-only-use-one-set-of-credentials"></a>È possibile usare un solo set di credenziali

In questo momento, è possibile usare un solo set di credenziali in un pacchetto. Le credenziali del dominio specificate quando si esegue la procedura illustrata in questo articolo sono valide per tutte le esecuzioni di pacchetti interattive o pianificate sull'istanza del database SQL, finché non si modificano o rimuovono le credenziali. Se il pacchetto deve connettersi a più origini dati con set di credenziali diversi, potrebbe essere necessario dividere il pacchetto in più pacchetti.

Se una delle origini dati è File di Azure, è possibile aggirare questa limitazione eseguendo il montaggio della condivisione file di Azure in fase di esecuzione del pacchetto con `net use` o equivalente in un'attività Esegui processo. Per altre informazioni, vedere [Montare una condivisione file di Azure e accedere alla condivisione in Windows](https://docs.microsoft.com/azure/storage/files/storage-how-to-use-files-windows).

## <a name="provide-domain-credentials-for-windows-authentication"></a>Fornire le credenziali di dominio per l'autenticazione di Windows
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

## <a name="connect-to-an-on-premises-sql-server"></a>Connettersi a SQL Server locale
Per verificare se è possibile connettersi a un'istanza di SQL Server locale, eseguire le operazioni seguenti:

1.  Per eseguire questo test, cercare un computer non appartenente al dominio.

2.  Nel computer non appartenente al dominio eseguire il comando riportato di seguito per avviare SQL Server Management Studio (SSMS) con le credenziali del dominio che si vuole usare:

    ```cmd
    runas.exe /netonly /user:<domain>\<username> SSMS.exe
    ```

3.  Controllare da SSMS se è possibile connettersi all'istanza di SQL Server locale che si prevede di usare.

### <a name="prerequisites"></a>Prerequisites
Per connettersi a SQL Server locale da un pacchetto in esecuzione in Azure, è necessario abilitare i prerequisiti seguenti:

1.  In Gestione configurazione SQL Server abilitare il protocollo TCP/IP.
2.  Consentire l'accesso a un programma attraverso Windows Firewall. Per altre informazioni, vedere [Configurare Windows Firewall per consentire l'accesso a SQL Server](https://docs.microsoft.com/sql/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access).
3.  Per connettersi con l'autenticazione di Windows, verificare che il runtime di integrazione SSIS di Azure appartenga a una rete virtuale che include anche SQL Server locale.  Per altre informazioni, vedere [Aggiungere un runtime di integrazione SSIS di Azure a una rete virtuale](https://docs.microsoft.com/azure/data-factory/join-azure-ssis-integration-runtime-virtual-network). Usare quindi `catalog.set_execution_credential` per fornire le credenziali, come illustrato in questo articolo.

## <a name="connect-to-an-on-premises-file-share"></a>Connettersi a una condivisione file locale
Per verificare se è possibile connettersi a una condivisione file locale, eseguire le operazioni seguenti:

1.  Per eseguire questo test, cercare un computer non appartenente al dominio.

2.  Nel computer non appartenente al dominio eseguire questo comando. Il comando apre una finestra del prompt dei comandi con le credenziali del dominio che si vuole usare, quindi verifica la connettività della condivisione file recuperando un elenco di directory.

    ```cmd
    runas.exe /netonly /user:<domain>\<username> cmd.exe
    dir \\fileshare
    ```

3.  Verificare se viene restituito l'elenco di directory per la condivisione file locale che si vuole usare.

## <a name="connect-to-a-file-share-on-an-azure-vm"></a>Connettersi a una condivisione file in una VM di Azure
Per connettersi a una condivisione file in una macchina virtuale di Azure, seguire questa procedura:

1.  Con SQL Server Management Studio (SSMS) o un altro strumento connettersi al database SQL che ospita il database del catalogo SSIS (SSISDB).

2.  Con SSISDB come database corrente, aprire una finestra di query.

3.  Eseguire la stored procedure `catalog.set_execution_credential` come descritto nelle opzioni seguenti:

    ```sql
    catalog.set_execution_credential @domain = N'.', @user = N'username of local account on Azure virtual machine', @password = N'password'
    ```

## <a name="connect-to-a-file-share-in-azure-files"></a>Connettersi a una condivisione file in File di Azure
Per altre informazioni sui file di Azure, vedere [File di Azure](https://azure.microsoft.com/services/storage/files/).

Per connettersi a una condivisione file in una condivisione file di Azure, seguire questa procedura:

1.  Con SQL Server Management Studio (SSMS) o un altro strumento connettersi al database SQL che ospita il database del catalogo SSIS (SSISDB).

2.  Con SSISDB come database corrente, aprire una finestra di query.

3.  Eseguire la stored procedure `catalog.set_execution_credential` come descritto nelle opzioni seguenti:

    ```sql
    catalog.set_execution_credential @domain = N'Azure', @user = N'<storage-account-name>', @password = N'<storage-account-key>'
    ```

## <a name="next-steps"></a>Passaggi successivi
- Distribuire un pacchetto. Per altre informazioni, vedere [Distribuire un progetto SSIS con SQL Server Management Studio (SSMS)](../ssis-quickstart-deploy-ssms.md).
- Eseguire un pacchetto. Per altre informazioni, vedere [Eseguire un pacchetto SSIS con SQL Server Management Studio (SSMS)](../ssis-quickstart-run-ssms.md).
- Pianificare un pacchetto. Per altre informazioni, vedere [Pianificare l'esecuzione del pacchetto SSIS in Azure](ssis-azure-schedule-packages.md).
