---
title: Caricare dati da SQL Server in Azure SQL Data Warehouse (SSIS) | Microsoft Docs
description: In questo articolo viene illustrato come creare un pacchetto di SQL Server Integration Services (SSIS) per spostare dati da una vasta gamma di origini dati in SQL Data Warehouse.
documentationcenter: NA
ms.service: sql-data-warehouse
ms.component: data-movement
ms.devlang: NA
ms.topic: conceptual
ms.tgt_pltfrm: NA
ms.custom: loading
ms.date: 04/04/2018
ms.author: douglasl
author: douglaslMS
manager: craigg-msft
ms.openlocfilehash: 75a352ff4bb1f074a89ad4cc007844261d20c431
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39087583"
---
# <a name="load-data-from-sql-server-to-azure-sql-data-warehouse-with-sql-server-integration-services-ssis"></a>Caricare i dati da SQL Server in Azure SQL Data Warehouse con SQL Server Integration Services (SSIS)

Creare un pacchetto di SQL Server Integration Services (SSIS) per caricare dati da SQL Server in [Azure SQL Data Warehouse](/azure/sql-data-warehouse/index). È anche possibile ristrutturare, trasformare e pulire i dati durante il passaggio attraverso il flusso di dati SSIS.

Questa esercitazione illustrerà come:

* Creare un nuovo progetto di Integration Services in Visual Studio.
* Connettersi a origini dati, inclusi SQL Server (come origine) e SQL Data Warehouse (come destinazione).
* Progettare un pacchetto SSIS che carica i dati dall'origine nella destinazione.
* Eseguire il pacchetto SSIS per caricare i dati.

Questa esercitazione usa SQL Server come origine dati. SQL Server può essere in esecuzione in locale o in una macchina virtuale di Azure.

## <a name="basic-concepts"></a>Concetti fondamentali
In SSIS l'unità di lavoro è un pacchetto. I pacchetti correlati vengono raggruppati in progetti. I progetti e pacchetti di progettazione in Visual Studio vengono creati con SQL Server Data Tools. Il processo di progettazione è un processo visivo in cui l'utente trascina e rilascia i componenti dalla casella degli strumenti all'area di progettazione, li connette e ne imposta le proprietà. Dopo aver completato il pacchetto, è possibile distribuirlo a SQL Server per la gestione completa, il monitoraggio e la sicurezza.

## <a name="options-for-loading-data-with-ssis"></a>Opzioni di caricamento dei dati con SSIS
SQL Server Integration Services (SSIS) è un set di strumenti flessibile che offre un'ampia gamma di opzioni per la connessione e il caricamento dei dati in SQL Data Warehouse.

1. Usare un componente di destinazione ADO NET per connettersi a SQL Data Warehouse. In questa esercitazione viene usato un componente di destinazione ADO NET perché contiene il minor numero di opzioni di configurazione.
2. Usare un componente di destinazione OLE DB per connettersi a SQL Data Warehouse. Questa opzione può offrire prestazioni leggermente migliori rispetto alla destinazione ADO NET.
3. Usare l'attività di caricamento BLOB di Azure per eseguire lo staging dei dati nell'archivio BLOB di Azure. Usare quindi l'attività Esegui SQL di SSIS per avviare uno script Polybase che carica i dati in SQL Data Warehouse. Questa opzione offre le prestazioni migliori tra le tre opzioni elencate di seguito. Per ottenere l'attività di caricamento BLOB di Azure, vedere [Microsoft SQL Server 2016 Integration Services Feature Pack per Azure][Microsoft SQL Server 2016 Integration Services Feature Pack for Azure]. Per altre informazioni su Polybase, vedere [Guida a PolyBase][PolyBase Guide].

## <a name="before-you-start"></a>Prima di iniziare
Per eseguire questa esercitazione, è necessario:

