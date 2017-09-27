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
ms.translationtype: MT
ms.sourcegitcommit: dbe6f832d4af55ddd15e12fba17a4da490fe19ae
ms.openlocfilehash: 25113093ccd068a9afe661e160ae3319025b7534
ms.contentlocale: it-it
ms.lasthandoff: 09/25/2017

---
# <a name="connect-to-on-premises-data-sources-with-windows-authentication"></a>Connettersi a origini dati locali con autenticazione di Windows
In questo articolo viene descritto come configurare il catalogo SSIS nel Database di SQL Azure per eseguire i pacchetti che utilizzano l'autenticazione di Windows per connettersi alle origini dati locali.

Le credenziali di dominio fornito quando si esegue la procedura in questo articolo si applicano a tutte le esecuzioni dei pacchetti nell'istanza del Database SQL fino a quando non si modifica o rimuovere le credenziali.

## <a name="prerequisite"></a>Prerequisiti
Prima di configurare le credenziali di dominio per l'autenticazione di Windows, verificare se un computer aggiunto al dominio non può connettersi alle origini dati locali in `runas` modalità. Ad esempio, per controllare se è possibile connettersi a un Server SQL locale, eseguire le operazioni seguenti:

1.  Per eseguire questo test, è presente un computer non appartenenti a un dominio.

2.  Nel computer non appartenenti a un dominio, eseguire il comando seguente per avviare SQL Server Management Studio (SSMS) con le credenziali di dominio che si desidera utilizzare:

   ```cmd
   runas.exe /netonly /user:<domain>\<username> SSMS.exe
   ```

3.  Da SQL Server Management Studio, controllare se è possibile connettersi a SQL Server locale che si desidera utilizzare.

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

## <a name="next-steps"></a>Passaggi successivi
- Distribuire un pacchetto. Per altre informazioni, vedere [distribuire un progetto SSIS con SQL Server Management Studio (SSMS)](../ssis-quickstart-deploy-ssms.md).
- Eseguire un pacchetto. Per altre informazioni, vedere [eseguire un pacchetto SSIS con SQL Server Management Studio (SSMS)](../ssis-quickstart-run-ssms.md).
- Pianificare un pacchetto. Per altre informazioni, vedere [del pacchetto SSIS di pianificazione di esecuzione in Azure](ssis-azure-schedule-packages.md)

