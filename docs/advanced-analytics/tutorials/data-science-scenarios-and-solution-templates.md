---
title: Scenari di analisi scientifica dei dati e modelli di soluzioni (SQL Server Machine Learning) | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: d67fd15c44d188870989f2ad6498733c5901fb9d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="data-science-scenarios-and-solution-templates"></a>Scenari di analisi scientifica dei dati e modelli di soluzioni
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

I modelli sono soluzioni di esempio che illustrano le procedure consigliate e possono essere usati per implementare rapidamente una soluzione. Ogni modello è progettato per risolvere un problema specifico, per un verticale specifico o un settore. Le attività incluse in ogni modello vanno dalla preparazione dei dati alla progettazione della funzionalità fino al training e alla valutazione del modello. Utilizzare tali modelli per informazioni su come [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] funziona. Quindi, è possibile personalizzare il modello per adattarlo proprio scenario e compilare una soluzione personalizzata. 

Ogni soluzione include dati di esempio, il codice R o codice Python e le stored procedure SQL se applicabile. Eseguire il codice in preferito R o Python ambiente di sviluppo, con calcoli eseguiti in SQL Server. In alcuni casi, è possibile eseguire il codice direttamente mediante T-SQL e qualsiasi strumento client SQL, ad esempio SQL Server Management Studio.

> [!TIP]
> 
> La maggior parte dei modelli disponibili in più versioni che supporta sia in locale e cloud piattaforme per machine learning. Ad esempio, è possibile compilare la soluzione utilizza solo SQL Server oppure è possibile compilare la soluzione in Microsoft R Server o in Azure Machine Learning.

