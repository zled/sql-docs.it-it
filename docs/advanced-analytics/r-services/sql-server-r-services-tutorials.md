---
title: "Esercitazioni di SQL Server R Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: 5ccc75f6-6703-47d9-b879-9a740569b45e
caps.latest.revision: 31
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 27
---
# Esercitazioni di SQL Server R Services
Usare queste esercitazioni per ottenere informazioni su [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] e gli scenari di analisi scientifica dei dati supportati, tra cui:

+ Sviluppo di modelli in R e distribuzione in SQL Server
+ Rendere operativo il codice R distribuendo una soluzione sviluppata da un analista dei dati in un server o in un altro ambiente di produzione.
+ Spostamento di dati tra R e SQL Server
+ Come usare contesti di calcolo remoti e locali
  

## <a name="a-namebkmkend-to-endadeveloping-an-end-to-end-advanced-analytics-solution"></a><a name="bkmk_end-to-end"></a>Sviluppare una soluzione di analisi avanzata end-to-end  

[Procedura dettagliata end-to-end per l'analisi scientifica dei dati](../../advanced-analytics/r-services/data-science-end-to-end-walkthrough.md) 

Provare a usare il processo di analisi scientifica dei dati end-to-end, dall'acquisizione e l'analisi dei dati all'assegnazione dei punteggi. Imparare a usare i dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e a rendere operativo il modello salvandolo in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
Si importerà il set di dati dei taxi di New York City in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con PowerShell e si esploreranno i dati con R. 

Si creerà quindi un modello predittivo e si distribuirà il modello R in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per l'assegnazione dei punteggi in modalità batch e a stima singola. 

  
Questa esercitazione è destinata agli utenti che hanno familiarità con R e con strumenti di sviluppo come PowerShell e SQL Server Management Studio. È necessario avere accesso a un ambiente di sviluppo R e avere familiarità con i comandi R. 
  
## <a name="a-namebkmkdatascienceadata-science-deep-dive"></a><a name="bkmk_dataScience"></a>Procedura approfondita per l'analisi scientifica dei dati  

[Introduzione a RevoScaleR e SQL Server](http://go.microsoft.com/fwlink/?LinkID=691640&clcid=0x809)  

Questa procedura dettagliata è un buon punto di partenza per analisti dei dati o sviluppatori che conoscono il linguaggio R e necessitano di informazioni sui pacchetti e le funzioni R avanzati di Microsoft R di Revolution Analytics. 

Verrà illustrato come usare le funzioni nei pacchetti ScaleR per spostare dati tra R e SQL e per scambiare i contesti di calcolo per adattarli a un'attività specifica. Si creeranno alcuni modelli e tracciati che verranno quindi spostati tra l'ambiente di sviluppo e SQL Server.  
  
Questa esercitazione è destinata agli utenti che usano R e desiderano altre informazioni su come RevoScaleR e SQL Server possono migliorare l'uso di R.

## <a name="in-database-advanced-analytics-for-the-sql-developer"></a>Analisi avanzata nel database per sviluppatori SQL  
  
[Analisi avanzata nel database per sviluppatori SQL &#40;Esercitazione&#41;](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)

Creare e distribuire una soluzione di analisi avanzata completa usando [!INCLUDE[tsql](../../includes/tsql-md.md)]. Questo esempio illustra l'integrazione tra il linguaggio R open source e il motore di database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si apprenderà come eseguire il wrapping del codice R in una stored procedure, come salvare un modello R in un database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e come effettuare chiamate con parametri al modello R per la creazione di stime. 
  
Questa esercitazione è destinata agli sviluppatori SQL, agli sviluppatori di applicazioni o agli amministratori di database SQL che offriranno assistenza per soluzioni R e desiderano informazioni sulla distribuzione dei modelli R in SQL Server.  Non è necessario alcun ambiente R; tutto il codice R viene fornito ed è possibile creare la soluzione completa usando solo [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] e strumenti di business intelligence e di sviluppo SQL già noti.   

## <a name="use-r-services-in-an-application"></a>Usare R Services in un'applicazione

[Build an intelligent app with SQL Server and R](https://www.microsoft.com/sql-server/developer-get-started/r) (Creare un'app intelligente con SQL Server e R)

Questa esercitazione illustra come una società di noleggio di sci potrebbe usare l'apprendimento automatico per prevedere i noleggi futuri, in modo da aiutare il piano aziendale e il personale a soddisfare la domanda futura.


## <a name="using-r-code-in-t-sql"></a>Usare il codice R in T-SQL  

[Usare il codice R in Transact-SQL &#40;SQL Server R Services&#41;](../../advanced-analytics/r-services/using-r-code-in-transact-sql-sql-server-r-services.md)  

Si tratta di una serie di singoli esempi molto brevi che descrivono la sintassi di base per usare R in [!INCLUDE[tsql](../../includes/tsql-md.md)]. 

Verrà illustrato come chiamare il runtime R da SQL, verranno delineate le differenze principali nei tipi di dati tra R e SQL, verrà eseguito il wrapping di funzioni R nel codice SQL e verrà eseguita una stored procedure che salva l'output R in una tabella SQL.
  
Questa esercitazione è destinata a coloro che non hanno mai usato R Services e desiderano informazioni di base su come chiamare R usando T-SQL. Non è necessario aver usato R in precedenza; è tuttavia necessario saper usare SQL Server Management Studio o altri strumenti che possono connettersi a un database e saper eseguire query T-SQL semplici.

  
## <a name="a-namebkmkprerequisitesaprerequisites"></a><a name="bkmk_Prerequisites"></a>Prerequisiti
  
Per eseguire una di queste esercitazioni, è necessario scaricare e installare **R Services (in-Database)** come descritto in [Configurare SQL Server R Services](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)

Dopo l'installazione di SQL Server, non dimenticare di eseguire i passaggi seguenti:
+ Abilitare R Services eseguendo *sp_configure*
+ Riavviare il server
+ Assicurarsi che il servizio che chiama il runtime R abbia le autorizzazioni necessarie
+ Assicurarsi che l'account di accesso SQL o l'account utente di Windows che verrà usato per il codice R abbia le autorizzazioni necessarie per connettersi al server e ai relativi database

Per informazioni su alcuni problemi comuni, vedere l'articolo [Domande frequenti sull'installazione e sull'aggiornamento (SQL Server R Services)](../../advanced-analytics/r-services/upgrade-and-installation-faq-sql-server-r-services.md)

Se non si ha già un ambiente di sviluppo R preferito, per iniziare è possibile installare uno degli strumenti seguenti:

+ [Microsoft R Client](https://msdn.microsoft.com/microsoft-r/r-client-get-started)
+ [Strumenti R per Visual Studio](https://www.visualstudio.com/vs/rtvs/)

Si noti che le librerie R standard sono insufficienti per usare queste esercitazioni; l'ambiente di sviluppo R e il computer SQL Server che esegue R devono entrambi avere i pacchetti ScaleR di Microsoft installati. Per altre informazioni sui prodotti Microsoft R, vedere [Microsoft R Products](https://msdn.microsoft.com/microsoft-r/microsoft-r-getting-started#compare-prods) (Prodotti Microsoft R).

## <a name="additional-resources"></a>Risorse aggiuntive

Al termine di queste esercitazioni, usare i link seguenti per visualizzare esempi e scenari più avanzati.
  
### <a name="end-to-end-solution-templates-for-key-machine-learning-tasks"></a>Modelli di soluzioni end-to-end per attività chiave di apprendimento automatico  

[Machine Learning Templates with SQL Server 2016 R Services (Modelli di apprendimento automatico con SQL Server 2016 R Services)](https://blogs.technet.microsoft.com/machinelearning/2016/03/23/machine-learning-templates-with-sql-server-2016-r-services/).  

Il team Microsoft Machine Learning ha reso disponibile un set di modelli personalizzabili che consentono di avviare una soluzione di apprendimento automatico per le seguenti attività:  
* Rilevamento di frodi  
* Stima personalizzata del trasferimento  
* Manutenzione predittiva  
  
È disponibile tutto il codice T-SQL e R, oltre a istruzioni su come preparare e distribuire un modello per la valutazione mediante le stored procedure SQL Server. 

### <a name="sample-data-and-sample-scripts"></a>Dati e script di esempio  
Esempi di prodotto per [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] sono disponibili nell'Area download Microsoft. Per ottenere solo gli esempi per [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] selezionare il file zip e aprire la cartella **Advanced Analytics**.  Sebbene alcune delle istruzioni si riferiscano alle versioni precedenti, è disponibile una demo sul rilevamento delle frodi assicurative basata sulla legge di Benford e una procedura dettagliata semplice relativa a un modello predittivo in un set di dati molto piccolo (set di dati Iris) che potrebbe risultare utile per le demo.
  
[Esempi di prodotti SQL Server 2016](https://www.microsoft.com/en-us/download/details.aspx?id=49502)  
### <a name="learn-more-about-r"></a>Ulteriori informazioni su R  
Per altre informazioni su R in generale, vedere una delle utili risorse elencate di seguito: [Risorse per il linguaggio R](http://revolutionanalytics.com/r-language-resources).  
  
Per altre informazioni sui pacchetti R disponibili in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], visitare il  [sito Revolution Analytics](http://go.microsoft.com/fwlink/?LinkId=691541).  
  
Questo post di blog descrive il processo di uso dei pacchetti e delle funzioni R disponibili in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] per la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]e include codice di esempio: [Using R inside SQL Server (Uso di R in SQL Server)](http://blog.revolutionanalytics.com/2015/10/previewing-using-revolution-r-enterprise-inside-sql-server.html).  
  
## <a name="see-also"></a>Vedere anche  
[Introduzione a SQL Server R Services](../../advanced-analytics/r-services/getting-started-with-sql-server-r-services.md)  
[Funzionalità e attività di SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-features-and-tasks.md)  
  
