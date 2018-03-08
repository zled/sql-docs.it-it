---
title: "Aggiungere dati di esempio per un modello DirectQuery in modalità progettazione | Documenti Microsoft"
ms.custom: 
ms.date: 02/21/2018
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1af1e823-85aa-4319-a93f-98b35f7c7322
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 068366df63bbe37d658345c1157a9d02eb7e5187
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/23/2018
---
# <a name="add-sample-data-to-a-directquery-model-in-design-mode"></a>Aggiungere dati di esempio a un modello DirectQuery in modalità progettazione
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
In modalità DirectQuery è possibile usare le partizioni di tabella per creare subset di dati di esempio durante la progettazione di modelli oppure per creare alternative di una visualizzazione completa di dati.
 
 Quando si distribuisce un modello tabulare di DirectQuery, è consentita una sola partizione per tabella. Tale partizione deve essere necessariamente una visualizzazione completa di dati. Una qualsiasi altra partizione sostituisce una visualizzazione completa di dati o dati di esempio. Questo argomento illustra come creare una partizione di esempio con un subset di dati.
 
 Per impostazione predefinita, quando si progetta un modello tabulare in modalità DirectQuery in SSDT, il database di lavoro del modello non contiene alcun dato. È presente una partizione predefinita per ogni tabella e tale partizione indirizza tutte le query all'origine dati. 
  
È tuttavia possibile aggiungere una quantità ridotta di dati di esempio al database di lavoro del modello per l'uso in fase di progettazione. I dati di esempio vengono specificati tramite una query in una partizione di esempio usata solo durante la progettazione e vengono memorizzati nella cache insieme al modello. In tal modo sarà possibile convalidare le decisioni di modellazione mentre si procede, senza alcun impatto sull'origine dati. È possibile testare le decisioni di modellazione con il set di dati di esempio quando si usa **Analizza in Excel** in SQL Server Data Tools (SSDT) o tramite altre applicazioni client che si connettono al database dell'area di lavoro.  
  
> [!TIP]  
>  Anche in modalità DirectQuery in un modello vuoto è sempre possibile visualizzare un piccolo set di righe predefinito per ogni tabella. In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]fare clic su **Tabella** > **Proprietà tabella** per visualizzare il set di dati di 50 righe.  
  
## <a name="create-a-sample-partition"></a>Creare una partizione di esempio
 Queste istruzioni sono valide per modelli tabulari creato o aggiornato a livello di compatibilità 1200 o superiore. I modelli con livelli di compatibilità inferiori usano proprietà diverse per ottenere i dati memorizzati nella cache. Per le descrizioni delle proprietà, vedere [Abilitare la modalità DirectQuery in SQL Server Management Studio](../../analysis-services/tabular-models/enable-directquery-mode-in-ssms.md) .  
  
1.  Nel diagramma o nella visualizzazione dati di SQL Server Data Tools selezionare una tabella dei fatti per aprire la pagina delle proprietà corrispondente. Le tabelle dei fatti consentono di aggiungere dati aggregati, dati numerici e misure al modello. È possibile averne più di una.  
  
2.  Fare clic su **Tabella** > **Proprietà** per aprire la finestra di dialogo Gestione partizioni.  
  
    Si noti la partizione predefinita è **(DirectQuery) \<nome tabella >**. Si tratta della visualizzazione completa di dati. Non eliminare la partizione. Questa partizione sarà usata durante la distribuzione del modello.  
  
4.  Selezionare la partizione e fare clic su **Copia**.  

    In questo modo viene creata una copia della partizione predefinita, che tuttavia conterrà i dati di esempio specificati in una query. Esempio:
  
     ![ssas_tabularproject_copypartition](../../analysis-services/tabular-models/media/ssas-tabularproject-copypartition.jpg "ssas_tabularproject_copypartition")  
  
5.  Selezionare la partizione copiata e quindi fare clic sul pulsante **Editor di query SQL** per aggiungere un filtro. Ridurre la dimensione dei dati di esempio durante la creazione del modello. Se ad esempio è stata selezionata la partizione **FactInternetSales** in AdventureWorksDW, il filtro potrebbe essere simile al seguente:  
  
    ```  
    SELECT [dbo].[FactInternetSales].* FROM [dbo].[FactInternetSales]  
    JOIN DimSalesTerritory as ST  
    ON ST.SalesTerritoryKey = FactInternetSales.SalesTerritoryKey  
    WHERE ST.SalesTerritoryGroup='North America';  
    ```  
  
6.  Fare clic su **Convalida** per verificare la presenza di errori di sintassi.  
  
     Si noti che in modalità DirectQuery, oltre ai pulsanti **Nuovo** , **Copia**ed **Elimina** nella finestra di dialogo Partizioni, è disponibile anche un pulsante di attivazione/disattivazione che legge in modo alternato **Imposta come esempio** o **Imposta come DirectQuery**.  
  
     La partizione DirectQuery può essere solo una. È possibile controllare questa condizione selezionando la partizione definita per la tabella e facendo clic su **Imposta come esempio**.  
  
7.  Elaborare la tabella.  
  


  
  
