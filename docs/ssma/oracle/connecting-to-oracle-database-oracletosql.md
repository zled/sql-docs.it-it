---
title: La connessione al Database Oracle (OracleToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-oracle
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Refreshing Oracle Metadata
ms.assetid: e276cdbf-3ebc-4ba8-b40d-a7a42befa2b6
caps.latest.revision: "9"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: On Demand
ms.openlocfilehash: df379493d026c3cc3da3bf01ea036e8f32072625
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="connecting-to-oracle-database-oracletosql"></a>La connessione al Database Oracle (OracleToSQL)
Per eseguire la migrazione di database Oracle a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è necessario connettersi al database Oracle che si desidera eseguire la migrazione. Quando ci si connette, SSMA Ottiene i metadati relativi a tutti gli schemi di Oracle e quindi visualizzato nel riquadro di esplorazione dei metadati di Oracle. SSMA archivia le informazioni relative al server di database, ma non archivia le password.  
  
La connessione al database rimane attiva finché non si chiude il progetto. Quando si riapre il progetto, sarà necessario riconnettere se si desidera una connessione attiva al database.  
  
I metadati relativi al database Oracle non viene aggiornato automaticamente. In alternativa, se si desidera aggiornare i metadati nel Visualizzatore metadati Oracle, è necessario aggiornare manualmente la. Per ulteriori informazioni, vedere la sezione "Aggiornamento dei metadati di Oracle" più avanti in questo argomento.  
  
## <a name="required-oracle-permissions"></a>Autorizzazioni necessarie Oracle  
L'account utilizzato per connettersi al database Oracle deve disporre di almeno **CONNETTI** autorizzazioni. In questo modo di SSMA per ottenere i metadati da schemi di proprietà utente connesso. Per ottenere i metadati per gli oggetti in altri schemi e quindi convertire gli oggetti in questi schemi, l'account deve disporre delle autorizzazioni seguenti:  
  
-   CREARE UNA ROUTINE  
  
-   ESEGUIRE TUTTE LE PROCEDURE  
  
-   SELEZIONARE UNA TABELLA  
  
-   SELEZIONARE QUALSIASI SEQUENZA  
  
-   CREARE QUALSIASI TIPO  
  
-   CREARE UN TRIGGER  
  
-   SELEZIONARE QUALSIASI DIZIONARIO  
  
## <a name="establishing-a-connection-to-oracle"></a>Stabilire una connessione a Oracle  
Quando ci si connette a un database, SSMA legge i metadati del database e quindi aggiunge i metadati del file di progetto. Questi metadati vengono utilizzati da SSMA durante la conversione di oggetti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] sintassi, e quando esegue la migrazione di dati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. È possibile esplorare i metadati nel riquadro Visualizzatore metadati Oracle ed esaminare le proprietà di singoli oggetti di database.  
  
> [!IMPORTANT]  
> Prima di tentare di connettersi, assicurarsi che il server di database è in esecuzione e può accettare connessioni.  
  
**Per connettersi a Oracle**  
  
1.  Nel **File** dal menu **Connect to Oracle**.  
  
    Se in precedenza connesso a Oracle, il nome di comando sarà **Riconnetti a Oracle**.  
  
2.  Nel **Provider** , quindi selezionare **Provider Client Oracle** o **Provider OLE DB**, a seconda di quale provider è installato. Il valore predefinito è il client Oracle.  
  
3.  Nel **modalità** selezionare **modalità Standard**, **modalità TNSNAME**, o **modalità della stringa di connessione**.  
  
    Per specificare il nome del server e la porta, utilizzare la modalità standard. Modalità nome servizio consente di specificare manualmente il nome del servizio Oracle. Utilizzare la modalità stringa di connessione per fornire una stringa di connessione completa.  
  
