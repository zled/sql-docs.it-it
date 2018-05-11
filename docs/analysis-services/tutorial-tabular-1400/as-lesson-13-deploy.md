---
title: "Lezione dell'esercitazione di Analysis Services 13: distribuire | Documenti Microsoft"
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 57ddfe2f2d00b098fbffa40811a7877752fefed4
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="deploy"></a>Distribuzione

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

In questa lezione, configurare le proprietà di distribuzione; Specifica un server per distribuire e un nome per il modello. È quindi possibile distribuire il modello al server. Dopo aver distribuito il modello, gli utenti possono connettersi a esso tramite un'applicazione client di creazione di report. Per ulteriori informazioni, vedere [Distribuisci ad Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-deploy) e [distribuzione della soluzione di modello tabulare](../tabular-models/tabular-model-solution-deployment-ssas-tabular.md).  
  
Tempo stimato per il completamento della lezione: **5 minuti**  
  
## <a name="prerequisites"></a>Prerequisiti  

In questo articolo fa parte di un'esercitazione di modellazione tabulare, che deve essere completata nell'ordine. Prima di eseguire le attività in questa lezione, è necessario avere completato la lezione precedente: [lezione 12: analizza in Excel](../tutorial-tabular-1400/as-lesson-12-analyze-in-excel.md).  

> [!IMPORTANT]  
> Se la distribuzione in Azure Analysis Services, è necessario disporre [le autorizzazioni di amministratore](https://docs.microsoft.com/azure/analysis-services/analysis-services-server-admins) sul serever.  

> [!IMPORTANT]  
> Se è installato il database di esempio AdventureWorksDW in un Server SQL locale e si distribuisce il modello in un server di Azure Analysis Services, un [gateway dati locale](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway) è obbligatorio.
  
## <a name="deploy-the-model"></a>Distribuire il modello  
  
#### <a name="to-configure-deployment-properties"></a>Per configurare le proprietà di distribuzione  

  
1.  In **Esplora**, fare doppio clic su di **AW Internet Sales** del progetto e quindi fare clic su **proprietà**.  
  
2.  Nel **pagine delle proprietà di AW Internet Sales** nella finestra di dialogo **Server di distribuzione**nella **Server** proprietà, immettere il nome completo del server. Se la connessione ad Azure Analysis Services, nome del server deve rappresentare l'URL completo.

    ![as-lesson13-deploy-property](../tutorial-tabular-1400/media/as-lesson13-deploy-property.png)
  
3.  Nel **Database** proprietà, digitare **Adventure Works Internet Sales**.  
  
4.  Nel **nome modello** proprietà, digitare **Adventure Works Internet Sales Model**.  
  
5.  Verificare le opzioni selezionate e fare clic su **OK**.  
  
#### <a name="to-deploy-the-adventure-works-internet-sales"></a>Per distribuire Adventure Works Internet Sales
  
1.  In **Esplora**, fare doppio clic su di **AW Internet Sales** progetto > **compilare**.  

2.  Fare doppio clic su di **AW Internet Sales** progetto > **Distribuisci**.

    Quando si distribuisce ad Azure Analysis Services, potrebbe essere richiesto di immettere l'account. Immettere l'account aziendale e una password, ad esempio nancy@adventureworks.com. Questo account deve essere Admins nel server.
  
    Verrà visualizzata la finestra di dialogo Distribuisci Visualizza lo stato di distribuzione dei metadati e ogni tabella inclusa nel modello.  
    
    ![as-lesson13-deploy-status](../tutorial-tabular-1400/media/as-lesson13-deploy-status.png)
  
3. Dopo aver completato la distribuzione, fare clic su **Chiudi**.  
  

In questa lezione viene descritto il metodo più semplice e più comune per distribuire un modello tabulare in SSDT. Opzioni avanzate di distribuzione, ad esempio la procedura guidata distribuzione o l'automazione AMO e XMLA forniscono maggiore flessibilità, coerenza e installazioni pianificate. Per ulteriori informazioni, vedere [distribuzione della soluzione di modello tabulare](../tabular-models/tabular-model-solution-deployment-ssas-tabular.md).

## <a name="conclusion"></a>Conclusioni  
Congratulazioni! Si è finito di creazione e la distribuzione del primo modello tabulare di Analysis Services. Tramite questa esercitazione sono state completate le attività più comuni di creazione di un modello tabulare. Ora che il modello Adventure Works Internet Sales è stato distribuito, è possibile utilizzare SQL Server Management Studio per gestire il modello, nonché creare script di processo e un piano di backup. Gli utenti possono ora connettersi al modello utilizzando un'applicazione client di creazione di report, ad esempio Microsoft Excel o Power BI.  

![ssms come lesson13](../tutorial-tabular-1400/media/as-lesson13-ssms.png)
  
  
  
## <a name="whats-next"></a>Quali sono le operazioni successive?
[Connettersi a Power BI Desktop](https://docs.microsoft.com/azure/analysis-services/analysis-services-connect-pbi)   
[Lezione supplementare - sicurezza dinamica](../tutorial-tabular-1400/as-supplemental-lesson-dynamic-security.md)   
[Lezione supplementare - righe di dettaglio](../tutorial-tabular-1400/as-supplemental-lesson-detail-rows.md)   
[Lezione supplementare - gerarchie incomplete](../tutorial-tabular-1400/as-supplemental-lesson-ragged-hierarchies.md)   
