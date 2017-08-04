---
title: Query di Data Mining | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.dataminingquery.f1
ms.assetid: 948e358a-6245-429f-82c7-4cedc5e048fd
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8809f1e5f91ad5746b66d4640747b1ec0a923f0f
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="data-mining-query"></a>Query di data mining
  Il riquadro di progettazione contiene il generatore delle query di stima di data mining che consente di compilare le query delle stime di data mining. È possibile progettare query di stima in base a tabelle di input o query di stima singleton. Passare alla visualizzazione dei risultati per eseguire la query e visualizzare i risultati. Nella visualizzazione Query viene visualizzata la query DMX (Data Mining Extensions) creata dal generatore delle query di stima.  
  
## <a name="options"></a>Opzioni  
 Pulsante Cambia visualizzazione  
 Fare clic su un'icona per alternare il riquadro di progettazione al riquadro Query. Per impostazione predefinita è aperto il riquadro di progettazione.  
  
 Per passare al riquadro di progettazione, scegliere il ![icona progettazione](../../integration-services/control-flow/media/ssis-designicon.gif "icona progettazione") icona.  
  
 Per passare al riquadro query, scegliere il ![icona SQL](../../integration-services/control-flow/media/ssis-queryicon.gif "icona SQL") icona.  
  
 **Modello di data mining**  
 Consente di visualizzare il modello di data mining selezionato sul quale si desidera basare le stime.  
  
 **Seleziona modello**  
 Consente di aprire la finestra di dialogo **Seleziona modello di data mining** .  
  
 **Colonne di input**  
 Consente di visualizzare le colonne di input selezionate per la generazione delle stime.  
  
 **Origine**  
 Consente di selezionare l'origine contenente il campo che verrà utilizzato per la colonna nell'elenco a discesa. È possibile usare il modello di data mining selezionato nella tabella **Modello di data mining** , la tabella o le tabelle di input selezionate nella tabella **Seleziona tabella/e di input** , una funzione di stima o un'espressione personalizzata.  
  
 È possibile trascinare le colonne dalle tabelle contenenti il modello di data mining e dalle tabelle di input sulla cella.  
  
 **Campo**  
 Consente di selezionare una colonna nell'elenco di colonne derivato dalla tabella di origine. Se è stata selezionata l'opzione **Funzione di stima** in **Origine**, la cella conterrà un elenco a discesa delle funzioni di stima disponibili per il modello di data mining selezionato.  
  
 **Alias**  
 Il nome della colonna restituito dal server.  
  
 **Visualizza**  
 Selezionare questa opzione per restituire la colonna o per utilizzarla solo nella clausola WHERE.  
  
 **Gruppo**  
 Usare questa opzione con la colonna **And/Or** per raggruppare le espressioni. Ad esempio, (espr1 OR espr2) AND espr3.  
  
 **And/Or**  
 Utilizzare questa opzione per creare una query logica. Ad esempio, (espr1 OR espr2) AND espr3.  
  
 **Criteri/Argomento**  
 Consente di specificare una condizione o un'espressione utente da applicare a una colonna. È possibile trascinare le colonne dalle tabelle contenenti il modello di data mining e dalle tabelle di input sulla cella.  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti query di data mining](../../analysis-services/data-mining/data-mining-query-tools.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento istruzione](../../dmx/data-mining-extensions-dmx-statements.md)  
  
  
