---
title: "Distribuire da SQL Server Data Tools (SSAS tabulare) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.asvs.bidtoolset.deploystatus.f1"
ms.assetid: 67dde3fe-ba43-41f3-b56c-c656029ee93f
caps.latest.revision: 17
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 17
---
# Distribuire da SQL Server Data Tools (SSAS tabulare)
  Utilizzare le attività contenute in questo argomento per distribuire una soluzione del modello tabulare utilizzando il comando Distribuisci in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Sezioni dell'argomento:  
  
-   [Configurare le proprietà Opzioni di distribuzione e Server di distribuzione](#bkmk_deploy)  
  
-   [Distribuire una soluzione del modello tabulare](#bkmk_deploy_proc)  
  
-   [Stato distribuzione](#bkmk_deploy_status)  
  
##  <a name="bkmk_deploy"></a> Configurare le proprietà Opzioni di distribuzione e Server di distribuzione  
 Prima di distribuire tale soluzione, è necessario innanzitutto specificare le proprietà Opzioni di distribuzione e Server di distribuzione. Per altre informazioni sulle impostazioni e le proprietà di distribuzione, vedere [Distribuzione di una soluzione del modello tabulare &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md).  
  
#### Per configurare le proprietà Opzioni di distribuzione e Server di distribuzione  
  
1.  In **Esplora soluzioni** di [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] fare clic con il pulsante destro del mouse sul nome del progetto, quindi scegliere **Proprietà**.  
  
2.  In **Opzioni di distribuzione** della finestra di dialogo **Proprietà di \><nome progetto>** specificare le impostazioni delle proprietà se diverse dalle impostazioni predefinite.  
  
    > [!NOTE]  
    >  Per i modelli in modalità cache, in corrispondenza di **Modalità query** è sempre selezionata l'opzione **In-Memory**.  
  
    > [!NOTE]  
    >  Non è possibile specificare **Impostazioni di rappresentazione** per i modelli in modalità DirectQuery.  
  
3.  In **Server di distribuzione** specificare le impostazioni delle proprietà **Server** (nome), **Edizione**, **Database** (nome) e **Nome cubo**, se diverse dalle impostazioni predefinite, quindi fare clic su **OK**.  
  
> [!NOTE]  
>  È inoltre possibile specificare l'impostazione della proprietà Server di distribuzione predefinito in modo che tutti i nuovi progetti creati vengano distribuiti automaticamente nel server specificato. Per altre informazioni, vedere [Configurare la modellazione dei dati e le proprietà di distribuzione predefinite &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md).  
  
##  <a name="bkmk_deploy_proc"></a> Distribuire una soluzione del modello tabulare  
  
#### Per distribuire una soluzione del modello tabulare  
  
-   In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], nel menu **Compila**, fare clic su **Distribuisci \<nome progetto>**.  
  
     Verrà visualizzata la finestra di dialogo **Distribuisci** e verrà fornita l'indicazione dello stato della distribuzione dei metadati e dell'elaborazione di ogni tabella inclusa nel modello, a meno che la proprietà Opzione di elaborazione non sia impostata su Non elaborare. Una volta completato il processo di distribuzione, utilizzare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per connettersi all'istanza di Analysis Services e verificare il nuovo oggetto di database modello creato. In alternativa, utilizzare un'applicazione client di creazione report per connettersi al modello distribuito.  
  
##  <a name="bkmk_deploy_status"></a> Stato distribuzione  
 La finestra di dialogo **Distribuisci** consente di monitorare lo stato di un'operazione di distribuzione. Inoltre è possibile arrestare un'operazione di distribuzione.  
  
 **Stato**  
 Viene indicato se l'operazione di distribuzione ha avuto esito positivo o negativo.  
  
 **Dettagli**  
 Vengono elencati gli elementi dei metadati distribuiti, lo stato di ogni elemento dei metadati e viene fornito un messaggio relativo a eventuali problemi.  
  
 **Arresta distribuzione**  
 Fare clic su questa opzione per arrestare l'operazione di distribuzione. Questa opzione è utile se l'operazione di distribuzione è troppo lunga o se si sono verificati troppi errori.  
  
## Vedere anche  
 [Distribuzione di una soluzione del modello tabulare &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md)   
 [Configurare la modellazione dei dati e le proprietà di distribuzione predefinite &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)  
  
  