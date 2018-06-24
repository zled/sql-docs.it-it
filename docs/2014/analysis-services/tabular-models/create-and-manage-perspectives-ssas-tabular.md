---
title: Creare e gestire prospettive (SSAS tabulare) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.bidtoolset.perspectivedb.f1
ms.assetid: 2a411c2b-2820-4086-ad7f-ce6a941fefc7
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 3d49d87c3cd5ff2b4ae68e485cfa9cc5afe31d6f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065207"
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
 [Prospettive &#40;tabulare di SSAS&#41;](perspectives-ssas-tabular.md)   
 [Gerarchie &#40;tabulare di SSAS&#41;](hierarchies-ssas-tabular.md)  
  
  