---
title: Caricamento con Integration Services - Data Warehouse parallelo | Documenti Microsoft
description: Fornisce informazioni di riferimento e la distribuzione per il caricamento dei dati in Parallel Data Warehouse (PDW) utilizzando i pacchetti di SQL Server Integration Services (SSIS).
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: efc077bda6d05642107a6e8694d53418401ff12c
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="load-data-with-integration-services-to-parallel-data-warehouse"></a>Caricare i dati con Integration Services a Parallel Data Warehouse
Fornisce informazioni di riferimento e di distribuzione per il caricamento dei dati in SQL Server Parallel Data Warehouse utilizzando i pacchetti di SQL Server Integration Services (SSIS).  
  
<!-- MISSING LINKS

## <a name="BeforeBegin"></a>Before You Begin  
Before you can start loading data, use the following topics to install the Integration Services Destination Adapters and to create an Integration Services package that connects SQL Server PDW:  


-   [Install Integration Services destination adapters](install-integration-services-destination-adapters.md)  
  
-   [Connect With Integration Services for loading](connect-with-ssis-for-loading.md)  
  
For general information about developing Integration Services packages, see [Designing and Implementing Packages (Integration Services)](http://msdn.microsoft.com/library/ms141091&#40;v=sql11&#40;.aspx) on MSDN.  

-->
  
## <a name="Basics"></a>Nozioni di base  
Integration Services è il componente di SQL Server per ad alte prestazioni estrazione, trasformazione e caricamento (ETL) di dati e viene comunemente utilizzato per popolare e aggiornare un data warehouse.  
  
L'adattatore di destinazione PDW è un componente di Integration Services che consente di caricare dati in PDW utilizzando pacchetti dtsx di Integration Services. In un pacchetto del flusso di lavoro per ServerPDW SQL, è possibile caricare e unire dati da più origini e caricare i dati a più destinazioni. I caricamenti avvengono in parallelo, sia all'interno di un pacchetto sia tra più pacchetti in esecuzione contemporaneamente, fino a un massimo di 10 caricamenti paralleli sullo stesso strumento.  
  
Oltre alle attività descritte in questo argomento, è possibile utilizzare altre funzionalità di Integration Services per filtrare, trasformare, analizzare e pulire i dati prima di caricarli nel data warehouse. È inoltre possibile migliorare il flusso di lavoro del pacchetto eseguendo istruzioni SQL e pacchetti figlio o inviando messaggi di posta elettronica.  
  
Per una documentazione completa di Integration Services, vedere [SQL Server Integration Services](http://msdn.microsoft.com/library/ms141026(v=sql11).aspx).  
  
## <a name="HowToDeployPackage"></a>Metodi per l'esecuzione di un pacchetto di Integration Services  
Utilizzare uno di questi metodi per eseguire un pacchetto di Integration Services.  
  
### <a name="run-from-sql-server-2008-r2-business-intelligence-development-studio-bids"></a>Eseguire da SQL Server 2008 R2 Business Intelligence Development Studio (BIDS)  
Per eseguire il pacchetto dall'interno BIDS, fare doppio clic sul pacchetto e scegliere **Esegui pacchetto**.  
  
Per impostazione predefinita, le offerte esegue i pacchetti utilizzando i file binari a 64 bit. Ciò è dovuto il **Run64BitRuntime** proprietà del pacchetto. Per impostare questa proprietà, passare a **Esplora**, pulsante destro del mouse sul progetto e scegliere **proprietà**. Nel **pagine delle proprietà di Integration Services**, passare a **le proprietà di configurazione** e selezionare **debug**. Verrà visualizzato il **Run64BitRuntime** proprietà sotto il **opzioni di Debug**. Per l'utilizzo di runtime a 32 bit, impostare questa proprietà su **False**. Per utilizzare il runtime a 64 bit, impostare questa proprietà su **True**.  
  
### <a name="run-from-sql-server-2012-sql-server-data-tools"></a>Eseguire da SQL Server 2012 SQL Server Data Tools  
Per eseguire il pacchetto dall'interno di SQL Server Data Tools, fare doppio clic sul pacchetto e scegliere **Esegui pacchetto**.  
  
### <a name="run-from-powershell"></a>Esecuzione di PowerShell  
Per eseguire il pacchetto di Windows PowerShell, usando il **dtexec** utilità: `dtexec /FILE <packagePath>`  
  
Ad esempio, `dtexec /FILE "C:\Users\User1\Desktop\Package.dtsx"`  
  
### <a name="run-from-a-windows-command-prompt"></a>Eseguire Windows da un prompt dei comandi 
Per eseguire il pacchetto da un prompt dei comandi di Windows, utilizzando il **dtexec** utilità: `dtexec /FILE <packagePath>`  
  
Esempio: `dtexec /FILE "C:\Users\User1\Desktop\Package.dtsx"`  
  
## <a name="DataTypes"></a>Tipi di dati  
Quando si utilizza servizi di integrazione per caricare dati da un'origine dati a un database di SQL Server PDW, i dati viene prima eseguito il mapping dall'origine dei dati ai tipi di dati di Integration Services. In questo modo è possibile eseguire il mapping dei dati di più origini a un set comune di tipi di dati.  
  
Quindi i mapping dei dati da servizi di integrazione di tipi di dati di SQL Server PDW. Per ogni tipo di dati di SQL Server PDW, nella tabella seguente sono elencati i tipi di dati di Integration Services che possono essere convertiti nel tipo di dati di SQL Server PDW.  
  
|Tipo di dati PDW|Integration Services tipi di dati (s) che eseguono il mapping al tipo di dati PDW|  
|---------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|  
|BIT|DT_BOOL|  
|bigint|DT_I1, DT_I2, DT_I4, DT_I8, DT_UI1, DT_UI2, DT_UI4|  
|CHAR|DT_STR|  
|DATE|DT_DBDATE|  
|DATETIME|DT_DATE, DT_DBDATE, DT_DBTIMESTAMP, DT_DBTIMESTAMP2|  
|DATETIME2|DT_DATE, DT_DBDATE, DT_DBTIMESTAMP, DT_DBTIMESTAMP2|  
|DATETIMEOFFSET|DT_WSTR|  
|DECIMAL|DT_DECIMAL, DT_I1, DT_I2, DT_I4, DT_I4, DT_I8, DT_NUMERIC, DT_UI1, DT_UI2, DT_UI4, DT_UI8|  
|FLOAT|DT_R4, DT_R8|  
|INT|DT_I1, DTI2, DT_I4, DT_UI1, DT_UI2|  
|MONEY|DT_CY|  
|NCHAR|DT_WSTR|  
|NUMERIC|DT_DECIMAL, DT_I1, DT_I2, DT_I4, DT_I8, DT_NUMERIC, DT_UI1, DT_UI2, DT_UI4, DT_UI8|  
|NVARCHAR|DT_WSTR, DT_STR|  
|REAL|DT_R4|  
|SMALLDATETIME|DT_DBTIMESTAMP2|  
|SMALLINT|DT_I1, DT_I2, DT_UI1|  
|SMALLMONEY|DT_R4|  
|TIME|DT_WSTR|  
|TINYINT|DT_I1|  
|VARBINARY|DT_BYTES|  
|VARCHAR|DT_STR|  
  
**Supporto limitato per la precisione del tipo di dati**  
  
PDW genera un errore di convalida se si esegue il mapping di una colonna di input DT_NUMERIC o DT_DECIMAL contenente un valore con precisione maggiore di 28.  
  
**Tipi di dati non supportato**  
  
SQL Server PDW non supporta i seguenti tipi di dati di Integration Services:  
  
-   DT_DBTIMESTAMPOFFSET  
  
-   DT_DBTIME2  
  
-   DT_GUID  
  
-   DT_IMAGE  
  
-   DT_NTEXT  
  
-   DT_TEXT  
  
Per caricare le colonne contenenti questi tipi di dati in SQL Server PDW, è necessario aggiungere una trasformazione conversione dati a monte nel flusso di dati per convertire i dati in un tipo di dati compatibile.  
  
## <a name="permissions"></a>Autorizzazioni  
Per eseguire un pacchetto di caricamento di Integration Services, è necessario:  
  
-   CARICARE l'autorizzazione per il database.  
  
-   Applicabile INSERT, UPDATE, le autorizzazioni di eliminazione nella tabella di destinazione.  
  
-   Se viene utilizzato un database di gestione temporanea, l'autorizzazione per creare il database di gestione temporanea. Questo vale per la creazione di una tabella temporanea.  
  
-   Se non viene utilizzato alcun database di gestione temporanea, l'autorizzazione per creare il database di destinazione. Questo vale per la creazione di una tabella temporanea.  
  
## <a name="GenRemarks"></a>Osservazioni generali  
Quando un pacchetto di Integration Services ha più destinazioni di SQL Server PDW in esecuzione e una delle connessioni viene terminata, Integration Services interrompe il push dei dati per tutte le destinazioni di SQL Server PDW.  
  
## <a name="Limits"></a>Limitazioni e restrizioni  
Per un pacchetto di Integration Services, il numero delle destinazioni di SQL Server PDW per la stessa origine dati è limitato dal numero massimo di caricamenti attivi. Il numero massimo è preconfigurato e non è configurabile dall'utente. 

<!-- MISSING LINKS
For the maximum number of loads and queued loads per appliance, see [Minimum and maximum values](minimum-and-maximum-values.md).  
-->
  
Ogni destinazione del pacchetto di Integration Services per la stessa origine dati viene conteggiato come un carico durante l'esecuzione del pacchetto. Si supponga ad esempio che il numero massimo di caricamenti attivi sia 10. Il pacchetto non viene eseguito se tenta di aprire 11 o più destinazioni per la stessa origine dati.  
  
È possibile eseguire contemporaneamente più pacchetti purché ogni pacchetto non utilizzi un numero di caricamenti attivi superiore al limite massimo consentito. Ad esempio, se il numero massimo di caricamenti attivi è 10, è possibile eseguire contemporaneamente due pacchetti che utilizzino entrambi 10 destinazioni. Mentre un pacchetto viene eseguito, l'altro rimane in attesa nella coda di caricamento.  
  
Se il numero di caricamenti in coda supera il numero massimo consentito di caricamenti in coda, il pacchetto non verrà eseguito. Ad esempio, se il numero massimo di caricamenti è 10 per strumento e il numero massimo di caricamenti in coda è 40 per strumento, è possibile eseguire contemporaneamente cinque pacchetti di Integration Services che 10 destinazioni aperte ciascuno. L'eventuale tentativo di eseguire un sesto pacchetto avrà esito negativo.  

> [!IMPORTANT]
> Utilizza un'origine dati OLE DB in SSIS con l'adattatore di destinazione PDW, può causare il danneggiamento dei dati se la tabella di origine contiene le colonne char e varchar con regole di confronto SQL. È consigliabile utilizzare un'origine ADO.NET se la tabella di origine contiene le colonne char o varchar con regole di confronto SQL. 

  
## <a name="Locks"></a>Comportamento di blocco  
Quando si caricano dati con Integration Services, SQL ServerPDW Usa i blocchi a livello di riga per aggiornare i dati nella tabella di destinazione. Ciò significa che durante l'aggiornamento ogni riga viene bloccata per la lettura e la scrittura. Le righe della tabella di destinazione non sono bloccate mentre i dati vengono caricati nella tabella di staging.  
  
## <a name="Examples"></a>Esempi  
  
### <a name="Walkthrough"></a>A. Caricamento semplice file flat  
La procedura dettagliata seguente viene illustrato un carico di dati semplice utilizzo di Integration Services per caricare i dati di file flat in un'applicazione di SQL Server PDW.  Questo esempio si presuppone che i servizi di integrazione è stato installato nel computer client e la destinazione di SQL Server PDW è stata installata, come descritto in precedenza.  
  
In questo esempio si caricherà nel `Orders` tabella, che è il seguente codice DDL. Il `Orders` tabella è inclusa la `LoadExampleDB` database.  
  
```sql  
CREATE TABLE LoadExampleDB.dbo.Orders (  
   id INT,  
   city varchar(25),  
   lastUpdateDate DATE,  
   orderDate DATE)  
;  
```  
  
Ecco i dati del carico:  
  
```  
id        city           lastUpdateDate     orderdate  
--------- -------------- ------------------ ----------  
1         Seattle        2010-05-01         2010-01-01  
2         Denver         2002-06-25         1999-01-02  
```  
  
In preparazione per il caricamento, creare il file flat `exampleLoad.txt`, che contiene i dati di carico:  
  
```  
id,city,lastUpdateDate,orderDate  
1,Seattle,2010-05-01,2010-01-01  
2,Denver,2002-06-25,1999-01-02  
```  
  
Innanzitutto, creare un pacchetto di Integration Services eseguendo questi passaggi:  
  
1.  In SQL Server Data Tools \(SSDT\)selezionare **File**, **New**e quindi **progetto**. Selezionare **progetto di Integration Services** tra le opzioni elencate. Nome di questo progetto `ExampleLoad`, fare clic su **OK**.  
  
2.  Fare clic su di **flusso di controllo** scheda e quindi trascinare il **attività flusso di dati** dal **della casella degli strumenti** per il **flusso di controllo** riquadro.  
  
3.  Fare clic su di **del flusso di dati** scheda e quindi trascinare **origine File Flat** dal **della casella degli strumenti** per il **del flusso di dati** riquadro. Doppio clic sulla casella appena creata per aprire la **Editor origine File Flat**.  
  
4.  Fare clic su **Connection Manager** e quindi fare clic su **New**.  
  
5.  Nel **nome gestione connessione** , immettere un nome descrittivo per la connessione. Per questo esempio, `Example Load Flat File CM`.  
  
6.  Fare clic su **Sfoglia** e selezionare il `ExampleLoad.txt` file dal computer locale.  
  
7.  Poiché il file flat contiene una riga con i nomi di colonna, fare clic su di **nomi di colonna nella prima riga di dati** casella.  
  
8.  Fare clic su **colonne** nella colonna a sinistra e anteprima i dati che verranno caricati per assicurarsi che i nomi delle colonne e dati sono stati interpretati correttamente.  
  
9. Fare clic su **avanzate** nella colonna sinistra. Fare clic su ogni nome di colonna per esaminare il tipo di dati che è stato associato ai dati. Digitare modifiche nella casella in modo che i tipi di dati dei dati caricati sono compatibili con i tipi di colonna di destinazione.  
  
10. Fare clic su **OK** per salvare la gestione connessione.  
  
11. Fare clic su **OK** per uscire dall'installazione di **Editor origine File Flat**.  
  
Specificare la destinazione del flusso di dati.  
  
1.  Trascinare il **destinazione SQL Server PDW** dal **della casella degli strumenti** per il **del flusso di dati** riquadro.  
  
2.  Doppio clic sulla casella appena creata per caricare il **Editor destinazione di SQL Server PDW**.  
  
3.  Fare clic sulla freccia rivolta verso il basso accanto a **Connection Manager**.  
  
4.  Selezionare **creare una nuova connessione**.  
  
5.  Inserire le informazioni per il database del server, utente, password e la destinazione con informazioni specifiche per il dispositivo. (Esempi sono mostrati sotto). Fare clic su **OK**.  
  
    Per le connessioni InfiniBand, **nome Server**: immettere < nome dispositivo >-SQLCTL01, 17001.  
  
    Per le connessioni Ethernet, **nome Server**: immettere l'indirizzo IP del cluster di nodi di controllo, la virgola, porta 17001. Ad esempio, 10.192.63.134,17001.  
  
    **Utente:**`user1`  
  
    **Password:**`password1`  
  
    **Database di destinazione:**`LoadExampleDB`  
  
6.  Selezionare la tabella di destinazione: `Orders`.  
  
7.  Selezionare **Append** come modalità di caricamento e fare clic su **OK**.  
  
Specificare il flusso di dati dall'origine alla destinazione.  
  
1.  Nel **del flusso di dati** riquadro, trascinare la freccia verde dal **origine File Flat** casella per il **destinazione SQL Server PDW** casella.  
  
2.  Fare doppio clic su di **destinazione SQL Server PDW** casella che consente di visualizzare il **Editor destinazione di SQL Server PDW** nuovamente. Verranno visualizzati i nomi delle colonne del file flat a sinistra, in **colonne Input senza mapping**. Verranno visualizzati i nomi delle colonne dalla tabella di destinazione a destra, in **colonne di destinazione senza mapping**. Il mapping delle colonne trascinando o facendo doppio clic su nomi di colonna corrispondente nel **colonne Input senza mapping** e **colonne di destinazione senza mapping** elencati per il **colonne con mapping**casella. Fare clic su **OK** per salvare le impostazioni.  
  
3.  Salvare il pacchetto, fare clic su **salvare** nel **File** menu.  
  
Eseguire il pacchetto nel computer in uso di Integration Services.  
  
1.  In Integration Services**Esplora** (a destra), fare doppio clic su `Package.dtsx` e selezionare **Execute**.  
  
2.  Il pacchetto verrà eseguito e verranno visualizzati lo stato di avanzamento e gli eventuali errori nel **lo stato di avanzamento** riquadro. Utilizzare un client SQL per confermare o monitorare il carico mediante la Console di amministrazione di SQL Server PDW.  
  
## <a name="see-also"></a>Vedere anche  
[Creare un'attività script che utilizza l'adapter di destinazione SSIS PDW](create-ssis-script-task-using-pdw-destination-adapter.md)  
[SQL Server Integration Services](http://msdn.microsoft.com/library/ms141026&#40;v=sql11&#40;.aspx)  
[Progettazione e implementazione di pacchetti (Integration Services)](http://msdn.microsoft.com/library/ms141091&#40;v=sql11&#40;.aspx)  
[Esercitazione: Creazione di un pacchetto di base tramite una procedura guidata](http://technet.microsoft.com/library/ms365330&#40;v=sql11&#40;.aspx)  
[Introduzione (Integration Services)](http://go.microsoft.com/fwlink/?LinkId=202412)  
[Esempio di generazione di pacchetti dinamiche](http://go.microsoft.com/fwlink/?LinkId=202413)  
[Progettazione di pacchetti SSIS per parallelismo (Video di SQL Server)](http://msdn.microsoft.com/library/dd795221.aspx)  
[Negli esempi della Community di Microsoft SQL Server: Integration Services](http://go.microsoft.com/fwlink/?LinkId=202415)  
[Miglioramento dei caricamenti incrementali tra Change Data Capture](http://msdn.microsoft.com/library/bb895315&#40;v=sql11&#40;.aspx)  
[Trasformazione Dimensione a modifica lenta](http://msdn.microsoft.com/library/ms141715&#40;v=sql11&#40;.aspx)  
[Attività Inserimento bulk](http://msdn.microsoft.com/library/ms141239&#40;v=sql11&#40;.aspx)  
  
<!-- MISSING LINKS
[Grant permissions to load data](grant-permissions-to-load-data.md)  
[Common metadata query examples](metadata-query-examples.md)
-->
