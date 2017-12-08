---
title: Creare e gestire prospettive (SSAS tabulare) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.asvs.bidtoolset.perspectivedb.f1
ms.assetid: 2a411c2b-2820-4086-ad7f-ce6a941fefc7
caps.latest.revision: "17"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 37228aace939d68a3e97e9b818a8cffe62b7632a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="create-and-manage-perspectives-ssas-tabular"></a>Creare e gestire prospettive (SSAS tabulare)
  Le prospettive consentono di definire subset visualizzabili di un modello in grado di offrire punti di vista mirati, specifici di un'attività aziendale o di un'applicazione del modello. Nelle attività di questo argomento vengono descritte le modalità di creazione e gestione delle prospettive tramite la finestra di dialogo **Prospettive** in Progettazione modelli.  
  
 In questo argomento sono incluse le attività seguenti:  
  
-   [Per aggiungere una prospettiva](#bkmk_add)  
  
-   [Per modificare una prospettiva](#bkmk_edit)  
  
-   [Per rinominare una prospettiva](#bkmk_rename)  
  
-   [Per eliminare una prospettiva](#bkmk_delete)  
  
-   [Per copiare una prospettiva](#bkmk_copy)  
  
## <a name="tasks"></a>Attività  
 Per creare prospettive si utilizzerà la finestra di dialogo **Prospettive** in cui è possibile aggiungere, modificare, eliminare, copiare e visualizzare prospettive. Per visualizzare la finestra di dialogo **Prospettive** , in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]fare clic sul menu **Modello** , quindi scegliere **Prospettive**.  
  
###  <a name="bkmk_add"></a> Per aggiungere una prospettiva  
  
-   Per aggiungere una nuova prospettiva, fare clic su **Nuova prospettiva**. È possibile selezionare e deselezionare gli oggetti campo da includere e fornire un nome per la nuova prospettiva.  
  
     Se si crea una prospettiva vuota con tutti i campi dell'oggetto campo, un utente che utilizza questa prospettiva visualizzerà un elenco di campi vuoto. Le prospettive devono contenere almeno una tabella e una colonna.  
  
###  <a name="bkmk_edit"></a> Per modificare una prospettiva  
  
-   Per modificare una prospettiva, selezionare e deselezionare i campi nella colonna della prospettiva. In questo modo verranno aggiunti e rimossi oggetti campo dalla prospettiva.  
  
###  <a name="bkmk_rename"></a> Per rinominare una prospettiva  
  
-   Quando si passa il mouse sull'intestazione di colonna (nome della prospettiva) di una prospettiva, viene visualizzato il pulsante **Rinomina** . Per rinominare la prospettiva, fare clic su **Rinomina**, quindi immettere un nuovo nome o modificare quello esistente.  
  
###  <a name="bkmk_delete"></a> Per eliminare una prospettiva  
  
-   Quando si passa il mouse sull'intestazione di colonna (nome della prospettiva) di una prospettiva, viene visualizzato il pulsante **Elimina** . Per eliminare la prospettiva, fare clic sul pulsante **Elimina** , quindi scegliere **Sì** nella finestra di conferma.  
  
###  <a name="bkmk_copy"></a> Per copiare una prospettiva  
  
-   Quando si passa il mouse sull'intestazione di colonna di una prospettiva, viene visualizzato il pulsante **Copia** . Per creare una copia di tale prospettiva, fare clic sul pulsante **Copia** . Una copia della prospettiva selezionata viene aggiunta come nuova prospettiva a destra delle prospettive esistenti. Il nome della nuova prospettiva viene ereditato dalla prospettiva copiata e alla fine del nome viene accodata un'annotazione *- Copy* . Ad esempio, se viene creata una copia della prospettiva *Vendite* , la nuova prospettiva viene denominata *Vendite - Copia*.  
  
## <a name="see-also"></a>Vedere anche  
 [Prospettive &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [Gerarchie &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/hierarchies-ssas-tabular.md)  
  
  
