---
title: Conversione dei database MySQL (MySQLToSQL) | Documenti Microsoft
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
ms.assetid: ac21850b-fb32-4704-9985-5759b7c688c7
caps.latest.revision: 17
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ee77ec5fa517bf955e3f83cb4a6540746215efb4
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="converting-mysql-databases-mysqltosql"></a>Conversione dei database MySQL (MySQLToSQL)
Dopo essersi connessi a MySQL, connesso alla [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure e imposta il progetto e le opzioni di mapping di dati, è possibile convertire oggetti di database MySQL [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o gli oggetti di database di SQL Azure.  
  
## <a name="the-conversion-process"></a>Il processo di conversione  
La conversione di oggetti di database utilizza le definizioni degli oggetti da MySQL, li converte simile [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SQL Azure o gli oggetti e quindi carica tali informazioni nei metadati di SSMA. Impossibile caricare le informazioni nell'istanza [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. È quindi possibile visualizzare gli oggetti e le relative proprietà utilizzando il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o Visualizzatore metadati di SQL Azure.  
  
Durante la conversione, SSMA Stampa messaggi di output nel riquadro di Output e i messaggi di errore nel riquadro elenco errori. Utilizzare le informazioni di output e l'errore per determinare se è necessario modificare i database di MySQL o il processo di conversione per ottenere i risultati di conversione desiderato.  
  
## <a name="setting-conversion-options"></a>Impostazione delle opzioni di conversione  
Prima di convertire gli oggetti, esaminare le opzioni di conversione del progetto nel **impostazioni progetto** la finestra di dialogo. Tramite questa finestra di dialogo, è possibile impostare la modalità di conversione di tabelle e indici in SSMA. Per ulteriori informazioni, vedere [impostazioni progetto &#40; Conversione &#41; &#40; MySQLToSQL &#41;](../../ssma/mysql/project-settings-conversion-mysqltosql.md)  
  
## <a name="conversion-results"></a>Risultati di conversione  
La tabella seguente mostra gli oggetti di MySQL vengono convertiti e il valore risultante [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oggetti:  
  
|||  
|-|-|  
|**Oggetti di MySQL**|**Oggetti SQL Server risultanti**|  
|Tabelle con gli oggetti dipendenti, ad esempio indici|SSMA consente di creare tabelle con gli oggetti dipendenti. Tabella viene quindi convertita con tutti gli indici e vincoli. Gli indici vengono convertiti in separato [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oggetti.<br /><br />**Mapping dei tipi di dati spaziali** possono essere eseguite solo a livello di nodo di tabella.<br /><br />Per ulteriori informazioni sulle impostazioni di conversione della tabella, vedere [le impostazioni di conversione](http://msdn.microsoft.com/en-us/f551cf6e-1575-4206-9cca-975b5b43a6b8)|  
|Funzioni|Se la funzione può essere convertita direttamente in Transact-SQL, SSMA crea una funzione. In alcuni casi, la funzione deve essere convertita a una stored procedure. Questa operazione può essere eseguita tramite **funzione di conversione** nelle impostazioni del progetto. In questo caso, SSMA crea una stored procedure e una funzione che chiama la stored procedure.<br /><br />**Digitare un valore:**<br /><br />Convertire in base alle impostazioni di progetto<br /><br />Convertire (funzione)<br /><br />Convertire in stored procedure<br /><br />Per ulteriori informazioni sulle impostazioni di conversione di funzione, vedere [le impostazioni di conversione](http://msdn.microsoft.com/en-us/f551cf6e-1575-4206-9cca-975b5b43a6b8)|  
|Procedure|Se la procedura può essere convertita direttamente in Transact-SQL, SSMA crea una stored procedure. In alcuni casi, una stored procedure deve essere chiamata in una transazione autonoma. In questo caso, SSMA crea due stored procedure: una che implementa la procedura e un altro che viene utilizzata per chiamare l'implementazione di stored procedure.|  
|Conversione del database|I database MySQL oggetti non vengono convertiti direttamente da SSMA per MySQL. Database MySQL vengono trattati più come nomi di schema e tutti i parametri fisici vengono persi durante la conversione. SSMA per MySQL Usa [Mapping database MySQL per gli schemi di SQL Server &#40; MySQLToSQL &#41; ](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md) per eseguire il mapping di oggetti di database MySQL a coppia o nello schema di database di SQL Server appropriato.|  
|Conversione di trigger|**SSMA consente di creare trigger in base alle regole seguenti:**<br /><br />PRIMA di trigger vengono convertiti nei trigger INSTEAD OF T-SQL<br /><br />I trigger AFTER vengono convertiti in trigger dopo T-SQL con o senza le iterazioni per righe.|  
|Conversione di visualizzazione|SSMA consente di creare visualizzazioni con gli oggetti dipendenti|  
|Conversione di istruzioni|-Oggetto ogni istruzione SQL può contenere una singola istruzione di MySQL (ad esempio DDL, DML e altri tipi di istruzioni) o BEGIN... Blocco finale.<br />-   **Conversione con istruzioni multiple: BEGIN... Conversione di fine blocco**istruzione SQL può anche contenere un blocco BEGIN... Blocco finale simile a quello nella definizione di stored procedure, funzioni o trigger. Tali blocchi devono essere convertiti allo stesso modo, che vengono convertiti per i singoli oggetti di istruzione di MySQL.|  
  
## <a name="converting-mysql-database-objects"></a>La conversione di oggetti di Database MySQL  
Per convertire gli oggetti di database MySQL, prima di selezionare gli oggetti che si desidera convertire e quindi chiedere di SSMA eseguire la conversione. Per visualizzare i messaggi di output durante la conversione nel **vista** dal menu **Output**.  
  
**Per convertire gli oggetti di MySQL in sintassi SQL Server o SQL Azure**  
  
1.  In Visualizzatore metadati MySQL, espandere il server MySQL e quindi espandere **database**.  
  
2.  Selezionare gli oggetti da convertire:  
  
    -   Per convertire tutti gli schemi, selezionare la casella di controllo accanto a **database**.  
  
    -   Per convertire o omettere un database, selezionare la casella di controllo accanto al nome del Database.  
  
    -   Per convertire o omettere una categoria di oggetti, espandere uno schema, quindi selezionare o deselezionare la casella di controllo accanto alla categoria.  
  
    -   Per convertire o omettere i singoli oggetti, espandere la cartella di categoria, quindi selezionare o deselezionare la casella di controllo accanto all'oggetto.  
  
3.  Per convertire tutti gli oggetti selezionati, fare doppio clic su **database** e selezionare **convertire Schema**.  
  
    È anche possibile convertire oggetti singoli o le categorie di oggetti facendo l'oggetto o la relativa cartella padre, quindi **convertire Schema**.  
  
## <a name="viewing-conversion-problems"></a>Visualizzazione di problemi di conversione  
Alcuni oggetti di MySQL potrebbero non essere convertiti. È possibile determinare le percentuali di successo di conversione visualizzando il report di riepilogo di conversione.  
  
**Per visualizzare un report di riepilogo**  
  
1.  Nel Visualizzatore metadati MySQL, selezionare **database**.  
  
2.  Nel riquadro di destra, selezionare il **Report** scheda.  
  
    Questo report mostra il report di riepilogo di valutazione per tutti gli oggetti di database che sono stati valutati o convertiti. È inoltre possibile visualizzare un report di riepilogo per i singoli oggetti:  
  
    -   Per visualizzare il report per un singolo schema, selezionare il database in Visualizzatore metadati MySQL.  
  
    -   Per visualizzare il report per un singolo oggetto, selezionare l'oggetto in Visualizzatore metadati MySQL. Gli oggetti che presentano problemi di conversione hanno un'icona di errore rossa.  
  
Per gli oggetti che non è stato possibile conversione, è possibile visualizzare la sintassi che ha generato l'errore di conversione.  
  
**Per visualizzare i problemi di conversione singoli**  
  
1.  Nel Visualizzatore metadati MySQL, espandere **database**.  
  
2.  Espandere il database che viene visualizzata un'icona di errore rossa.  
  
3.  Nel database, espandere una cartella che contiene un'icona di errore rossa.  
  
4.  Selezionare l'oggetto con un'icona di errore rossa.  
  
5.  Nel riquadro di destra, fare clic su di **Report** scheda.  
  
6.  Nella parte superiore del **Report** scheda è riportato un elenco a discesa. Se l'elenco Mostra **statistiche**, modificare la selezione di **origine**.  
  
    SSMA verrà visualizzato il codice sorgente e diversi pulsanti immediatamente sopra il codice.  
  
7.  Fare clic su di **problema successivo** pulsante. Si tratta di un'icona di errore rossa con una freccia rivolta verso destra.  
  
    SSMA verrà evidenziati il primo codice problematico origine che trova nell'oggetto corrente.  
  
Per ogni elemento che non è stato possibile convertire, è necessario determinare ciò che si desidera eseguire con tale oggetto:  
  
-   È possibile modificare l'oggetto nel database di MySQL per rimuovere o modificare il codice problematico. Per caricare il codice aggiornato in SSMA, è necessario aggiornare i metadati. Per ulteriori informazioni, vedere [connessione a MySQL &#40; MySQLToSQL &#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
  
-   È possibile escludere l'oggetto dalla migrazione. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure metadati Explorer e Visualizzatore metadati MySQL, deselezionare la casella di controllo accanto all'elemento prima di caricare gli oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure e la migrazione dei dati da MySQL.  
  
## <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo del processo di migrazione è [il caricamento di convertire gli oggetti di Database in SQL Server &#40; MySQLToSQL &#41;](../../ssma/mysql/loading-converted-database-objects-into-sql-server-mysqltosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database MySQL a SQL Server: database SQL di Azure &#40; MySQLToSql &#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  

