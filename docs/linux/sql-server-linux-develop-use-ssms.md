---
title: La gestione di SQL Server in Linux con SSMS | Documenti Microsoft
description: In questa esercitazione viene illustrato come utilizzare SQL Server Management Studio in Windows per connettersi a SQL Server in esecuzione in Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 30cc4564-f389-4707-9b25-8ba782cc5150
ms.workload: On Demand
ms.openlocfilehash: 98fdce174be9f7a3dc67d910a84f8558ede1b317
ms.sourcegitcommit: b4fd145c27bc60a94e9ee6cf749ce75420562e6b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2018
---
# <a name="use-sql-server-management-studio-ssms-on-windows-to-manage-sql-server-on-linux"></a>Utilizzare SQL Server Management Studio (SSMS) in Windows per la gestione di SQL Server in Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In questo argomento viene illustrato come utilizzare [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) per connettersi a SQL Server 2017 in Linux. SQL Server Management Studio è un'applicazione Windows, pertanto utilizzare SQL Server Management Studio, quando si dispone di un computer Windows in grado di connettersi a un'istanza remota di SQL Server in Linux.

Dopo avere stabilito la connessione, si esegue una semplice query Transact-SQL (T-SQL) per verificare la comunicazione con il database.

## <a name="install-the-newest-version-of-sql-server-management-studio"></a>Installare la versione più recente di SQL Server Management Studio

Quando si utilizza SQL Server, è consigliabile utilizzare sempre la versione più recente di SQL Server Management Studio (SSMS). La versione più recente di SQL Server Management Studio viene aggiornata continuamente, ottimizzazione e attualmente funziona con SQL Server Linux su 2017. Per scaricare e installare la versione più recente, vedere [scaricare SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md). Per rimanere aggiornati, la versione più recente di SSMS chiede di quando è disponibile una nuova versione disponibile per il download. 

## <a name="connect-to-sql-server-on-linux"></a>Connettersi a SQL Server in Linux

La procedura seguente viene illustrato come connettersi a SQL Server 2017 in Linux con SQL Server Management Studio.

1. Avviare SSMS digitando **Microsoft SQL Server Management Studio** nelle finestre di casella di ricerca e quindi fare clic sull'app desktop.

    ![SQL Server Management Studio](./media/sql-server-linux-develop-use-ssms/ssms.png)

2. Nel **Connetti al Server** finestra, immettere le informazioni seguenti (se è già in esecuzione SQL Server Management Studio, fare clic su **Connetti > motore di Database** per aprire la **Connetti al Server** finestra):

   | Impostazione | Description |
   |-----|-----|
   | **Tipo server** | Il valore predefinito è il motore di database; non modificare questo valore. |
   | **Nome server** | Immettere il nome di computer Linux SQL Server di destinazione o il relativo indirizzo IP. |
   | **Autenticazione** | Per SQL Server 2017 in Linux, usare **autenticazione di SQL Server**. |
   | **Account di accesso** | Immettere il nome di un utente con accesso a un database nel server (ad esempio, il valore predefinito **SA** account creato durante l'installazione). |
   | **Password** | Immettere la password per l'utente specificato (per il **SA** account, creato questo durante l'installazione). |

    ![SQL Server Management Studio: Connettersi al server di Database SQL](./media/sql-server-linux-develop-use-ssms/connect.png)

3. Fare clic su **Connetti**.

    > [!TIP]
    > Se si verifica un errore di connessione, provare a diagnosticare il problema dal messaggio di errore. Rivedere poi i [consigli per la risoluzione dei problemi di connessione](sql-server-linux-troubleshooting-guide.md#connection).
 
5. Dopo avere stabilito la connessione per il server SQL, **Esplora oggetti** verrà aperto e sarà ora possibile accedere al database per eseguire attività amministrative o eseguire query sui dati.
 
     ![Esplora oggetti](./media/sql-server-linux-develop-use-ssms/object-explorer.png)
     
## <a name="run-sample-queries"></a>Eseguire query di esempio

Dopo la connessione al server, è possibile connettersi a un database ed eseguire una query di esempio. Se si ha familiarità con la scrittura di query, vedere [la scrittura di istruzioni Transact-SQL](../t-sql/tutorial-writing-transact-sql-statements.md).

1. Identificare un database da utilizzare per eseguire una query. Potrebbe trattarsi di un nuovo database creato nel [esercitazione Transact-SQL](../t-sql/tutorial-writing-transact-sql-statements.md). Oppure potrebbe trattarsi di **AdventureWorks** database di esempio che si [scaricato e ripristinato](sql-server-linux-migrate-restore-database.md).
2. In **Esplora oggetti**, passare al database di destinazione nel server.
2. Il database e quindi scegliere **nuova Query**:

    ![Nuova query. Connettersi al Database di SQL server: SQL Server Management Studio](./media/sql-server-linux-develop-use-ssms/new-query.png)

3. Nella finestra query, scrivere una query Transact-SQL per selezionare i dati da una delle tabelle. Nell'esempio seguente consente di selezionare dati dal **Production. Product** sommario di **AdventureWorks** database.

        SELECT TOP 10 Name, ProductNumber
        FROM Production.Product
        ORDER BY Name ASC

4. Fare clic su di **Execute** pulsante:

    ![Esito positivo. Connettersi al Database di SQL server: SQL Server Management Studio](./media/sql-server-linux-develop-use-ssms/execute-query.png)

## <a name="next-steps"></a>Passaggi successivi

Oltre alle query, è possibile utilizzare le istruzioni T-SQL per creare e gestire i database.

Se si ha familiarità con T-SQL, vedere [esercitazione: scrittura di istruzioni Transact-SQL](../t-sql/tutorial-writing-transact-sql-statements.md) e [riferimento a Transact-SQL (motore di Database)](https://msdn.microsoft.com/library/bb510741.aspx).

Per ulteriori informazioni sull'utilizzo di SQL Server Management Studio, vedere [utilizzare SQL Server Management Studio](https://msdn.microsoft.com/library/ms174173.aspx).
