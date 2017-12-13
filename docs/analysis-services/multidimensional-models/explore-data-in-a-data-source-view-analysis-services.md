---
title: Esplorare i dati in una vista origine dati (Analysis Services) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exploring data [Analysis Services]
- data source views [Analysis Services], exploring data
- viewing source data
ms.assetid: 2c922c35-fbcb-45b2-96b1-c7a846d8b419
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0d6788ac8b59b9f962e32cadaa3312372732aa3c
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="explore-data-in-a-data-source-view-analysis-services"></a>Esplorare dati in una vista origine dati (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]È possibile utilizzare il **Esplora dati** nella finestra di dialogo di progettazione di viste origine dati in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] per esplorare i dati per una tabella, vista o una query denominata in un'origine dati (DSV) visualizzare. Quando si esplorano i dati in Progettazione vista origine dati, è possibile visualizzare il contenuto di ogni colonna di dati in una tabella, una vista o una query denominata selezionata. La visualizzazione del contenuto effettivo consente di determinare se sono necessarie tutte le colonne, se sono necessari calcoli denominati per incrementare la fruibilità e la facilità di utilizzo per gli utenti e se le query denominate o i calcoli denominati esistenti restituiscono i valori previsti.  
  
 Per visualizzare i dati, è necessario disporre di una connessione attiva alle origini dati per l'oggetto selezionato nella vista origine dati. Nella query vengono inviati anche i calcoli denominati contenuti in una tabella.  
  
 I dati restituiti in un formato tabulare che è possibile ordinare e copiare. Fare clic sull'intestazione di colonna per riordinare le righe in base alla colonna. È anche possibile evidenziare i dati nella griglia e premere CTRL-C per copiare la selezione negli Appunti.  
  
 È inoltre possibile controllare il metodo di campionamento e il conteggio campione. Per impostazione predefinita, vengono restituite le prime 5000 righe.  
  
## <a name="to-browse-data-or-change-sampling-options"></a>Per esplorare i dati o modificare le opzioni di campionamento  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]aprire il progetto o connettersi al database contenente la vista origine dati in cui si desidera esplorare i dati.  
  
2.  In Esplora soluzioni espandere la cartella **Viste origine dati** , quindi fare doppio clic sulla vista origine dati.  
  
3.  Fare clic con il pulsante destro del mouse sulla tabella, sulla vista o sulla query denominata contenente i dati che si desidera visualizzare, quindi scegliere **Esplora dati**.  
  
     L'origine dati sottostante la tabella, vista o query denominata nella vista origine dati sono le query e i risultati vengono visualizzati nel **Esplora \<nome oggetto > tabella** scheda.  
  
4.  Nel **Esplora \<nome oggetto > tabella** sulla barra degli strumenti, fare clic su di **opzioni di campionamento** icona.  
  
     Verrà visualizzata la finestra di dialogo **Opzioni di esplorazione dati** . In tale finestra di dialogo è possibile specificare il metodo di campionamento (un numero di record inferiore o superiore alla dimensione di campionamento predefinita pari a 5000 righe) o il conteggio campione.  
  
5.  Fare clic su **OK** o **Annulla** , a seconda dei casi.  
  
6.  Per ricampionare i dati, fare clic su **Ricampiona dati** sul **Esplora \<nome oggetto > tabella** sulla barra degli strumenti.  
  
## <a name="see-also"></a>Vedere anche  
 [Viste origine dati in modelli multidimensionali](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)  
  
  
