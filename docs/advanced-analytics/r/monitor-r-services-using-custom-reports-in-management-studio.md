---
title: Monitorare R Services tramite i report personalizzati in Management Studio | Microsoft Docs
ms.custom: 
ms.date: 02/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5933c72c-ba63-4966-b882-75719ef8428e
caps.latest.revision: 13
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 14f6d6d7373afd452f06acae43f7023de136bc71
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="monitor-r-services-using-custom-reports-in-management-studio"></a>Monitorare R Services tramite i report personalizzati in Management Studio
Per rendere più semplice la gestione di SQL Server R Services, il team del prodotto ha reso disponibili numerosi report personalizzati di esempio che possono essere aggiunti a SQL Server Management Studio per visualizzare i dettagli di R Services, ad esempio:

- Un elenco delle sessioni attive di R
- La configurazione di R dell'istanza corrente
- Statistiche di esecuzione per il runtime di R
- Un elenco degli eventi estesi per R Services
- Un elenco di pacchetti di R installati nell'istanza corrente

In questo argomento viene illustrato come installare e usare i report. Per altre informazioni sui report personalizzati in Management Studio, vedere [Report personalizzati in Management Studio](~/ssms/object/custom-reports-in-management-studio.md).

## <a name="how-to-install-the-reports"></a>Come installare i report

I report vengono progettati usando SQL Server Reporting Services, ma possono essere usati direttamente da SQL Server Management Studio, anche se Reporting Services non è installato sull'istanza. 

Per usare questi report:

* Scaricare i file RDL dal repository GitHub degli esempi di prodotto di SQL Server.
* Aggiungere i file nella cartella dei report personalizzati usata da SQL Server Management Studio.
* Aprire i report in SQL Server Management Studio.


### <a name="step-1-download-the-reports"></a>Passaggio 1. Scaricare i report

1. Aprire il repository di GitHub che contiene gli [esempi relativi ai prodotti SQL Server](https://github.com/Microsoft/sql-server-samples) e scaricare i report di esempio da questa pagina: 

   + [Report personalizzati SSMS](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/r-services/ssms-custom-reports)
      
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

Il repository in GitHub degli esempi di prodotto include attualmente i seguenti report per SQL Server R Services:

+ **R Services - Sessioni attive**

  Usare questo report per visualizzare gli utenti attualmente connessi all'istanza di SQL e che stanno eseguendo i processi R. 
  
+ **R Services - Configurazione**

  Usare questo report per visualizzare le proprietà della fase di esecuzione R e della configurazione di R Services. Il report indica se è necessario un riavvio e verifica la disponibilità dei protocolli di rete necessari. 
  
  Per l'esecuzione di R in un contesto di calcolo SQL è necessaria l'autenticazione implicita. A tal fine, il report verifica se esiste un accesso al database per il gruppo SQLRUserGroup.

  > [!NOTE]
  > Per altre informazioni su questi campi, vedere [Package metadata](http://r-pkgs.had.co.nz/description.html)(Metadati dei pacchetti) di Hadley Wickam. Ad esempio, è stato introdotto il campo *Nome alternativo* per il runtime di R per facilitare la distinzione tra le versioni. 

 + **R Services - Configurazione istanza** 

   Questo report consente di configurare R Services dopo l'installazione. Se R Services non è configurato correttamente, è possibile eseguirlo dal report precedente.
 
+ **R Services - Statistiche di esecuzione**

  Usare questo report per visualizzare le statistiche di esecuzione di R Services. Ad esempio, è possibile ottenere il numero totale di script R che sono stati eseguiti, il numero di esecuzioni parallele e le funzioni RevoScaleR usate più di frequente.
  Attualmente il report controlla solo le statistiche per le funzioni di pacchetto RevoScaleR.
  Fare clic su **View SQL Script** (Visualizza script SQL) per ottenere il codice T-SQL per il report. 

+ **R Services - Eventi estesi**

  Usare questo report per visualizzare un elenco degli eventi estesi disponibili per il monitoraggio dell'esecuzione degli script R. 
  Fare clic su **View SQL Script** (Visualizza script SQL) per ottenere il codice T-SQL per il report.

+ **R Services - Pacchetti**

  Usare questo report per visualizzare un elenco dei pacchetti R installati nell'istanza di SQL Server. Attualmente il report include le proprietà del pacchetto seguenti: 
  + Pacchetto (nome)
  + Versione 
  + Dipende da
  + Licenza
  + Compilato
  + Percorso libreria

+ **R Services - Uso risorse**

  Usare questo report per visualizzare il consumo di risorse di CPU, memoria e risorse di I/O in seguito all'esecuzione di script R di SQL Server. È anche possibile visualizzare l'impostazione di memoria del pool di risorse esterno. 


## <a name="see-also"></a>Vedere anche

[Monitoraggio di R Services](../../advanced-analytics/r-services/monitoring-r-services.md)

[Eventi estesi per R Services](../../advanced-analytics/r-services/extended-events-for-sql-server-r-services.md)