1. **SQL Server Integration Services (SSIS)**. SSIS è un componente di SQL Server e richiede una versione di valutazione o una versione con licenza di SQL Server. Per ottenere una versione di valutazione di SQL Server 2016 Preview, vedere [SQL Server Valutazioni][SQL Server Evaluations].
2. **Visual Studio**. Per ottenere l'edizione gratuita di Visual Studio Community, vedere [Visual Studio Community][Visual Studio Community].
3. **SQL Server Data Tools per Visual Studio (SSDT)**. Per ottenere SQL Server Data Tools per Visual Studio, vedere [Scaricare SQL Server Data Tools (SSDT)][Download SQL Server Data Tools (SSDT)].
4. **Dati di esempio**. Questa esercitazione usa i dati di esempio archiviati in SQL Server nel database di esempio AdventureWorks come dati di origine da caricare in SQL Data Warehouse. Per ottenere il database di esempio AdventureWorks, vedere la pagina dei [database di esempio AdventureWorks 2014][AdventureWorks 2014 Sample Databases].
5. **Un database SQL Data Warehouse e le autorizzazioni**. In questa esercitazione ci si connette a un'istanza di SQL Data Warehouse e si caricano i dati. È necessario avere le autorizzazioni per creare una tabella e caricare i dati.
6. **Una regola del firewall**. È necessario creare una regola del firewall in SQL Data Warehouse con l'indirizzo IP del computer locale prima di poter caricare dati in SQL Data Warehouse.

## <a name="step-1-create-a-new-integration-services-project"></a>Passaggio 1: Creare un nuovo progetto di Integration Services
1. Avviare Visual Studio.
2. Scegliere **Nuovo progetto** dal menu **File**.
3. Andare ai tipi di progetto **Installati | Progetti | Business Intelligence | Integration Services**.
4. Selezionare **Progetto di Integration Services**. Specificare i valori per **Nome** e **Percorso** e quindi selezionare **OK**.

Viene aperto Visual Studio e viene creato un nuovo progetto di Integration Services (SSIS). Visual Studio apre quindi la finestra di progettazione per il singolo nuovo pacchetto SSIS (package.dtsx) nel progetto. Vengono visualizzate le aree della schermata seguenti:

* A sinistra, la **Casella degli strumenti** dei componenti SSIS.
* Al centro, l'area di progettazione con più schede. In genere si usano almeno le schede **Flusso di controllo** e il **Flusso di dati**.
* A destra, i riquadri **Esplora soluzioni** e **Proprietà**.
  
    ![][01]

## <a name="step-2-create-the-basic-data-flow"></a>Passaggio 2: Creare il flusso di dati di base
1. Trascinare un'attività Flusso di dati dalla casella degli strumenti al centro dell'area di progettazione (nella scheda **Flusso di controllo**).
   
    ![][02]
2. Fare doppio clic sull'attività Flusso di dati per passare alla scheda Flusso di dati.
3. Dall'elenco Altre origini nella casella degli strumenti trascinare un'origine ADO.NET nell'area di progettazione. Con l'adattatore di origine ancora selezionato, modificare il nome su **Origine SQL Server** nel riquadro **Proprietà**.
4. Dall'elenco Altre destinazioni nella casella degli strumenti,trascinare una destinazione ADO.NET all'area di progettazione sotto l'origine ADO.NET. Con l'adattatore di destinazione ancora selezionato, modificare il nome su **Destinazione SQL DW**  nel riquadro **Proprietà**.
   
    ![][09]

## <a name="step-3-configure-the-source-adapter"></a>Passaggio 3: Configurare l'adattatore di origine
1. Fare doppio clic sull'adattatore di origine per aprire l'**Editor origine ADO.NET**.
   
    ![][03]
2. Nella scheda **Gestione connessione** della finestra **Editor origine ADO.NET** fare clic sul pulsante **Nuovo** accanto all'elenco **Gestione connessione ADO.NET** per aprire la finestra di dialogo **Configura gestione connessione ADO.NET** e creare le impostazioni di connessione per il database di SQL Server da cui questa esercitazione carica i dati.
   
    ![][04]
3. Nella finestra di dialogo **Configura gestione connessione ADO.NET** fare clic sul pulsante **Nuovo** per aprire la finestra di dialogo **Gestione connessione** e creare una nuova connessione dati.
   
    ![][05]
4. Nella finestra di dialogo **Gestione connessione** eseguire le operazioni seguenti.
   
   1. Per **Provider** selezionare il provider di dati SqlClient.
   2. Per **Nome server** immettere il nome di SQL Server.
   3. Nella sezione **Accesso al server** selezionare o immettere le informazioni di autenticazione.
   4. Nella sezione **Connessione a un database** selezionare il database di esempio AdventureWorks.
   5. Fare clic su **Test connessione**.
      
       ![][06]
   6. Nella finestra di dialogo che indica i risultati del test di connessione fare clic su **OK** per tornare alla finestra di dialogo **Gestione connessione**.
   7. Nella finestra di dialogo **Gestione connessione** fare clic su **OK** per ritornare alla finestra di dialogo **Configura gestione connessione ADO.NET**.
