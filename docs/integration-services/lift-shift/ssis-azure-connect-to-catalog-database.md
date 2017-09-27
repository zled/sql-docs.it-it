---
title: Connettersi al database del catalogo di SSISDB in Azure | Documenti Microsoft
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
ms.openlocfilehash: 646999095957abb4e615b59b316b6ca59155dea3
ms.contentlocale: it-it
ms.lasthandoff: 09/25/2017

---
# <a name="connect-to-the-ssisdb-catalog-database-on-azure"></a>Connettersi al database del catalogo di SSISDB in Azure

Ottenere le informazioni di connessione è necessario connettersi al database del catalogo di SSISDB ospitata in un server di Database SQL di Azure. È necessario quanto segue per la connessione:
- nome completo del server
- Nome del database
- informazioni di accesso 

## <a name="prerequisites"></a>Prerequisiti
Prima di iniziare, verificare di che aver 17.2 per o versione successiva di SQL Server Management Studio. Per scaricare la versione più recente di SSMS, vedere [scaricare SQL Server Management Studio (SQL Server Management Studio)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

## <a name="get-the-connection-info-from-the-azure-portal"></a>Ottenere le informazioni di connessione dal portale di Azure
1. Accedere al [portale di Azure](https://portal.azure.com/).
2. Nel portale di Azure, selezionare **database SQL** dal menu a sinistra e quindi selezionare il `SSISDB` database il **database SQL** pagina. 
3. Nel **Panoramica** pagina per il `SSISDB` del database, controllare il nome completo del server, come illustrato nella figura seguente. Passare il mouse sul nome del server per visualizzare il **fare clic per copiare** opzione.

    ![Informazioni sulla connessione server](media/ssis-azure-connect-to-catalog-database/server-name.png) 

4. Se non si ricorda le informazioni di accesso per il server di Database SQL, passare alla pagina del Database di SQL server. Non esiste è possibile visualizzare l'amministratore del server name e, se necessario, reimpostare la password.

## <a name="connect-with-ssms"></a>La connessione con SQL Server Management Studio
1. Aprire SQL Server Management Studio.

2. **Connettersi al server**. Nel **Connetti al Server** finestra di dialogo immettere le informazioni seguenti:

   | Impostazione       | Valore consigliato | Description | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Tipo server** | Motore di database | Questo valore è obbligatorio. |
   | **Nome server** | Il nome completo del server | Il nome deve essere nel formato: **mysqldbserver.database.windows.net**. |
   | **Autenticazione** | autenticazione di SQL Server | Questa Guida rapida Usa autenticazione di SQL Server. |
   | **Account di accesso** | L'account amministratore del server | Si tratta dell'account specificato al momento della creazione del server. |
   | **Password** | La password per l'account di amministratore del server | Questa è la password specificata al momento della creazione del server. |

3. **Connettersi al database SSISDB**. Selezionare **opzioni** per espandere il **Connetti al Server** la finestra di dialogo. Nella struttura **Connetti al Server** la finestra di dialogo, seleziona il **le proprietà di connessione** scheda. Nel **Connetti al database** campo, selezionare o immettere `SSISDB`.

4. Selezionare quindi **Connetti**.

5. In Esplora oggetti espandere **cataloghi di Integration Services** e quindi espandere **SSISDB** per visualizzare gli oggetti nel database del catalogo SSIS.

## <a name="next-steps"></a>Passaggi successivi
- Distribuire un pacchetto. Per altre informazioni, vedere [distribuire un progetto SSIS con SQL Server Management Studio (SSMS)](../ssis-quickstart-deploy-ssms.md).
- Eseguire un pacchetto. Per altre informazioni, vedere [eseguire un pacchetto SSIS con SQL Server Management Studio (SSMS)](../ssis-quickstart-run-ssms.md).
- Pianificare un pacchetto. Per altre informazioni, vedere [del pacchetto SSIS di pianificazione di esecuzione in Azure](ssis-azure-schedule-packages.md)

