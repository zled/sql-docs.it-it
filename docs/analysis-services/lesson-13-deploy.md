---
title: 'Lezione 14: Distribuire | Documenti Microsoft'
ms.custom: 
ms.date: 03/27/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 24863a8a-9017-415a-a97b-fbac76ed0675
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 29a05dfbeea281b2468b95e69b458d4948f7f624
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/23/2018
---
# <a name="lesson-13-deploy"></a>Lezione 13: distribuire
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

In questa lezione si configurerà le proprietà di distribuzione; Specifica una locale o istanza del server Azure e un nome per il modello. Distribuire il modello verrà quindi a tale istanza. Dopo aver distribuito il modello, gli utenti possono connettersi a esso tramite un'applicazione client di creazione di report. Per ulteriori informazioni sulla distribuzione, vedere [distribuzione della soluzione di modello tabulare](../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md) e [Distribuisci ad Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-deploy).  
  
Tempo stimato per il completamento della lezione: **5 minuti**  
  
## <a name="prerequisites"></a>Prerequisiti  
Questo argomento fa parte di un'esercitazione relativa alla modellazione tabulare che deve essere completata nell'ordine specificato. Prima di eseguire le attività in questa lezione, è necessario avere completato la lezione precedente: [lezione 12: analizza in Excel](../analysis-services/lesson-12-analyze-in-excel.md).  
  
## <a name="deploy-the-model"></a>Distribuire il modello  
  
#### <a name="to-configure-deployment-properties"></a>Per configurare le proprietà di distribuzione  
  
1.  In **Esplora**, fare doppio clic su di **AW Internet Sales** del progetto e quindi fare clic su **proprietà**.  
  
2.  Nel **pagine delle proprietà di AW Internet Sales** nella finestra di dialogo **Server di distribuzione**nella **Server** proprietà, digitare il nome di un server di Azure Analysis Services o un istanza del server locale in esecuzione in modalità tabulare. Questo sarà l'istanza del server in cui verrà distribuito il modello.  

    ![aas-deploy-deployment-server-property](../analysis-services/media/aas-deploy-deployment-server-property.png)
 
    > [!IMPORTANT]  
    > Il remoto Analysis Services istanza in ordine per eseguire la distribuzione, è necessario disporre delle autorizzazioni di amministratore.  
  
3.  Nel **Database** proprietà, digitare **Adventure Works Internet Sales**.  
  
4.  Nel **nome modello** proprietà, digitare **Adventure Works Internet Sales Model**.  
  
5.  Verificare le opzioni selezionate e fare clic su **OK**.  
  
#### <a name="to-deploy-the-adventure-works-internet-sales-tabular-model"></a>Per distribuire il modello tabulare Adventure Works Internet Sales  
  
1.  In **Esplora**, fare doppio clic su di **AW Internet Sales** progetto > **compilare**.  

2.  Fare doppio clic su di **AW Internet Sales** progetto > **Distribuisci**.

    Quando si distribuisce ad Azure Analysis Services, è probabile che chiesto di immettere l'account. Immettere l'account aziendale e una password, ad esempio nancy@adventureworks.com. Questo account deve essere Admins nell'istanza del server.
  
    Verrà visualizzata la finestra di dialogo Distribuisci in cui sono indicati lo stato della distribuzione e ogni tabella inclusa nel modello.  
    
    ![aas-deploy-status](../analysis-services/media/aas-deploy-status.png)
  
3. Dopo aver completato la distribuzione, fare clic su **Chiudi**.  
  
## <a name="conclusion"></a>Conclusioni  
Congratulazioni! Si è finito di creazione e la distribuzione del primo modello tabulare di Analysis Services. Tramite questa esercitazione sono state completate le attività più comuni di creazione di un modello tabulare. Ora che il modello Adventure Works Internet Sales è stato distribuito, è possibile utilizzare SQL Server Management Studio per gestire il modello, nonché creare script di processo e un piano di backup. Gli utenti possono ora connettersi al modello utilizzando un'applicazione client di creazione di report, ad esempio Microsoft Excel o Power BI.  

![as-tabular-lesson13-ssms](../analysis-services/media/as-tabular-lesson13-ssms.png)
  
  
## <a name="see-also"></a>Vedere anche  
[Modalità DirectQuery](../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)  
[Configurare le proprietà di modellazione e distribuzione dei dati predefinite](../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)  
[Database modello tabulare](../analysis-services/tabular-models/tabular-model-databases-ssas-tabular.md)  
  
  
  ## <a name="whats-next"></a>Quali sono le operazioni successive?
*  [Lezione supplementare - implementare la sicurezza dinamica mediante i filtri di riga](../analysis-services/supplemental-lesson-implement-dynamic-security-by-using-row-filters.md).

*  [Supplementare lezione - configurare le proprietà di creazione di report per i report Power View](../analysis-services/supplemental-lesson-configure-reporting-properties-for-power-view-reports.md).
