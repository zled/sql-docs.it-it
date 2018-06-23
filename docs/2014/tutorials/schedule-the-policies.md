---
title: Pianificazione criteri | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59417a54-55f1-4468-ba41-368aa852c2d4
caps.latest.revision: 5
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 99c6e3a4eacfea76ff16ea266d38f2087c088f33
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065496"
---
# <a name="schedule-the-policies"></a>Pianificazione criteri
  In questa attività verrà eseguita la pianificazione dei criteri per procedure consigliate importati nell'attività precedente.  
  
### <a name="to-schedule-the-best-practices-policies"></a>Per pianificare i criteri per procedure consigliate  
  
1.  In Esplora oggetti, espandere **Management**, espandere **gestione dei criteri**, espandere **criteri**, fare doppio clic su un migliori criteri per procedure consigliate e quindi fare clic su  **Proprietà**.  
  
    > [!NOTE]  
    >  In alternativa, per vedere facilmente quali criteri sono associati alle procedure consigliate e ordinare le categorie delle procedure consigliate, espandere **Management**, espandere **gestione dei criteri**, quindi fare clic su **Criteri**. Scegliere **Dettagli Esplora oggetti** dal menu **Visualizza**. Nel **dettagli Esplora oggetti** riquadro, fare clic sui **categoria** sull'intestazione per ordinare i criteri per categoria. I criteri consigliate hanno il prefisso **consigliate Microsoft**. Fare doppio clic sui criteri che si desidera configurare e quindi fare clic su **proprietà**.  
  
2.  Nel **generali** pagina del **Apri criteri** della finestra di dialogo il **modalità di valutazione** fare clic su **su pianificazione**.  
  
3.  Accanto ai **pianificazione** fare clic su **Pick** per specificare una pianificazione esistente oppure fare clic su **nuovo** per creare una nuova pianificazione.  
  
4.  Dopo aver configurato una pianificazione, è possibile selezionare il **Enabled** casella di controllo nella parte superiore della pagina per abilitare i criteri pianificati.  
  
5.  Ripetere i passaggi da 1 a 4 per tutti i criteri che si desidera pianificare.  
  
    > [!NOTE]  
    >  Per visualizzare i risultati di valutazione dopo l'esecuzione di criteri pianificati, aprire il log Cronologia criteri nell'istanza di destinazione. Per aprire il registro, fare doppio clic su **criteri di gestione**, quindi fare clic su **Visualizza cronologia**.  
  
## <a name="summary"></a>Riepilogo  
 I criteri pianificati sono stati configurati per essere eseguiti in un'istanza singola di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Se si desidera distribuire i criteri pianificati in più istanze, continuare con la prossima attività in questa esercitazione.  
  
## <a name="next-steps"></a>Passaggi successivi  
 [Distribuire criteri pianificati in più istanze](../../2014/tutorials/deploy-scheduled-policies-to-multiple-instances.md)  
  
  