4.  Se si seleziona **modalità Standard**, specificare i valori seguenti:  
  
    1.  Nel **nome Server** immettere o selezionare il nome o indirizzo IP del server di database.  
  
    2.  Se il server di database non è configurato per accettare le connessioni sull'impostazione predefinita la porta (1521), immettere il numero di porta utilizzato per le connessioni di Oracle nel **porta Server** casella.  
  
    3.  Nel **SID Oracle** , immettere l'identificatore di sistema.  
  
    4.  Nel **nome utente** , immettere un account di Oracle che disponga delle autorizzazioni necessarie.  
  
    5.  Nel **Password** immettere la password per il nome utente specificato.  
  
5.  Se si seleziona **modalità TNSNAME**, specificare i valori seguenti:  
  
    1.  Nel **connettersi identificatore** , immettere l'identificatore (alias TNS) del database di connettersi.  
  
    2.  Nel **nome utente** , immettere un account di Oracle che disponga delle autorizzazioni necessarie.  
  
    3.  Nel **Password** immettere la password per il nome utente specificato.  
  
6.  Se si seleziona **modalità della stringa di connessione**, specificare una stringa di connessione nel **stringa di connessione** casella.  
  
    L'esempio seguente illustra una stringa di connessione OLE DB:  
  
    `Provider=OraOLEDB.Oracle;Data Source=MyOracleDB;User Id=myUsername;Password=myPassword;`  
  
    Nell'esempio seguente viene illustrata una stringa di connessione Oracle Client che utilizza la sicurezza integrata:  
  
    `Data Source=MyOracleDB;Integrated Security=yes;`  
  
    Per ulteriori informazioni, vedere [OracleToSQL connettersi a Oracle &#40; &#41;](../../ssma/oracle/connect-to-oracle-oracletosql.md).  
  
## <a name="reconnecting-to-oracle"></a>Connettersi a Oracle  
La connessione al server di database rimane attiva finché non si chiude il progetto. Quando si riapre il progetto, sarà necessario riconnettere se si desidera una connessione attiva al database. È possibile lavorare offline fino a quando non si desidera aggiornare i metadati, caricare gli oggetti di database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], e la migrazione dei dati.  
  
## <a name="refreshing-oracle-metadata"></a>Aggiornamento dei metadati di Oracle  
I metadati relativi al database Oracle non viene aggiornato automaticamente. I metadati nel Visualizzatore metadati Oracle sono uno snapshot di metadati quando si è connessi prima o l'ultima volta che si aggiorna manualmente i metadati. È possibile aggiornare manualmente i metadati per tutti gli schemi, un singolo schema o singoli oggetti di database.  
  
**Per aggiornare i metadati**  
  
1.  Assicurarsi di essere connessi al database.  
  
2.  Nel Visualizzatore metadati Oracle, selezionare la casella di controllo accanto a ogni oggetto di nello schema o database che si desidera aggiornare.  
  
3.  Fare doppio clic su **schemi**, o allo schema o il database dell'oggetto e quindi selezionare **aggiornamento dal Database**.  
  
    Se non si dispone di una connessione attiva, verrà visualizzato SSMA il **Connect to Oracle** nella finestra di dialogo in modo che sia possibile connettersi.  
  
4.  Nell'aggiornamento dalla finestra di dialogo Database, specificare gli oggetti da aggiornare.  
  
    -   Per aggiornare un oggetto, scegliere il **Active** campo adiacente all'oggetto fino a quando non viene visualizzata una freccia.  
  
    -   Per impedire l'aggiornamento di un oggetto, fare clic su di **Active** campo adiacente all'oggetto fino a quando un **X** viene visualizzato.  
  
    -   Per aggiornare o rifiutare una categoria di oggetti, fare clic su di **Active** campo adiacente nella cartella di categoria.  
  
    Per visualizzare le definizioni della codifica a colori, fare clic su di **legenda** pulsante.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok_md.md)]  
  
## <a name="next-step"></a>Passaggio successivo  
  
-   Il passaggio successivo del processo di migrazione consiste nel [connettersi a un'istanza di SQL Server](http://msdn.microsoft.com/en-us/1b2a8059-1829-4904-a82f-9c06de1e245f).  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database Oracle a SQL Server &#40; OracleToSQL &#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
