---
title: Connessione a MySQL (MySQLToSQL) | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-mysql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Connecting to MySQL, MySQL permission
- Connecting to MySQL,reconnecting
ms.assetid: 084c7020-f729-4f91-90e0-143f85fa68d1
caps.latest.revision: 13
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: e389f57c1ccff2145ecaed8bfa15b33549a3c9ea
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="connecting-to-mysql-mysqltosql"></a>Connessione a MySQL (MySQLToSQL)
Per eseguire la migrazione di database MySQL a SQL Server o SQL Azure, è necessario connettersi al database di MySQL che si desidera eseguire la migrazione. Quando ci si connette, SSMA Ottiene i metadati relativi a tutti gli schemi di MySQL e successivamente visualizzata nel riquadro di esplorazione dei metadati di MySQL. SSMA archivia le informazioni relative al server di database, ma non archivia le password.  
  
La connessione al database rimane attiva finché non si chiude il progetto. Quando si riapre il progetto, sarà necessario riconnettere se si desidera una connessione attiva al database.  
  
Metadati sul database MySQL non viene aggiornato automaticamente. In alternativa, se si desidera aggiornare i metadati nel Visualizzatore metadati MySQL, è necessario aggiornare manualmente la. Per ulteriori informazioni, vedere la sezione "Aggiornamento dei metadati di MySQL" più avanti in questo argomento.  
  
## <a name="required-mysql-permissions"></a>Autorizzazioni necessarie di MySQL  
L'account utilizzato per connettersi al database MySQL è necessario disporre almeno **CONNETTI** autorizzazioni. In questo modo di SSMA per ottenere i metadati da schemi di proprietà utente connesso. Per ottenere i metadati per gli oggetti in altri schemi e quindi convertire gli oggetti in questi schemi, l'account deve disporre delle autorizzazioni seguenti:  
  
-   "Mostra" privilegi per gli oggetti di database  
  
-   Privilegio 'SELECT' per 'Information_schema'  
  
-   Privilegio 'SELECT' per mysql (per funzioni definite dall'utente)  
  
## <a name="establishing-a-connection-to-mysql"></a>Stabilire una connessione a MySQL  
Quando ci si connette a un database, SSMA legge i metadati del database e quindi aggiunge i metadati del file di progetto. Questi metadati vengono utilizzati da SSMA quando converte gli oggetti in sintassi SQL Server o SQL Azure e quando esegue la migrazione di dati in SQL Server o SQL Azure. È possibile esplorare i metadati nel riquadro di esplorazione dei metadati di MySQL e le proprietà di singoli oggetti di database.  
  
> [!IMPORTANT]  
> Prima di tentare di connettersi, assicurarsi che il server di database è in esecuzione e può accettare connessioni.  
  
**Per la connessione a MySQL**  
  
1.  Nel **File** dal menu **connessione a MySQL** (questa opzione abilitata dopo la creazione del progetto).  
  
    Se in precedenza si è connessi a MySQL, sarà il nome del comando **Riconnetti a MySQL**.  
  
2.  Nel **Provider** , selezionare i Driver di MySQL 5.1 ODBC (attendibile). È il provider predefinito in modalità standard.  
  
3.  Nel **modalità** , quindi selezionare **modalità Standard**. Si tratta della modalità predefinita.  
  
    Per specificare il nome del server e la porta, utilizzare la modalità standard.  
  
4.  In **modalità Standard**, specificare i valori seguenti:  
  
    1.  Nel **nome Server** , immettere il nome del server MySQL. Nel **porta Server** , immettere il numero di porta da 3306. È la porta predefinita.  
  
    2.  Nel **nome utente** , immettere un account che disponga delle autorizzazioni necessarie di MySQL.  
  
    3.  Nel **Password** immettere la password per il nome utente specificato.  
  
5.  **SSL:** se si desidera connettersi in modo sicuro a MySQL, avvalersi di Secure Socket Layer (SSL) controllando il **SSL** casella di controllo.  
  
6.  **Configurare:** fornisce un'opzione per configurare la connessione a MySQL tramite Secure Socket Layer (SSL).  
  
    > [!NOTE]  
    > Per abilitare **configura**, SSL deve essere impostato su **True**.  
  
    Se si sceglie il pulsante "Configura", viene visualizzata una finestra di dialogo. Utilizzare la crittografia durante la connessione al MySQL Database, percorso file tre certificato seguenti presente nella finestra di dialogo deve essere definito [Privacy avanzata posta certificati (PEM)]:  
  
    -   **Autorità di certificazione SSL:** specifica il percorso in un file con un elenco di attendibilità le autorità di certificazione SSL.  
  
    -   **Certificato SSL:** specifica il nome del file di certificato SSL da utilizzare per stabilire una connessione sicura.  
  
    -   **CHIAVE di SSL:** specifica il nome del file di chiave SSL da utilizzare per stabilire una connessione sicura.  
  
    > [!NOTE]  
    > -   Il **OK** pulsante viene abilitato quando sono state fornite le informazioni necessarie. Se non sono validi tutti i percorsi di file, il pulsante "OK" rimarrà disabilitato.  
    > -   Il **Annulla** pulsante consente di chiudere la finestra di dialogo e **disattiva** all'opzione SSL dal modulo di connessione principale.  
  
7.  Per altre informazioni, vedere [connessione a MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connect-to-mysql-mysqltosql.md)  
  
## <a name="reconnecting-to-mysql"></a>La riconnessione a MySQL  
La connessione al server di database rimane attiva finché non si chiude il progetto. Quando si riapre il progetto, sarà necessario riconnettere se si desidera una connessione attiva al database. È possibile lavorare offline fino a quando non si desidera aggiornare i metadati vengono caricati gli oggetti di database SQL Server o SQL Azure e la migrazione dei dati.  
  
## <a name="refreshing-mysql-metadata"></a>Aggiornamento dei metadati di MySQL  
I metadati sul database MySQL non vengono aggiornati automaticamente. I metadati nel Visualizzatore metadati MySQL sono uno snapshot di metadati quando si è connessi prima o l'ultima volta che si aggiorna manualmente i metadati. È possibile aggiornare manualmente i metadati per tutti gli schemi, un singolo schema o singoli oggetti di database.  
  
**Per aggiornare i metadati**  
  
1.  Assicurarsi di essere connessi al database.  
  
2.  Nel Visualizzatore metadati MySQL, selezionare la casella di controllo accanto a ogni oggetto di nello schema o database che si desidera aggiornare.  
  
3.  Fare doppio clic su **schemi**, o allo schema o il database dell'oggetto e quindi selezionare **aggiornamento dal Database**.  
  
    Se non si dispone di una connessione attiva, verrà visualizzato SSMA il **connessione a MySQL** nella finestra di dialogo in modo che sia possibile connettersi.  
  
4.  Nell'aggiornamento dalla finestra di dialogo Database, specificare gli oggetti da aggiornare.  
  
    -   Per aggiornare un oggetto, scegliere il **Active** campo adiacente all'oggetto fino a quando non viene visualizzata una freccia.  
  
    -   Per impedire l'aggiornamento di un oggetto, fare clic su di **Active** campo adiacente all'oggetto fino a quando un **X** viene visualizzato.  
  
    -   Per aggiornare o rifiutare una categoria di oggetti, fare clic su di **Active** campo adiacente nella cartella di categoria.  
  
    -   Per visualizzare le definizioni della codifica a colori, fare clic su di **legenda** pulsante.  
  
5.  Scegliere **OK**.  
  
## <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo del processo di migrazione consiste [connessione a SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[Database MySQL la migrazione a SQL Server - SQL di Azure DB &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
