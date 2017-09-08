---
title: La connessione al Database di DB2 (DB2ToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 5eb5801d-f0c3-4127-97c0-0b1ef49f4844
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3c7d7f8162968d579f1e3e1346fb2498ebf941cb
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="connecting-to-db2-database-db2tosql"></a>La connessione al Database di DB2 (DB2ToSQL)
Per eseguire la migrazione di database DB2 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è necessario connettersi al database DB2 che si desidera eseguire la migrazione. Quando ci si connette, SSMA Ottiene i metadati relativi a tutti gli schemi di DB2 e successivamente visualizzata nel riquadro di esplorazione dei metadati di DB2. SSMA archivia le informazioni relative al server di database, ma non archivia le password.  
  
La connessione al database rimane attiva finché non si chiude il progetto. Quando si riapre il progetto, sarà necessario riconnettere se si desidera una connessione attiva al database.  
  
I metadati relativi al database DB2 non viene aggiornato automaticamente. In alternativa, se si desidera aggiornare i metadati nel Visualizzatore metadati DB2, è necessario aggiornare manualmente la. Per ulteriori informazioni, vedere la sezione "Aggiornamento dei metadati di DB2" più avanti in questo argomento.  
  
## <a name="required-db2-permissions"></a>Autorizzazioni necessarie DB2  
L'autorizzazione utente definisce l'elenco dei comandi e gli oggetti che sono disponibili per un utente. In tal modo, questo elenco controlla le azioni dell'utente. In DB2, sono presenti gruppi predeterminati di privilegi per l'autorizzazione a livello di istanza e a livello di un database DB2. In questo modo di SSMA per ottenere i metadati da schemi di proprietà utente connesso. Per ottenere i metadati per gli oggetti in altri schemi e quindi convertire gli oggetti in questi schemi, l'account deve disporre delle autorizzazioni seguenti:  
  
-   Schema per la migrazione dello schema è in genere concesso l'accesso pubblico a meno che non è stata utilizzata la parola chiave RESTRICT creazione  
  
-   Accesso ai dati per la migrazione dei dati richiede DATAACCESS  
  
## <a name="establishing-a-connection-to-db2"></a>Stabilire una connessione a DB2  
Quando ci si connette a un database, SSMA legge i metadati del database e quindi aggiunge i metadati del file di progetto. Questi metadati vengono utilizzati da SSMA durante la conversione di oggetti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] sintassi, e quando esegue la migrazione di dati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. È possibile esplorare i metadati nel riquadro Visualizzatore metadati DB2 e le proprietà di singoli oggetti di database.  
  
> [!IMPORTANT]  
> Prima di tentare di connettersi, assicurarsi che il server di database è in esecuzione e può accettare connessioni.  
  
**Per la connessione a DB2**  
  
1.  Nel **File** dal menu **connessione a DB2**.  
  
    Se in precedenza connesso a DB2, il nome di comando sarà **Riconnetti a DB2**.  
  
2.  Nel **Provider** casella verrà visualizzato il **Provider OLE DB** che è attualmente l'unico provider di accesso client di DB2.  
  
3.  Nel **Manager** è possibile selezionare una casella **Db2 per zOs**, o **DB2 per LUW**  
  
4.  Nel **modalità** selezionare **modalità Standard**, o **modalità della stringa di connessione**.  
  
    Per specificare il nome del server e la porta, utilizzare la modalità standard. Modalità nome servizio consente di specificare manualmente il nome del servizio di DB2. Utilizzare la modalità stringa di connessione per fornire una stringa di connessione completa.  
  
5.  Se si seleziona **modalità Standard**, specificare i valori seguenti:  
  
    -   Nel **nome Server** immettere o selezionare il nome o indirizzo IP del server di database.  
  
    -   Se il server di database non è configurato per accettare le connessioni sull'impostazione predefinita la porta (1521), immettere il numero di porta utilizzato per le connessioni di DB2 nel **porta Server** casella.  
  
    -   Nel **porta Server** , immettere il numero di porta TCP/IP.  
  
    -   Nel **Initial Catalog** , immettere il nome del database  
  
    -   Nel **nome utente** , immettere un account di DB2 che disponga delle autorizzazioni necessarie.  
  
    -   Nel **Password** immettere la password per il nome utente specificato.  
  
6.  Se si seleziona **modalità della stringa di connessione**, specificare una stringa di connessione nel **stringa di connessione** casella.  
  
    L'esempio seguente illustra una stringa di connessione OLE DB:  
  
    `Provider=OraOLEDB.DB2;Data Source=MyDB2DB;User Id=myUsername;Password=myPassword;`  
  
    Nell'esempio seguente viene illustrata una stringa di connessione Client DB2 che utilizza la sicurezza integrata:  
  
    `Data Source=MyDB2DB;Integrated Security=yes;`  
  
    Per ulteriori informazioni, vedere [OracleToSQL connettersi a Oracle &#40; &#41;](../../ssma/oracle/connect-to-oracle-oracletosql.md).  
  
## <a name="reconnecting-to-db2"></a>La riconnessione a DB2  
La connessione al server di database rimane attiva finché non si chiude il progetto. Quando si riapre il progetto, sarà necessario riconnettere se si desidera una connessione attiva al database. È possibile lavorare offline fino a quando non si desidera aggiornare i metadati, caricare gli oggetti di database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], e la migrazione dei dati.  
  
## <a name="refreshing-db2-metadata"></a>Aggiornamento dei metadati di DB2  
I metadati relativi al database DB2 non viene aggiornato automaticamente. I metadati nel Visualizzatore metadati DB2 sono uno snapshot di metadati quando si è connessi prima o l'ultima volta che si aggiorna manualmente i metadati. È possibile aggiornare manualmente i metadati per tutti gli schemi, un singolo schema o singoli oggetti di database.  
  
**Per aggiornare i metadati**  
  
1.  Assicurarsi di essere connessi al database.  
  
2.  Nel Visualizzatore metadati DB2, selezionare la casella di controllo accanto a ogni oggetto di nello schema o database che si desidera aggiornare.  
  
3.  Fare doppio clic su **schemi**, o allo schema o il database dell'oggetto e quindi selezionare **aggiornamento dal Database**.  
  
    Se non si dispone di una connessione attiva, verrà visualizzato SSMA il **connessione a DB2** nella finestra di dialogo in modo che sia possibile connettersi.  
  
4.  Nell'aggiornamento dalla finestra di dialogo Database, specificare gli oggetti da aggiornare.  
  
    -   Per aggiornare un oggetto, scegliere il **Active** campo adiacente all'oggetto fino a quando non viene visualizzata una freccia.  
  
    -   Per impedire l'aggiornamento di un oggetto, fare clic su di **Active** campo adiacente all'oggetto fino a quando un **X** viene visualizzato.  
  
    -   Per aggiornare o rifiutare una categoria di oggetti, fare clic su di **Active** campo adiacente nella cartella di categoria.  
  
    Per visualizzare le definizioni della codifica a colori, fare clic su di **legenda** pulsante.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok_md.md)]  
  
## <a name="next-step"></a>Passaggio successivo  
  
-   Il passaggio successivo del processo di migrazione consiste nel [connessione a SQL Server](http://msdn.microsoft.com/en-us/b59803cb-3cc6-41cc-8553-faf90851410e).  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database DB2 a SQL Server &#40; DB2ToSQL &#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  

