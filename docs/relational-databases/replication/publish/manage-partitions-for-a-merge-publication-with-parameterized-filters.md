---
title: "Gestione delle partizioni di una pubblicazione di tipo merge con filtri con parametri | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "partizioni [replica di SQL Server]"
  - "partizioni della replica di tipo merge [replica di SQL Server], SQL Server Management Studio"
  - "filtri con parametri [replica di SQL Server], gestione delle partizioni"
ms.assetid: fb5566fe-58c5-48f7-8464-814ea78e6221
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# Gestione delle partizioni di una pubblicazione di tipo merge con filtri con parametri
  In questo argomento viene descritto come gestire le partizioni per una pubblicazione di tipo merge con i filtri con parametri in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] o Replication Management Objects (RMO). È possibile utilizzare i filtri di riga con parametri per generare partizioni non sovrapposte. È possibile limitare tali partizioni in modo che solo una sottoscrizione riceva una determinata partizione. In questi casi, la presenza di un numero elevato di Sottoscrittori comporta un numero elevato di partizioni, che richiedono anche un numero uguale di snapshot partizionati. Per altre informazioni, vedere [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Indicazioni](#Recommendations)  
  
-   **Per gestire le partizioni di una pubblicazione di tipo merge con filtri con parametri, utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Oggetti RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Recommendations"></a> Indicazioni  
  
-   Se si crea, come consigliato, uno script per la topologia di replica, gli script di pubblicazione contengono le chiamate di stored procedure necessarie per creare le partizioni di dati. Lo script offre un riferimento per le partizioni create e un modo per ricreare, se necessario, una o più partizioni. Per altre informazioni, vedere [Scripting Replication](../../../relational-databases/replication/scripting-replication.md).  
  
-   Se una pubblicazione contiene filtri con parametri che producono sottoscrizioni con partizioni non sovrapposte ed è necessario ricreare un'eventuale sottoscrizione persa, rimuovere la partizione sottoscritta, ricreare la sottoscrizione, quindi ricreare la partizione. Per altre informazioni, vedere [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md). La replica genera script di creazione per le partizioni del Sottoscrittore esistenti al momento della generazione di uno script per la creazione della pubblicazione. Per altre informazioni, vedere [Scripting Replication](../../../relational-databases/replication/scripting-replication.md).  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Gestire le partizioni nella **partizioni di dati** pagina della **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo. Per ulteriori informazioni sull'accesso a questa finestra di dialogo, vedere [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md). In questa pagina è possibile creare ed eliminare partizioni, consentire ai Sottoscrittori di avviare la generazione e il recapito di snapshot, generare snapshot per una o più partizioni ed eliminare snapshot.  
  
#### Per creare una partizione  
  
1.  Nel **partizioni di dati** pagina della **Proprietà pubblicazione - \< pubblicazione>** nella finestra di dialogo fare clic su **Aggiungi**.  
  
2.  Nel **Aggiungi partizione dati** finestra di dialogo immettere un valore per il **HOST_NAME ()** e/o **SUSER_SNAME ()** valore associato alla partizione che si desidera creare.  
  
3.  Facoltativamente, specificare una pianificazione per l'aggiornamento degli snapshot:  
  
    1.  Selezionare **esecuzione pianificata dell'agente Snapshot per questa partizione per l'esecuzione seguente**  
  
    2.  Accettare la pianificazione predefinita per l'aggiornamento degli snapshot oppure fare clic su **Cambia** per specificare una pianificazione diversa.  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### Per eliminare una partizione  
  
1.  Nella pagina **Partizioni dati** selezionare una partizione della griglia.  
  
2.  Fare clic su **Elimina**.  
  
#### Per consentire ai Sottoscrittori di avviare la generazione e il recapito di snapshot  
  
1.  Nella pagina **Partizioni dati** selezionare **Definisci automaticamente una partizione e genera uno snapshot, se necessario, quando un nuovo Sottoscrittore cerca di eseguire la sincronizzazione**.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### Per generare lo snapshot di una partizione  
  
1.  Nella pagina **Partizioni dati** selezionare una partizione della griglia.  
  
2.  Fare clic su **Genera gli snapshot selezionati adesso**.  
  
#### Per eliminare lo snapshot di una partizione  
  
1.  Nella pagina **Partizioni dati** selezionare una partizione della griglia.  
  
2.  Fare clic su **Elimina gli snapshot esistenti**.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 Per migliorare la gestione di una pubblicazione con filtri con parametri, è possibile enumerare le partizioni esistenti a livello di programmazione, utilizzando stored procedure di replica. È inoltre possibile creare ed eliminare le partizioni esistenti. È possibile ottenere le informazioni seguenti sulle partizioni esistenti:  
  
-   Come una partizione viene filtrata (utilizzando [SUSER_SNAME & #40; Transact-SQL & #41;](../../../t-sql/functions/suser-sname-transact-sql.md) o [HOST_NAME & #40; Transact-SQL & #41;](../../../t-sql/functions/host-name-transact-sql.md)).  
  
-   Nome del processo che genera uno snapshot partizionato.  
  
-   Ora dell'ultima esecuzione di un processo di snapshot partizionato.  
  
 Mentre la seconda parte dello snapshot a due parti può essere generata su richiesta quando viene inizializzata una nuova sottoscrizione, le procedure descritte di seguito consentono di controllare il modo in cui tale snapshot viene generato e di effettuare la pregenerazione dello snapshot nel momento più appropriato. Per altre informazioni, vedere [Snapshots for Merge Publications with Parameterized Filters](../../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md).  
  
#### Per visualizzare informazioni sulle partizioni esistenti  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_helpmergepartition & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-helpmergepartition-transact-sql.md). Specificare il nome della pubblicazione per **@publication**. (Facoltativo) Specificare **@suser_sname** o **@host_name** per restituire informazioni solo in base a un solo criterio di filtro.  
  
#### Per definire una nuova partizione e generare un nuovo snapshot partizionato  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addmergepartition & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql.md). Specificare il nome della pubblicazione per **@publication**e il valore con parametri che definisce la partizione per uno degli elementi indicati di seguito.  
  
    -   **@suser_sname** : se il filtro con parametri è definito dal valore restituito da [SUSER_SNAME & #40; Transact-SQL & #41;](../../../t-sql/functions/suser-sname-transact-sql.md).  
  
    -   **@host_name** : se il filtro con parametri è definito dal valore restituito da [HOST_NAME & #40; Transact-SQL & #41;](../../../t-sql/functions/host-name-transact-sql.md).  
  
2.  Creare e inizializzare lo snapshot con parametri per la nuova partizione. Per altre informazioni, vedere [Create a Snapshot for a Merge Publication with Parameterized Filters](../../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
#### Per eliminare una partizione  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_dropmergepartition & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-dropmergepartition-transact-sql.md). Specificare il nome della pubblicazione per **@publication** e il valore con parametri che definisce la partizione per uno degli elementi indicati di seguito.  
  
    -   **@suser_sname** : se il filtro con parametri è definito dal valore restituito da [SUSER_SNAME & #40; Transact-SQL & #41;](../../../t-sql/functions/suser-sname-transact-sql.md).  
  
    -   **@host_name** : se il filtro con parametri è definito dal valore restituito da [HOST_NAME & #40; Transact-SQL & #41;](../../../t-sql/functions/host-name-transact-sql.md).  
  
     Viene inoltre effettuata la rimozione del processo di snapshot e degli eventuali file di snapshot per la partizione.  
  
##  <a name="RMOProcedure"></a> Utilizzo di RMO (Replication Management Objects)  
 Per migliorare la gestione di una pubblicazione con filtri con parametri, è possibile creare nuove partizioni del Sottoscrittore a livello di programmazione, enumerare le partizioni del Sottoscrittore esistenti ed eliminare quelle desiderate utilizzando oggetti RMO (Replication Management Objects). Per informazioni sulla creazione di partizioni del Sottoscrittore, vedere [Create a Snapshot for a Merge Publication with Parameterized Filters](../../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md). È possibile ottenere le informazioni seguenti sulle partizioni esistenti:  
  
-   Valore e funzione di filtro su cui si basa la partizione.  
  
-   Nome del processo che genera uno snapshot con parametri per il Sottoscrittore.  
  
-   Ora dell'ultima esecuzione di un processo di snapshot con parametri.  
  
#### Per visualizzare informazioni sulle partizioni esistenti  
  
1.  Creare una connessione al server di pubblicazione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.MergePublication> (classe). Impostare il <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> e <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> proprietà per la pubblicazione, quindi impostare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà per il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> creato nel passaggio 1.  
  
3.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo per ottenere le proprietà dell'oggetto. Se questo metodo restituisce **false**, le proprietà della pubblicazione sono state definite in modo non corretto nel passaggio 2 oppure la pubblicazione non esiste.  
  
4.  Chiamare il <xref:Microsoft.SqlServer.Replication.MergePublication.EnumMergePartitions%2A> metodo e passa il risultato a una matrice di <xref:Microsoft.SqlServer.Replication.MergePartition> oggetti.  
  
5.  Per ogni <xref:Microsoft.SqlServer.Replication.MergePartition> oggetto nella matrice, ottenere le proprietà di interesse.  
  
#### Per eliminare partizioni esistenti  
  
1.  Creare una connessione al server di pubblicazione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Creare un'istanza di <xref:Microsoft.SqlServer.Replication.MergePublication> (classe). Impostare il <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> e <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> proprietà per la pubblicazione, quindi impostare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà per il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> creato nel passaggio 1.  
  
3.  Chiamare il <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> metodo per ottenere le proprietà dell'oggetto. Se questo metodo restituisce **false**, le proprietà della pubblicazione sono state definite in modo non corretto nel passaggio 2 oppure la pubblicazione non esiste.  
  
4.  Chiamare il <xref:Microsoft.SqlServer.Replication.MergePublication.EnumMergePartitions%2A> metodo e passa il risultato a una matrice di <xref:Microsoft.SqlServer.Replication.MergePartition> oggetti.  
  
5.  Per ogni <xref:Microsoft.SqlServer.Replication.MergePartition> oggetto nella matrice, determinare se la partizione deve essere eliminata. Questa decisione è in genere in base al valore di <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterLogin%2A> proprietà o <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterHostName%2A> proprietà.  
  
6.  Chiamare il <xref:Microsoft.SqlServer.Replication.MergePublication.RemoveMergePartition%2A> metodo il <xref:Microsoft.SqlServer.Replication.MergePublication> oggetto dal passaggio 2. Passare il <xref:Microsoft.SqlServer.Replication.MergePartition> oggetto dal passaggio 5.  
  
7.  Ripetere il passaggio 6 per ogni partizione eliminata.  
  
## Vedere anche  
 [Filtri di riga con parametri](../../../relational-databases/replication/merge/parameterized-row-filters.md)   
 [Snapshot per pubblicazioni di tipo merge con filtri con parametri](../../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)  
  
  