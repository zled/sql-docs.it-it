---
title: 'Articolo aggiornato: documentazione dei database relazionali | Microsoft Docs'
description: Visualizza frammenti di contenuto aggiornato relativi alle modifiche recenti alla documentazione dei database relazionali.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: conceptual
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.prod_service: sql-non-specified
ms.component: relational-databases
ms.date: 04/28/2018
ms.openlocfilehash: 4f962279eb30e15b395f96417cc5e03aa1dbcfad
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39087773"
---
# <a name="new-and-recently-updated-relational-databases-docs"></a>Articoli nuovi e aggiornati di recente: documentazione dei database relazionali



Microsoft aggiorna quasi quotidianamente alcuni degli articoli presenti nel sito Web della documentazione [Docs.Microsoft.com](http://docs.microsoft.com/). Questo articolo contiene estratti degli articoli aggiornati di recente. Possono essere indicati anche collegamenti a nuovi articoli.

Questo articolo è generato da un programma che viene rieseguito periodicamente. In alcuni casi un estratto può avere una formattazione imperfetta o essere visualizzato come markdown dell'articolo di origine. Qui le immagini non vengono mai visualizzate.

Sono riportati gli aggiornamenti recenti per l'intervallo di date e l'area di interesse seguenti:



- *Intervallo di date degli aggiornamenti:* &nbsp; **03/02/2018** &nbsp; - &nbsp; **28/04/2018**
- *Area di interesse:* &nbsp; **database relazionali**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


1. [Join (SQL Server)](performance/joins.md)
2. [Sottoquery (SQL Server)](performance/subqueries.md)
3. [Configurare il database di distribuzione repliche nel gruppo di disponibilità Always On](replication/configure-distribution-availability-group.md)
4. [Individuazione dati e classificazione SQL](security/sql-data-discovery-and-classification.md)
5. [Guida per il controllo delle versioni delle righe e il blocco della transazione](sql-server-transaction-locking-and-row-versioning-guide.md)
6. [sys.dm_os_job_object (database SQL di Azure)](system-dynamic-management-views/sys-dm-os-job-object-transact-sql.md)
7. [Stored procedure di sistema per Filestream e tabelle FileTable (Transact-SQL)](system-stored-procedures/filestream-and-filetable-system-stored-procedures.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione sono visualizzati gli estratti degli aggiornamenti raccolti dagli articoli che recentemente sono stati sottoposti a un aggiornamento di grande entità.

Gli estratti visualizzati qui sono separati dal relativo contesto semantico. Inoltre è possibile che un estratto sia talvolta separato da importanti elementi di sintassi markdown che lo circondano nell'articolo vero e proprio. Di conseguenza, questi estratti devono essere usati solo come indicazioni generali. Gli estratti consentono solo di comprendere se sia utile o meno consultare l'articolo completo.

Per queste e altre ragioni, non copiare codice da questi estratti e non prendere come verità assoluta ciò che si legge negli estratti. Consultare gli articoli completi.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Elenco compatto degli articoli aggiornati di recente

Questo elenco compatto include i collegamenti a tutti gli articoli aggiornati elencati nella sezione degli estratti.

1. [Usare un file di formato per ignorare una colonna di una tabella (SQL Server)](#TitleNum_1)
2. [Dati JSON in SQL Server](#TitleNum_2)
3. [Guida sull'architettura di elaborazione delle query](#TitleNum_3)
4. [Esercitazione: Preparare SQL Server per la replica: server di pubblicazione, server di distribuzione, sottoscrittore](#TitleNum_4)
5. [Esercitazione: Configurare la replica tra due server sempre connessi (replica transazionale)](#TitleNum_5)
6. [Esercitazione: Configurare la replica tra un server e più client per dispositivi mobili (replica di tipo merge)](#TitleNum_6)
7. [Eseguire query con ricerca full-text](#TitleNum_7)
8. [Transparent Data Encryption con supporto Bring Your Own Key per database SQL di Azure e SQL Data Warehouse](#TitleNum_8)
9. [PowerShell e CLI: abilitare Transparent Data Encryption usando la propria chiave di Azure Key Vault](#TitleNum_9)
10. [Informazioni su Change Data Capture (SQL Server)](#TitleNum_10)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-use-a-format-file-to-skip-a-table-column-sql-serverimport-exportuse-a-format-file-to-skip-a-table-column-sql-servermd"></a>1. &nbsp; [Usare un file di formato per ignorare una colonna di una tabella (SQL Server)](import-export/use-a-format-file-to-skip-a-table-column-sql-server.md)

*Aggiornamento: 13/04/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Successivo](#TitleNum_2))

<!-- Source markdown line 221.  ms.author= "douglasl".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 167916d79c5de1e7f13990cb7acc41ceb541b9a7 cb92eb201292294e3397879c98f353fba45f1c1c  (PR=0  ,  Filename=use-a-format-file-to-skip-a-table-column-sql-server.md  ,  Dirpath=docs\relational-databases\import-export\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



**Uso di OPENROWSET(BULK...)**


Per usare un file di formato XML per ignorare una colonna di tabella usando `OPENROWSET(BULK...)`, è necessario specificare un elenco esplicito di colonne nell'elenco di selezione e anche nella tabella di destinazione, come illustrato di seguito:

```
    INSERT ...<column_list> SELECT <column_list> FROM OPENROWSET(BULK...)
```

Nell'esempio seguente viene utilizzato il provider di set di righe con lettura bulk `OPENROWSET` e il file di formato `myTestSkipCol2.xml` . Nell'esempio viene eseguita l'importazione bulk del file di dati `myTestSkipCol2.dat` nella tabella `myTestSkipCol` . L'istruzione contiene un elenco esplicito di colonne nell'elenco selezionato e nella tabella di destinazione, come richiesto.

In SSMS eseguire il codice seguente. Aggiornare i percorsi di file system per il percorso dei file di esempio nel computer in uso.

```
USE WideWorldImporters;
GO
INSERT INTO myTestSkipCol
  (Col1,Col3)
    SELECT Col1,Col3
      FROM  OPENROWSET(BULK  'C:\myTestSkipCol2.Dat',
      FORMATFILE='C:\myTestSkipCol2.Xml'
       ) as t1 ;
GO
```



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-json-data-in-sql-serverjsonjson-data-sql-servermd"></a>2. &nbsp;[Dati JSON in SQL Server](json/json-data-sql-server.md)

*Aggiornamento: 13/04/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_1) | [Successivo](#TitleNum_3))

<!-- Source markdown line 145.  ms.author= "jovanpop".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 19e276637a463b412f2c29a84f9fb7d0b0f5fcc5 e2f2e8b4732779b3f24561cc0c4da3a958f4edbb  (PR=0  ,  Filename=json-data-sql-server.md  ,  Dirpath=docs\relational-databases\json\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



È possibile che i documenti JSON abbiano sottoelementi e dati gerarchici che non possano essere mappati direttamente nelle colonne relazionali standard. In questo caso, è possibile rendere flat la gerarchia JSON unendo l'entità padre alle sottomatrici.

Nell'esempio seguente il secondo oggetto della matrice include una sottomatrice in cui sono rappresentate le competenze delle persone. Ogni oggetto secondario può essere analizzato tramite una chiamata di funzione `OPENJSON` aggiuntiva:

```
DECLARE @json NVARCHAR(MAX)
SET @json =
N'[
       { "id" : 2,"info": { "name": "John", "surname": "Smith" }, "age": 25 },
       { "id" : 5,"info": { "name": "Jane", "surname": "Smith", "skills": ["SQL", "C#", "Azure"] }, "dob": "2005-11-04T12:00:00" }
 ]'

SELECT *
FROM OPENJSON(@json)
  WITH (id int 'strict $.id',
        firstName nvarchar(50) '$.info.name', lastName nvarchar(50) '$.info.surname',
        age int, dateOfBirth datetime2 '$.dob',
    skills nvarchar(max) '$.skills' as json)
    outer apply openjson( a.skills )
                     with ( skill nvarchar(8) '$' ) as b
```
La matrice **skills** (competenze) viene restituita nella prima funzione `OPENJSON` come frammento di testo JSON originale e passata a un'altra funzione `OPENJSON` tramite l'operatore `APPLY`. La seconda funzione `OPENJSON` analizza la matrice JSON e restituisce i valori stringa come singolo set di righe di colonna che viene poi unito al risultato della prima funzione `OPENJSON`.
Il risultato di questa query è illustrato nella tabella seguente:

**Risultati**

|id|firstName|lastName|age|dateOfBirth|skill|
|--------|---------------|--------------|---------|-----------------|----------|
|2|John|Smith|25|||
|5|Jane|Smith||2005-11-04T12:00:00|SQL|
|5|Jane|Smith||2005-11-04T12:00:00|C#|
|5|Jane|Smith||2005-11-04T12:00:00|Azure|

`OUTER APPLY OPENJSON` unisce l'entità di primo livello alla sottomatrice e restituisce un set di risultati flat. Dato il join, la seconda riga sarà ripetuta per ogni competenza.




&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-query-processing-architecture-guidequery-processing-architecture-guidemd"></a>3. &nbsp; [Guida sull'architettura di elaborazione delle query](query-processing-architecture-guide.md)

*Aggiornamento: 13/04/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_2) | [Successivo](#TitleNum_4))

<!-- Source markdown line 34.  ms.author= "jroth".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 96d91b39acdb2f32aaff323e374e92d6f229d241 2c1d2f8585632ada174388399782dc3ed2721dba  (PR=0  ,  Filename=query-processing-architecture-guide.md  ,  Dirpath=docs\relational-databases\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



**Ordine di precedenza degli operatori logici**


Se in un'istruzione vengono usati più operatori logici, viene valutato prima `NOT`, quindi `AND` e infine `OR`. Gli operatori aritmetici (e bit per bit) vengono valutati prima degli operatori logici. Per altre informazioni, vedere [Precedenza degli operatori].

Nell'esempio seguente la condizione per il colore riguarda il modello di prodotto 21 e non il modello di prodotto 20, perché `AND` ha la priorità rispetto a `OR`.

```
SELECT ProductID, ProductModelID
FROM Production.Product
WHERE ProductModelID = 20 OR ProductModelID = 21
  AND Color = 'Red';
GO
```

È possibile modificare il significato della query aggiungendo le parentesi in modo da imporre la priorità dell'operatore `OR` nell'ordine di valutazione. La query seguente trova solo i prodotti di colore rosso dei modelli 20 e 21.

```
SELECT ProductID, ProductModelID
FROM Production.Product
WHERE (ProductModelID = 20 OR ProductModelID = 21)
  AND Color = 'Red';
GO
```

L'uso delle parentesi, anche quando non è obbligatorio, può contribuire a rendere le query più leggibili e a ridurre il rischio di errori dovuti all'ordine di precedenza degli operatori. Non ha inoltre alcun effetto negativo rilevante sulle prestazioni. L'esempio seguente risulta più leggibile rispetto a quello precedente, anche se sintatticamente i due esempi sono identici.

```
SELECT ProductID, ProductModelID
FROM Production.Product
WHERE ProductModelID = 20 OR (ProductModelID = 21
  AND Color = 'Red');
GO
```




&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-tutorial-prepare-sql-server-for-replication---publisher-distributor-subscriberreplicationtutorial-preparing-the-server-for-replicationmd"></a>4. &nbsp; [Esercitazione: Preparare SQL Server per la replica: server di pubblicazione, server di distribuzione, sottoscrittore](replication/tutorial-preparing-the-server-for-replication.md)

*Aggiornamento: 13/04/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_3) | [Successivo](#TitleNum_5))

<!-- Source markdown line 56.  ms.author= "mathoma".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 6e5caedacff193ce79bdd98708ae1b9dc91f0a8f 9f7af4d3f8b1cffd048db2a5b29fc9e6013f5ed2  (PR=0  ,  Filename=tutorial-preparing-the-server-for-replication.md  ,  Dirpath=docs\relational-databases\replication\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



- Installare [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
- Installare [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).
- Scaricare un [database campione AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases). Per istruzioni sul ripristino di un database in SSMS, vedere [Ripristino di un database](https://docs.microsoft.com/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms).

>[!NOTE]
> - La replica non è supportata per server SQL Server con versioni la cui distanza sia maggiore di 2. Per altre informazioni, vedere [Supported SQL Versions in Repl Topology](https://blogs.msdn.microsoft.com/repltalk/2016/08/12/suppported-sql-server-versions-in-replication-topology/) (Versioni di SQL Server supportate nella topologia di replica).
> - In *{Included-Content-Goes-Here}* è necessario connettersi al server di pubblicazione e al sottoscrittore usando un account di accesso che sia membro del ruolo predefinito del server **sysadmin**. Per altre informazioni sul ruolo sysadmin, vedere [Ruoli a livello di server](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/server-level-roles).


**Tempo stimato per il completamento dell'esercitazione: 30 minuti**

**Creare account di Windows per la replica**

In questa sezione verranno creati account di Windows per l'esecuzione degli agenti di replica. Verrà creato un account di Windows separato nel server locale per gli agenti seguenti:

|Agent|Percorso|Nome account|
|---------|------------|----------------|
|agente snapshot|Server di pubblicazione|<*nome_computer*>\repl_snapshot|



&nbsp;

&nbsp;

---

<a name="TitleNum_5"/>

### <a name="5-nbsp-tutorial-configure-replication-between-two-fully-connected-servers-transactionalreplicationtutorial-replicating-data-between-continuously-connected-serversmd"></a>5. &nbsp; [Esercitazione: Configurare la replica tra due server sempre connessi (replica transazionale)](replication/tutorial-replicating-data-between-continuously-connected-servers.md)

*Aggiornamento: 13/04/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_4) | [Successivo](#TitleNum_6))

<!-- Source markdown line 162.  ms.author= "mathoma".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0d74f984d0ffc01cce0376837e6d94df3c5654d7 4ecf4d724286130927dd43687d6845059af6f9b7  (PR=0  ,  Filename=tutorial-replicating-data-between-continuously-connected-servers.md  ,  Dirpath=docs\relational-databases\replication\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



**Creare una sottoscrizione per la pubblicazione transazionale**

In questa sezione si aggiungerà un sottoscrittore alla pubblicazione creata in precedenza. Questa esercitazione usa un sottoscrittore remoto (NODE2\SQL2016). È anche possibile, tuttavia, aggiungere localmente una sottoscrizione al server di pubblicazione.

**Per creare la sottoscrizione**


1.  Connettersi al server di pubblicazione in *{Included-Content-Goes-Here}*, espandere il nodo del server e quindi la cartella **Replica**.

2.  Nella cartella **Pubblicazioni locali** fare clic con il pulsante destro del mouse sulla pubblicazione **AdvWorksProductTrans** e quindi selezionare **Nuove sottoscrizioni**.  Verrà avviata la Creazione guidata nuova sottoscrizione:

    Nuova sottoscrizione

3.  Nella pagina Pubblicazione selezionare **AdvWorksProductTrans**e quindi Selezionare **Avanti**:

    Selezionare il server di pubblicazione transazionale

4.  Nella pagina Posizione in cui eseguire l'agente di distribuzione selezionare **Esegui tutti gli agenti nel database di distribuzione**e quindi selezionare **Avanti**.  Per altre informazioni sulle sottoscrizioni pull e push, vedere [Sottoscrivere le pubblicazioni](https://docs.microsoft.com/sql/relational-databases/replication/subscribe-to-publications):

    Esegui agenti nel database di distribuzione

5.  Nella pagina Sottoscrittori, se il nome dell'istanza del sottoscrittore non è visualizzato, selezionare **Aggiungi sottoscrittore** e quindi selezionare **Aggiungi Sottoscrittore SQL Server** dall'elenco a discesa. Verrà aperta la finestra di dialogo **Connetti al server**. Immettere il nome dell'istanza del sottoscrittore e quindi selezionare **Connetti**.



&nbsp;

&nbsp;

---

<a name="TitleNum_6"/>

### <a name="6-nbsp-tutorial-configure-replication-between-a-server-and-mobile-clients-mergereplicationtutorial-replicating-data-with-mobile-clientsmd"></a>6. &nbsp; [Esercitazione: Configurare la replica tra un server e più client per dispositivi mobili (replica di tipo merge)](replication/tutorial-replicating-data-with-mobile-clients.md)

*Aggiornamento: 13/04/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_5) | [Successivo](#TitleNum_7))

<!-- Source markdown line 93.  ms.author= "mathoma".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0eed78dfe83c88358c030539a2b25d11ef5ec2d3 79b2a3f32c940fede94b11ad2a3ef8a00b911a39  (PR=0  ,  Filename=tutorial-replicating-data-with-mobile-clients.md  ,  Dirpath=docs\relational-databases\replication\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



La tabella Employee contiene una colonna (OrganizationNode) con tipo di dati hierarchyid, supportato per la replica solo in SQL Server 2017. Se si usa una build precedente a SQL Server 2017, nella parte inferiore della schermata viene visualizzato un messaggio che informa della possibilità di perdere dati se si usa questa colonna nella replica bidirezionale. Ai fini di questa esercitazione, questo messaggio può essere ignorato. Questo tipo di dati, tuttavia, deve essere replicato in un ambiente di produzione solo se si usa la build supportata. Per altre informazioni sulla replica del tipo di dati hierarchyid, vedere [Uso di colonne hierarchyid nella replica](https://docs.microsoft.com/sql/t-sql/data-types/hierarchyid-data-type-method-reference#using-hierarchyid-columns-in-replicated-tables)


-  Nella pagina Filtro righe tabella selezionare **Aggiungi** e quindi selezionare **Aggiungi filtro**.

-  Nella finestra di dialogo **Aggiungi filtro** selezionare **Employee (HumanResources)** in **Selezionare la tabella da filtrare**. Selezionare la colonna **LoginID**, selezionare la freccia a destra per aggiungere la colonna alla clausola WHERE della query di filtro e modificare la clausola WHERE come segue:

    ```
    WHERE [LoginID] = HOST_NAME()
    ```

    A. Selezionare **Una riga di questa tabella verrà inviata a una sola sottoscrizione** e quindi selezionare **OK**:

    Aggiungi filtro



- Nella pagina **Filtro righe tabella** selezionare **Employee (Human Resources)**, selezionare **Aggiungi** e quindi selezionare **Aggiungi join per estendere il filtro selezionato**.

    A. Nella finestra di dialogo **Aggiungi join** selezionare **Sales.SalesOrderHeader** in **Tabella unita in join**. Selezionare **L'istruzione per il join verrà scritta manualmente** e completare l'istruzione per il join come indicato di seguito:



&nbsp;

&nbsp;

---

<a name="TitleNum_7"/>

### <a name="7-nbsp-query-with-full-text-searchsearchquery-with-full-text-searchmd"></a>7. &nbsp; [Eseguire query con ricerca full-text](search/query-with-full-text-search.md)

*Aggiornamento: 13/04/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_6) | [Successivo](#TitleNum_8))

<!-- Source markdown line 247.  ms.author= "douglasl".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 5ec67b56aa0a6eadadbcfa8b73b6726e75eca2bb 4eb108b202d3dd035a312bac7872cf02bcf31cfa  (PR=0  ,  Filename=query-with-full-text-search.md  ,  Dirpath=docs\relational-databases\search\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



**Altre informazioni sulle ricerche di termini di generazione**


Le *forme flessive* sono costituite dai diversi tempi e coniugazioni di un verbo oppure dalle forme singolare e plurale di un sostantivo.

È possibile cercare, ad esempio, la forma flessiva della parola "guida". Se diverse righe della tabella contengono le parole "guida", "guide", "guidò", "guidando" e "guidato", tali parole vengono tutte incluse nel set di risultati, in quanto ognuna può essere generata in modo flessivo da "guida".

Per impostazione predefinita, [FREETEXT] e [FREETEXTTABLE] consentono di cercare le forme flessive di tutte le parole specificate. [CONTAINS] e [CONTAINSTABLE] supportano un argomento `INFLECTIONAL` facoltativo.

**Cercare sinonimi di una parola specifica**


Un *thesaurus* definisce i sinonimi specificati dall'utente per i termini. Per altre informazioni sui file del thesaurus, vedere [Configurare e gestire i file del thesaurus per la ricerca full-text].

Se viene aggiunta, ad esempio, una voce quale "{macchina, automobile, camion, furgone}" a un thesaurus, è possibile cercare la forma del thesaurus della parola "macchina". Il set di risultati includerà tutte le righe della tabella in cui viene eseguita la query che contengono le parole "automobile", "camion", "furgone" o "macchina", in quanto ognuna di queste parole appartiene al set di espansione dei sinonimi relativo alla parola "macchina".

[FREETEXT] e [FREETEXTTABLE] usano il thesaurus per impostazione predefinita. [CONTAINS] e [CONTAINSTABLE] supportano un argomento `THESAURUS` facoltativo.



&nbsp;

&nbsp;

---

<a name="TitleNum_8"/>

### <a name="8-nbsp-transparent-data-encryption-with-bring-your-own-key-support-for-azure-sql-database-and-data-warehousesecurityencryptiontransparent-data-encryption-byok-azure-sqlmd"></a>8. &nbsp; [Transparent Data Encryption con supporto Bring Your Own Key per database SQL di Azure e SQL Data Warehouse](security/encryption/transparent-data-encryption-byok-azure-sql.md)

*Aggiornamento: 24/04/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_7) | [Successivo](#TitleNum_9))

<!-- Source markdown line 110.  ms.author= "aliceku".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 9527658848d430bf0148be84474a75b232cbd112 70ed2a129c580962384f808e8526673957f00d2c  (PR=5662  ,  Filename=transparent-data-encryption-byok-azure-sql.md  ,  Dirpath=docs\relational-databases\security\encryption\  ,  MergeCommitSha40=91a9c812739a1c9a6ec9e7b8cda71ee1f5adae3d) -->



**Come configurare il ripristino di emergenza geografico con Azure Key Vault**


Per mantenere la disponibilità elevata delle protezioni TDE per i database crittografati, è necessario configurare gli Azure Key Vault ridondanti in base ai gruppi di failover del database SQL esistenti o desiderati o alle istanze di replica geografica attive.  Ogni server con replica geografica richiede un insieme di credenziali delle chiavi separato, che deve trovarsi nella stessa area di Azure del server. Se un database primario diventa inaccessibile a causa di un'interruzione in un'area e viene attivato un failover, il database secondario può sostituirlo usando l'insieme di credenziali delle chiavi secondario.

Per i database SQL di Azure con replica geografica, è necessaria la configurazione di Azure Key Vault seguente:
- Un database primario con un insieme di credenziali delle chiavi nell'area e un database secondario con un insieme di credenziali delle chiavi nell'area.
- Almeno un database secondario è obbligatorio, ne sono supportati fino a quattro.
- Database secondari di database secondari (concatenamento) non sono supportati.

La sezione seguente descrive i passaggi di installazione e configurazione in modo più dettagliato.

**Procedura di configurazione di Azure Key Vault**


- Installare [PowerShell](https://docs.microsoft.com/powershell/azure/install-azurerm-ps?view=azurermps-5.6.0)
- Creare due istanze di Azure Key Vault in due aree diverse usando [PowerShell per abilitare la proprietà di "eliminazione temporanea"](https://docs.microsoft.com/azure/key-vault/key-vault-soft-delete-powershell) per gli insiemi di credenziali delle chiavi. Questa opzione non è ancora disponibile nel portale di Azure Key Vault, ma è richiesta da SQL.
- Per il corretto funzionamento del backup e del ripristino delle chiavi è necessario che entrambi gli Azure Key Vault si trovino in due aree disponibili nella stessa area geografica di Azure.  Se è necessario che i due insiemi di credenziali delle chiavi si trovino in aree geografiche diverse per soddisfare i requisiti di ripristino di emergenza geografico di SQL, seguire il [processo BYOK](https://docs.microsoft.com/azure/key-vault/key-vault-hsm-protected-keys) che consente l'importazione delle chiavi da un modulo di protezione hardware locale.



&nbsp;

&nbsp;

---

<a name="TitleNum_9"/>

### <a name="9-nbsp-powershell-and-cli-enable-transparent-data-encryption-using-your-own-key-from-azure-key-vaultsecurityencryptiontransparent-data-encryption-byok-azure-sql-configuremd"></a>9. &nbsp; [PowerShell e CLI: abilitare Transparent Data Encryption usando la propria chiave di Azure Key Vault](security/encryption/transparent-data-encryption-byok-azure-sql-configure.md)

*Aggiornamento: 24/04/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_8) | [Successivo](#TitleNum_10))

<!-- Source markdown line 196.  ms.author= "aliceku".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 a0e00f5701d9a493f503a477c69097ce65aba174 721e8fb856a55ee1e8e9e7fc06036a03adab647b  (PR=5662  ,  Filename=transparent-data-encryption-byok-azure-sql-configure.md  ,  Dirpath=docs\relational-databases\security\encryption\  ,  MergeCommitSha40=91a9c812739a1c9a6ec9e7b8cda71ee1f5adae3d) -->



**Prerequisiti per l'interfaccia della riga di comando**


- È necessario avere una sottoscrizione di Azure ed essere un amministratore per tale sottoscrizione.
- [Scelta consigliata ma facoltativa] Usare un modulo di protezione hardware (HSM) o un archivio chiavi locale per creare una copia locale del materiale della chiave di protezione TDE.
- Interfaccia della riga di comando 2.0 o versione successiva. Per installare la versione più recente e connettersi alla sottoscrizione di Azure, vedere [Installare l'interfaccia della riga di comando di Azure 2.0](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest).
- Creare un insieme di credenziali delle chiavi e una chiave da usare per TDE in Azure Key Vault.
   - [Gestire Key Vault tramite l'interfaccia della riga di comando 2.0](https://docs.microsoft.com/azure/key-vault/key-vault-manage-with-cli2)
   - [Istruzioni per l'uso di un modulo di protezione hardware e Key Vault](https://docs.microsoft.com/azure/key-vault/key-vault-get-started#a-idhsmaif-you-want-to-use-a-hardware-security-module-hsm)
 - L'insieme di credenziali delle chiavi deve avere la proprietà seguente per essere usato per TDE:
   - [Eliminazione temporanea](https://docs.microsoft.com/azure/key-vault/key-vault-ovw-soft-delete)
   - [Come usare l'eliminazione temporanea di Key Vault con l'interfaccia della riga di comando](https://docs.microsoft.com/azure/key-vault/key-vault-soft-delete-cli)
- La chiave deve avere i seguenti attributi per essere usata per TDE:
   - Nessuna data di scadenza
   - Non disabilitata
   - In grado di eseguire operazioni *get*, *wrap key*, *unwrap key*

**Passaggio: Creare un server e assegnare a tale server un'identità Azure AD**

      cli
      # create server (with identity) and database



&nbsp;

&nbsp;

---

<a name="TitleNum_10"/>

### <a name="10-nbsp-about-change-data-capture-sql-servertrack-changesabout-change-data-capture-sql-servermd"></a>10. &nbsp; [Informazioni su Change Data Capture (SQL Server)](track-changes/about-change-data-capture-sql-server.md)

*Aggiornamento: 17/04/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_9))

<!-- Source markdown line 112.  ms.author= "jroth".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 588bff652adefd719e799e9777a416b70184c5f8 77ebdbb1b98b24054d5c5afbb3f1d40e94d1e6bc  (PR=5574  ,  Filename=about-change-data-capture-sql-server.md  ,  Dirpath=docs\relational-databases\track-changes\  ,  MergeCommitSha40=bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68) -->



**Uso di regole di confronto diverse tra database e tabella**


È importante sapere che può accadere che alcune regole di confronto siano diverse tra il database e le colonne di una tabella configurata per Change Data Capture. CDC usa l'archiviazione provvisoria per popolare tabelle laterali. Se una tabella contiene colonne CHAR o VARCHAR con regole di confronto diverse dalle regole di confronto del database e se tali colonne archiviano caratteri non ASCII (ad esempio caratteri DBCS), è possibile che CDC non salvi in modo permanente i dati modificati coerentemente con i dati nelle tabelle di base. Ciò è dovuto al fatto che alle variabili dell'archiviazione provvisoria non possono essere associate regole di confronto.

Considerare uno degli approcci seguenti per verificare che i dati modificati acquisiti siano coerenti con le tabelle di base:

- Usare il tipo di dati NCHAR o NVARCHAR per colonne contenenti dati non ASCII.

- In alternativa, usare le stesse regole di confronto per le colonne e per il database.

Ad esempio, se un database usa le regole di confronto di SQL_Latin1_General_CP1_CI_AS, considerare la tabella seguente:

```
CREATE TABLE T1(
     C1 INT PRIMARY KEY,
     C2 VARCHAR(10) collate Chinese_PRC_CI_AI)
```

CDC potrebbe non acquisire i dati binari per la colonna C2, perché le regole di confronto sono diverse (Chinese_PRC_CI_AI). Per evitare questo problema, usare NVARCHAR:

```
CREATE TABLE T1(
     C1 INT PRIMARY KEY,
     C2 NVARCHAR(10) collate Chinese_PRC_CI_AI --Unicode data type, CDC works well with this data type)
```







## <a name="similar-articles-about-new-or-updated-articles"></a>Articoli simili su articoli nuovi o aggiornati

In questa sezione sono elencati articoli molto simili ad articoli aggiornati di recente in altre aree di interesse all'interno del repository GitHub pubblico di Microsoft: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).



#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Aree di interesse *con* articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (11+6):&nbsp; documentazione di &nbsp;**Advanced Analytics per SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (18+0): &nbsp; documentazione di &nbsp;**Analysis Services per SQL Server**](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (218+14):**documentazione della**connessione a SQL Server](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (14+0):&nbsp; documentazione del &nbsp;**motore di database per SQL Server**](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (3+2): documentazione di &nbsp;&nbsp;**SQL Server Integration Services**](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (3+3):&nbsp; documentazione di &nbsp;**Linux per SQL Server**](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (7+10):&nbsp; documentazione dei &nbsp;**database relazionali per SQL Server**](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornato (0+2):&nbsp; documentazione di &nbsp;**SQL Server Reporting Services**](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (1+3):&nbsp; documentazione di &nbsp;**SQL Operations Studio**](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nuovo + aggiornato (2+3):&nbsp; documentazione di &nbsp;**Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (1+1):&nbsp; documentazione di &nbsp;**SQL Server Data Tools (SSDT)**](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (5+2):&nbsp; documentazione di &nbsp;**SQL Server Management Studio (SSMS)**](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornato (0+2):&nbsp; documentazione di &nbsp;**Transact-SQL**](../t-sql/new-updated-t-sql.md)
- [Nuovo + aggiornato (1+1): documentazione di &nbsp;&nbsp;**Tools per SQL Server**](../tools/new-updated-tools.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Aree di interesse *senza* articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (0+0):**documentazione della**piattaforma di strumenti analitici per SQL Server](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nuovo + aggiornato (0+0): **Data Quality Services for SQL (Data Quality Services per SQL)** Docs](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0+0): **Data Mining Extensions (DMX) for SQL (Estensioni di data mining (DMX) per SQL)** Docs](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0+0): documentazione di **Master Data Services (MDS) per SQL**](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (0+0): **Multidimensional Expressions (MDX) for SQL(Espressioni MDX per SQL)** Docs](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0+0): **ODBC (Open Database Connectivity) for SQL (ODBC (Open Database Connectivity) per SQL)** Docs](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornato (0+0): **PowerShell for SQL (PowerShell per SQL)** Docs](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (0+0): **Samples for SQL (Esempi per SQL)** Docs](../samples/new-updated-samples.md)
- [Nuovo + aggiornato (0+0): **SQL Server Migration Assistant (SSMA)** Docs](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (0+0): **XQuery for SQL (XQuery per SQL)** Docs](../xquery/new-updated-xquery.md)

