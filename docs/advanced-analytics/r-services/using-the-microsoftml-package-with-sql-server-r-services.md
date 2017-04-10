---
title: "Uso del pacchetto MicrosoftML con SQL Server R Services | Microsoft Docs"
ms.custom: ""
ms.date: "01/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "R"
ms.assetid: 1c377717-e281-431e-8171-3924dcce1cdd
caps.latest.revision: 12
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 10
---
# Uso del pacchetto MicrosoftML con SQL Server R Services
Il pacchetto **MicrosoftML** fornito con Microsoft R Server ed SQL Server vNext CTP 1.0 include più algoritmi di apprendimento automatico sviluppati da Microsoft che supportano l'elaborazione multicore e il flusso rapido dei dati. Il pacchetto include inoltre le trasformazioni per l'elaborazione di testo e la creazione di funzionalità.

### <a name="new-machine-learning-algorithms"></a>Nuovi algoritmi di apprendimento automatico


-  **Strumento di apprendimento lineare rapido.** Uno strumento di apprendimento lineare basato sui metodi SDCA (Stochastic Dual Coordinate Ascent) che può essere usato per la regressione o la classificazione binaria. Il modello supporta la regolarizzazione L1 ed L2.

- **Struttura ad albero rapida.** Un algoritmo di albero delle decisioni con boosting, originariamente noto come FastRank, sviluppato per l'utso in Bing. È uno degli strumenti di apprendimento più noti e veloci. Supporta la regressione e la classificazione binaria.

- **Foresta rapida.** Un modello di regressione logistica basato sul metodo della foresta casuale. È simile alla funzione `rxLogit` in RevoScaleR, ma supporta la regolarizzazione L1 ed L2. Supporta la regressione e la classificazione binaria.

- **Regressione logistica.** Un modello di regressione logistica simile alla funzione `rxLogit` in RevoScaleR con supporto aggiuntivo per la regolarizzazione L1 ed L2. Supporta la classificazione multiclasse o binaria.

- **Rete neurale.** Un modello di rete neurale per la classificazione binaria, la classificazione multiclasse e la regressione. Supporta l'accelerazione GPU e le reti complesse personalizzabili.

- **SVM a una classe.** Un modello di rilevamento delle anomalie basato sul metodo SVM che può essere usato per la classificazione binaria in set di dati bilanciati.

## <a name="transformation-functions"></a>Funzioni di trasformazione

Il pacchetto **MicrosoftML** include inoltre le funzioni seguenti che possono essere usate per la trasformazione dei dati e le funzionalità di estrazione.

- `featurizeText()`
 
  Genera il numero di n-grammi in una specifica stringa di testo. 

  La funzione include le opzioni di rilevamento del linguaggio usato, esegue la creazione di token per il testo e la normalizzazione, rimuove le parole non significative e genera funzionalità a partire dal testo. 

- `categorical()`

  Crea un dizionario di categorie e trasforma ogni categoria in un vettore indicatore. 
 
- `categoricalHash()`

  Converte i valori categorici in una matrice indicatore eseguendo l'hash dei valori e usando l'hash come indice nel contenitore.  

- `selectFeatures()` 

  Seleziona un sottoinsieme di funzionalità da una variabile specificata, calcolando i valori non predefiniti o un punteggio di informazioni comuni rispetto all'etichetta. 

Per informazioni dettagliate su queste nuove funzionalità, vedere [MicrosoftML functions](https://msdn.microsoft.com/microsoft-r/microsoftml/microsoftml) (Funzioni di MicrosoftML).

## <a name="support-for-microsoftml-in-r-services"></a>Supporto per MicrosoftML in R Services

Il pacchetto **MicrosoftML** è completamente integrato con la pipeline di elaborazione dei dati usata dal pacchetto **RevoScaleR**. Attualmente, è possibile usare il pacchetto **MicrosoftML** in qualsiasi contesto di calcolo basato su Windows, incluso SQL Server R Services.



## <a name="see-also"></a>Vedere anche


[RevoScaleR Function Reference](https://msdn.microsoft.com/microsoft-r/scaler/scaler) (Informazioni di riferimento per le funzioni di RevoScaleR)