5. Nella finestra di dialogo **Configura gestione connessione ADO.NET** fare clic su **OK** per ritornare all'**Editor origine ADO.NET**.
6. Nell'**Editor origine ADO.NET** selezionare la tabella **Sales.SalesOrderDetail** nell'elenco **Nome tabella o vista**.
   
    ![][07]
7. Fare clic su **Anteprima** per visualizzare le prime 200 righe di dati nella tabella di origine nella finestra di dialogo **Anteprima risultati query**.
   
    ![][08]
8. Nella finestra di dialogo **Anteprima risultati query** fare clic su **Chiudi** per ritornare all'**Editor origine ADO.NET**.
9. Nell'**Editor origine ADO.NET** fare clic su **OK** per completare la configurazione dell'origine dati.

## <a name="step-4-connect-the-source-adapter-to-the-destination-adapter"></a>Passaggio 4: Connettere l'adattatore di origine all'adattatore di destinazione
1. Selezionare l'adattatore di origine nell'area di progettazione.
2. Selezionare la freccia blu che si estende dall'adattatore di origine e trascinarla nell'editor di destinazione fino al completo inserimento.
   
    ![][10]
   
    In un pacchetto SSIS tipico è possibile usare diversi altri componenti dalla casella degli strumenti SSIS tra l'origine e la destinazione per ristrutturare, trasformare e pulire i dati mentre attraversano il flusso di dati SSIS. Per mantenere più semplice possibile questo esempio, viene eseguita la connessione dell'origine direttamente alla destinazione.

## <a name="step-5-configure-the-destination-adapter"></a>Passaggio 5: Configurare l'adattatore di destinazione
1. Fare doppio clic sull'adattatore di destinazione per aprire l'**Editor destinazione ADO.NET**.
   
    ![][11]
2. Nella scheda **Gestione connessione** della finestra **Editor destinazione ADO.NET** fare clic sul pulsante **Nuovo** accanto all'elenco **Gestione connessione** per aprire la finestra di dialogo **Configura gestione connessione ADO.NET** e creare le impostazioni di connessione per il database di Azure SQL Data Warehouse da cui questa esercitazione carica i dati.
3. Nella finestra di dialogo **Configura gestione connessione ADO.NET** fare clic sul pulsante **Nuovo** per aprire la finestra di dialogo **Gestione connessione** e creare una nuova connessione dati.
4. Nella finestra di dialogo **Gestione connessione** eseguire le operazioni seguenti.
   1. Per **Provider** selezionare il provider di dati SqlClient.
   2. Per **Nome server** immettere il nome di SQL Data Warehouse.
   3. Nella sezione **Accesso al server** selezionare **Usa autenticazione di SQL Server** e immettere le informazioni di autenticazione.
   4. Nella sezione **Connessione a un database** selezionare un database di SQL Data Warehouse esistente.
   5. Fare clic su **Test connessione**.
   6. Nella finestra di dialogo che indica i risultati del test di connessione fare clic su **OK** per tornare alla finestra di dialogo **Gestione connessione**.
   7. Nella finestra di dialogo **Gestione connessione** fare clic su **OK** per ritornare alla finestra di dialogo **Configura gestione connessione ADO.NET**.
5. Nella finestra di dialogo **Configura gestione connessione ADO.NET** fare clic su **OK** per ritornare all'**Editor destinazione ADO.NET**.
6. Nell'**Editor destinazione ADO.NET** fare clic su **Nuovo** accanto all'elenco **Tabella o vista** per visualizzare la finestra di dialogo **Crea tabella** per creare una nuova tabella di destinazione con un elenco di colonne che corrisponde alla tabella di origine.
   
    ![][12a]
7. Nella finestra di dialogo **Crea tabella** eseguire le operazioni seguenti.
   
   1. Modificare il nome della tabella di destinazione su **SalesOrderDetail**.
   2. Rimuovere la colonna **rowguid**. Il tipo di dati **uniqueidentifier** non è supportato in SQL Data Warehouse.
   3. Modificare il tipo di dati della colonna **LineTotal** su **money**. Il tipo di dati **decimal** non è supportato in SQL Data Warehouse. Per informazioni sui tipi di dati supportati, vedere [CREATE TABLE (Azure SQL Data Warehouse, Parallel Data Warehouse)][CREATE TABLE (Azure SQL Data Warehouse, Parallel Data Warehouse)].
      
       ![][12b]
   4. Fare clic su **OK** per creare la tabella e ritornare all'**Editor destinazione ADO.NET**.