+ Per informazioni dettagliate e gli aggiornamenti, vedere questo annuncio: [interessanti nuovi modelli in Azure Machine Learning](https://blogs.technet.microsoft.com/machinelearning/2015/04/09/exciting-new-templates-in-azure-ml/)

+ Per il download e le istruzioni di installazione, vedere [illustrato come utilizzare i modelli](#bkmk_HowTo).

## <a name="fraud-detection"></a>Rilevamento di frodi

[Modello di rilevamento di frodi online (SQL Server R Services)](https://github.com/Microsoft/r-server-fraud-detection)

**Che cosa:** la capacità di rilevare le transazioni illecite è importante per le aziende online. Per ridurre le perdite di addebito, le aziende devono identificare rapidamente le transazioni effettuate utilizzando strumenti di pagamento rubato o le credenziali. Quando vengono rilevate transazioni illecite, le aziende in genere adottano misure per bloccare immediatamente determinati conti, al fine di evitare ulteriori perdite. In questo scenario, si imparare a utilizzare dati da transazioni di acquisto in linea per identificare le frodi probabile.

**Procedura:** rilevazione delle frodi viene risolto come un problema di classificazione binaria. La metodologia usata in questo modello può essere facilmente applicata al rilevamento di frodi in altri domini.


## <a name="campaign-optimization"></a>Ottimizzazione della campagna

[Prevedere come e quando contattare lead](https://microsoft.github.io/r-server-campaign-optimization/)

**Che cosa:** questa soluzione Usa dati assicurazione del settore per stimare lead basate su dati demografici, i dati di risposta cronologico e dettagli specifici del prodotto.  Indicazioni vengono generate anche per indicare la migliore canale e l'ora agli utenti di approccio per influenzare il comportamento di acquisto.

**Procedura:** crea e confronta più modelli della soluzione. La soluzione illustra inoltre l'integrazione automatica dei dati e la preparazione dei dati tramite le stored procedure. Esempi di parallela vengono forniti per SQL Server in-database, in Azure e HDInsight Spark. 

## <a name="health-care-predict-length-of-stay-in-hospital"></a>Sanità: stimare durata della permanenza in ospedale 

[Stima di durata di viene](https://gallery.cortanaintelligence.com/Solution/Predicting-Length-of-Stay-in-Hospitals-1)

**Che cosa:** stimare in modo accurato quali pazienti potrebbero richiedere ricovero a lungo termine è una parte importante di attenzione e pianificazione. Gli amministratori devono essere in grado di determinare quali strutture richiedono ulteriori risorse e operatori sanitari desidera garantire che soddisfino le esigenze di pazienti.

**Procedura:** questa soluzione Usa la macchina virtuale di analisi scientifica dei dati e include un'istanza di SQL Server con machine learning abilitato. Include inoltre un set di report di Power BI che è possibile utilizzare per interagire con un modello distribuito.

## <a name="customer-churn"></a>Varianza del cliente

[Modello di stima della varianza del cliente (SQL Server R Services)](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/Churn/Introduction.md)

**Che cosa:** analisi e stima della varianza del cliente è importante in ogni settore in cui deve essere gestita e ha impedita la perdita di clienti da concorrenti: banking, telecomunicazioni e delle vendite al dettaglio, solo per citarne alcune. L'obiettivo dell'analisi dell'abbandono dei clienti è l'identificazione dei clienti con alta probabilità di abbandono e l'adozione di misure appropriate per mantenere tali clienti e la loro attività.

**Procedura:** questo modello formula il problema di varianza come un **classificazione binaria** problema. Mediante dati di esempio provenienti da due origini (dati demografici e transazioni dei clienti), il modello indica se la probabilità di abbandono dei singoli clienti è alta o bassa.
  
## <a name="predictive-maintenance"></a>Manutenzione predittiva

[Modello di manutenzione predittiva (SQL Server 2016)](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/PredictiveMaintenance/Introduction.md)

**Che cosa:** manutenzione predittiva ha lo scopo di aumentare l'efficienza delle attività di manutenzione acquisendo precedenti errori e utilizzo di tali informazioni per stimare quando o in un dispositivo potrebbe non riuscire. La possibilità di previsione obsolescenza dei dispositivi è particolarmente importante per le applicazioni che si basano sui dati distribuiti o sensori. Questo metodo può anche essere applicato per monitorare o stimare errori nei dispositivi IoT (Internet of Things).

Questo annuncio per altre informazioni: [nuovo modello di manutenzione predittiva](https://blogs.technet.microsoft.com/machinelearning/2015/04/09/exciting-new-templates-in-azure-ml/)

**Procedura:** questa soluzione è incentrata sulla rispondere alla domanda "Quando una macchina in circolazione riuscirà?" I dati di input rappresentano misurazioni simulate di sensori per motori di aerei. Dati ottenuti dal monitoraggio corrente operazione condizioni del modulo, ad esempio il ciclo di lavoro corrente, impostazioni e le misurazioni sensore, vengono utilizzati per creare tre tipi di modelli predittivi:

-   **Modelli di regressione**per stimare quanto un motore può continuare a funzionare prima di bloccarsi. Il modello di esempio consente di stimare la metrica "Rimanenti vita utile" (RUL), denominato anche "Per errore di runtime" (TTF).
  
-   **Modelli di classificazione**per determinare la probabilità che un motore si guasti.
  
    Il **modello di classificazione binaria** consente di stimare se un motore avrà esito negativo in un determinato periodo di tempo.

    Il **modello di classificazione multiclasse** consente di stimare se un determinato motore potrebbe non riuscire e fornisce un intervallo di tempo probabile dell'errore. Ad esempio, per un determinato giorno, è possibile prevedere se un dispositivo potrebbe guastarsi in tale giorno o in un determinato periodo di tempo successivo al giorno specificato.

## <a name="energy-demand-forecasting"></a>Previsione della domanda di energia

[Domanda di energia previsione modello con SQL Server R Services](https://gallery.cortanaintelligence.com/Tutorial/Energy-Demand-Forecast-Template-with-SQL-Server-R-Services-1)

**Che cosa:**: Demand forecasting è un problema importante in vari domini inclusi energia, delle vendite al dettaglio e servizi. Previsione accurata richiesta aiuta le aziende condurre produzione migliori la pianificazione, l'allocazione delle risorse e altre decisioni aziendali più importanti. Nel settore dell'energia, è fondamentale per ridurre il costo di archiviazione di energia e bilanciamento del carico di domanda e offerta richiesta previsione.

**Procedura:** questo modello utilizza SQL Server R Services per stimare domanda di energia elettrica. Il modello utilizzato per la stima è un modello di regressione di foresta casuale basato su **rxDForest**, un'ad alte prestazioni algoritmo di machine learning inclusa in Microsoft R Server. La soluzione include un simulatore di domanda, tutto il codice R e T-SQL necessario per il training del modello e le stored procedure da usare per generare le previsioni e includerle in report. 


## <a name="bkmk_HowTo"></a>Come utilizzare i modelli

Per scaricare i file inclusi in ogni modello è possibile usare i comandi di GitHub oppure aprire il collegamento e fare clic su **Download Zip** (Scarica zip) per salvare tutti i file nel computer.  Dopo che è stata scaricata, la soluzione contiene in genere le seguenti cartelle:
  
-   **Data**: contiene i dati di esempio per ogni applicazione.
  
-   **R**: contiene tutto il codice di sviluppo R necessario per la soluzione. La soluzione richiede le librerie di Microsoft R Server, ma può essere aperta e modificata in qualsiasi IDE R. Il codice R è stato ottimizzato con l'esecuzione dei calcoli all'interno del database, impostando il contesto di calcolo su un'istanza di SQL Server.
  
-   **SQLR**: contiene più file con estensione sql eseguibili in un ambiente SQL quale [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per creare le stored procedure che eseguono attività correlate quali l'elaborazione dei dati, la progettazione delle funzionalità e la distribuzione del modello.
  
    La cartella contiene anche uno script di PowerShell che consente di chiamare tutti gli script e di creare l'ambiente end-to-end. Modificare lo script in base alle esigenze dell'ambiente di elaborazione.

## <a name="next-steps"></a>Passaggi successivi

+ [Esercitazioni di SQL Server machine learning](machine-learning-services-tutorials.md)




