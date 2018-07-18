---
title: Monitorare i servizi R con i report personalizzati in Management Studio | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 0e444612a5acd0726bdd6fb743e43813d6b0caf7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="monitor-machine-learning-services-using-custom-reports-in-management-studio"></a>Monitoraggio Machine Learning Services utilizzando i report personalizzati in Management Studio
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Per rendere più facile da gestire istanza usato per machine learning, il team del prodotto ha fornito un numero di report personalizzato di esempio che è possibile aggiungere a SQL Server Management Studio. In questi rapporti, è possibile visualizzare i dettagli, ad esempio:

- Sessioni R Active o Python
- Impostazioni di configurazione per l'istanza
- Statistiche di esecuzione per i processi di machine learning
- Eventi estesi per R Services
- Pacchetti R o Python installati nell'istanza corrente

In questo articolo viene illustrato come installare e utilizzare i report personalizzati forniti in modo specifico per leaerning macchina. 

Per un'introduzione generale a report in Management Studio, vedere [report personalizzati in Management Studio](../../ssms/object/custom-reports-in-management-studio.md).

## <a name="how-to-install-the-reports"></a>Come installare i report

I report vengono progettati usando SQL Server Reporting Services, ma possono essere usati direttamente da SQL Server Management Studio, anche se Reporting Services non è installato sull'istanza. 

Per usare questi report:

* Scaricare i file RDL dal repository GitHub degli esempi di prodotto di SQL Server.
* Aggiungere i file nella cartella dei report personalizzati usata da SQL Server Management Studio.
* Aprire i report in SQL Server Management Studio.


### <a name="step-1-download-the-reports"></a>Passaggio 1. Scaricare i report

1. Aprire il repository di GitHub che contiene [esempi del prodotto SQL Server](https://github.com/Microsoft/sql-server-samples)e scaricare i report di esempio. 

    + [Report personalizzati di SQL Server Management Studio](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/machine-learning-services/ssms-custom-reports)

    > [!NOTE]
    > I report possono essere utilizzati con SQL Server 2017 MCM Learning Services o SQL Server 2016 R Services.

2. Per scaricare gli esempi, è anche possibile accedere a GitHub e creare un fork locale degli esempi. 

### <a name="step-2-copy-the-reports-to-management-studio"></a>Passaggio 2. Copiare i report in Management Studio

3. Individuare la cartella dei report personalizzati usata da SQL Server Management Studio. Per impostazione predefinita, i report personalizzati vengono archiviati in questa cartella:
    
   `C:\Users\user_name\Documents\SQL Server Management Studio\Custom Reports`

   È tuttavia possibile specificare una cartella diversa oppure creare sottocartelle.

4. Copiare i file con estensione rdl nella cartella dei report personalizzati.


### <a name="step-3-run-the-reports"></a>Passaggio 3. Eseguire i report

5. In Management Studio fare doppio clic sul nodo **Database** per l'istanza in cui si vogliono eseguire i report.
6. Fare clic su **Report**e quindi su **Report personalizzati**.
7. Nella finestra di dialogo **Apri file** individuare la cartella dei report personalizzati.
8. Selezionare uno dei file RDL scaricati e fare clic su **Apri**.

> [!IMPORTANT]
> Su alcuni computer, ad esempio quelli con periferiche video con DPI elevato o risoluzione maggiore di 1080p, o in alcune sessioni di desktop remoto, questi report non possono essere usati. È presente un bug nel controllo Visualizzatore report in SSMS che provoca il blocco del report.

## <a name="report-list"></a>Elenco dei report

Repository di esempi di prodotto in GitHub include attualmente i report seguenti:

+ **R Services - Sessioni attive**

  Utilizzare questo report per visualizzare gli utenti che sono attualmente connessi per l'istanza di SQL Server e in esecuzione di machine learning i processi. 
  
+ **R Services - Configurazione**

  Utilizzare questo report per visualizzare la configurazione del runtime di script esterni e i servizi correlati. Il report indica se è necessario un riavvio e verifica la disponibilità dei protocolli di rete necessari. 
  
  Autenticazione implicita è necessaria per attività di machine learning in esecuzione in SQL Server come un contesto di calcolo. Per verificare che l'autenticazione implicita è configurato, il report viene verificata l'esistenza di un accesso al database per il gruppo SQLRUserGroup.

 + **R Services - Configurazione istanza** 

   Questo report consentono di configurare l'apprendimento. È anche possibile eseguire questo report per correggere gli errori di configurazione, vedere il report precedente.
 
+ **R Services - Statistiche di esecuzione**

  Utilizzare questo report per visualizzare le statistiche di esecuzione per i processi di machine learning. Ad esempio, è possibile ottenere il numero totale di script R che sono stati eseguiti, il numero di esecuzioni parallele e le funzioni RevoScaleR usate più di frequente. Fare clic su **Visualizza Script SQL** per ottenere il codice T-SQL completo dietro il report.

  Attualmente il report controlla solo le statistiche per le funzioni di pacchetto RevoScaleR.

+ **R Services - Eventi estesi**

  Utilizzare questo report per visualizzare un elenco degli eventi estesi sono disponibili per il monitoraggio delle attività correlate al runtime dello script esterno. Fare clic su **Visualizza Script SQL** per ottenere il codice T-SQL completo dietro il report.

+ **R Services - Pacchetti**

  Utilizzare questo report per visualizzare un elenco dei pacchetti R o Python installata nell'istanza di SQL Server.

+ **R Services - Uso risorse**

  Utilizzare questo report per visualizzare il consumo di risorse della CPU, memoria e i/o dall'esecuzione dello script esterno. È anche possibile visualizzare l'impostazione di memoria del pool di risorse esterno.

## <a name="see-also"></a>Vedere anche

[Monitoraggio dei servizi](managing-and-monitoring-r-solutions.md)

[Eventi estesi per R Services](extended-events-for-sql-server-r-services.md)