8. Nell'**Editor destinazione ADO.NET** selezionare la scheda **Mapping** per visualizzare come le colonne nell'origine vengono mappate alle colonne nella destinazione.
   
    ![][13]
9. Fare clic su **OK** per completare la configurazione dell'origine dati.

## <a name="step-6-run-the-package-to-load-the-data"></a>Passaggio 6: Eseguire il pacchetto per caricare i dati
Eseguire il pacchetto facendo clic sul pulsante **Avvia** della barra degli strumenti o selezionando una delle opzioni **Esegui** nel menu **Debug**.

Quando inizia l'esecuzione del pacchetto si possono osservare delle ruote gialle in rotazione che indicano l'attività e il numero di righe elaborate fino a ora.

![][14]

Quando l'esecuzione del pacchetto è terminata vengono visualizzati dei segni di spunta verdi che indicano l'esito positivo e il numero totale di righe di dati caricati dall'origine alla destinazione.

![][15]

Congratulazioni! Hai usato correttamente SQL Server Integration Services per caricare dati in Azure SQL Data Warehouse.

## <a name="next-steps"></a>Passaggi successivi
* Altre informazioni sul flusso di dati SSIS. Iniziare da qui: [Flusso di dati][Data Flow].
* Informazioni su come eseguire il debug e risolvere i problemi relativi ai pacchetti direttamente nell'ambiente di progettazione. Iniziare da qui: [Strumenti per la risoluzione dei problemi relativi allo sviluppo dei pacchetti][Troubleshooting Tools for Package Development].
* Informazioni su come distribuire i progetti SSIS e i pacchetti nel server Integration Services o in un'altra posizione di archiviazione. Iniziare da qui: [Distribuire progetti e pacchetti][Deployment of Projects and Packages].

<!-- Image references -->
[01]:  ./media/load-data-to-sql-data-warehouse/ssis-designer-01.png
[02]:  ./media/load-data-to-sql-data-warehouse/ssis-data-flow-task-02.png
[03]:  ./media/load-data-to-sql-data-warehouse/ado-net-source-03.png
[04]:  ./media/load-data-to-sql-data-warehouse/ado-net-connection-manager-04.png
[05]:  ./media/load-data-to-sql-data-warehouse/ado-net-connection-05.png
[06]:  ./media/load-data-to-sql-data-warehouse/test-connection-06.png
[07]:  ./media/load-data-to-sql-data-warehouse/ado-net-source-07.png
[08]:  ./media/load-data-to-sql-data-warehouse/preview-data-08.png
[09]:  ./media/load-data-to-sql-data-warehouse/source-destination-09.png
[10]:  ./media/load-data-to-sql-data-warehouse/connect-source-destination-10.png
[11]:  ./media/load-data-to-sql-data-warehouse/ado-net-destination-11.png
[12a]: ./media/load-data-to-sql-data-warehouse/destination-query-before-12a.png
[12b]: ./media/load-data-to-sql-data-warehouse/destination-query-after-12b.png
[13]:  ./media/load-data-to-sql-data-warehouse/column-mapping-13.png
[14]:  ./media/load-data-to-sql-data-warehouse/package-running-14.png
[15]:  ./media/load-data-to-sql-data-warehouse/package-success-15.png

<!-- Article references -->

<!-- MSDN references -->
[PolyBase Guide]: ../relational-databases/polybase/polybase-guide.md
[Download SQL Server Data Tools (SSDT)]: ../ssdt/download-sql-server-data-tools-ssdt.md
[CREATE TABLE (Azure SQL Data Warehouse, Parallel Data Warehouse)]: ../t-sql/statements/create-table-azure-sql-data-warehouse.md
[Data Flow]: ./data-flow/data-flow.md
[Troubleshooting Tools for Package Development]: ./troubleshooting/troubleshooting-tools-for-package-development.md
[Deployment of Projects and Packages]: ./packages/deploy-integration-services-ssis-projects-and-packages.md

<!--Other Web references-->
[Microsoft SQL Server 2016 Integration Services Feature Pack for Azure]: http://go.microsoft.com/fwlink/?LinkID=626967
[SQL Server Evaluations]: https://www.microsoft.com/evalcenter/evaluate-sql-server-2016
[Visual Studio Community]: https://www.visualstudio.com/products/visual-studio-community-vs.aspx
[AdventureWorks 2014 Sample Databases]: https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks
