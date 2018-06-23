---
title: Modificare un avviso dati nella finestra di progettazione di avvisi| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editing, data alerts
- updating, data alerts
- editing, alerts
- updating, alerts
ms.assetid: dde3664d-90b5-4b12-969e-39152c86e58a
caps.latest.revision: 10
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: f5c9314b2dca029341c4ea503e6417a5e9c2507d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36168248"
---
# <a name="edit-a-data-alert-in-alert-designer"></a>Modificare un avviso dati nella finestra di progettazione di avvisi
  È possibile aprire una definizione di avviso dati da modificare tramite Gestione avvisi dati. La definizione di avviso può essere modificata solo dall'utente che l'ha creata. Per altre informazioni sull'apertura di gestione avvisi dati, vedere [Gestire gli avvisi dati in Gestione avvisi dati](manage-my-data-alerts-in-data-alert-manager.md).  
  
 Nella figura seguente è illustrato il menu di scelta rapida per un avviso dati in Gestione avvisi dati.  
  
 ![Aprire la finestra di progettazione Avviso dati facendo clic su Modifica](media/rs-alertmanageriwopendesigner.gif "Aprire la finestra di progettazione Avviso dati facendo clic su Modifica")  
  
 Nella procedura seguente sono inclusi i passaggi per aprire la definizione di avviso per la modifica nella finestra di progettazione Avviso dati di Gestione avvisi dati.  
  
### <a name="to-edit-a-data-alert-definition-in-data-alert-designer"></a>Per modificare una definizione di avviso in Gestione avvisi dati  
  
1.  In Gestione avvisi dati fare clic con il pulsante destro del mouse sulla definizione di avviso dati che si desidera modificare, quindi scegliere **Modifica**.  
  
     La definizione di avviso viene aperta in Gestione avvisi dati.  
  
2.  Aggiornare le regole e le impostazioni di pianificazione e di posta elettronica. Per altre informazioni, vedere [finestra di progettazione avviso dati](../../2014/reporting-services/data-alert-designer.md) e [creare un avviso di dati di progettazione avviso dati](create-a-data-alert-in-data-alert-designer.md).  
  
    > [!NOTE]  
    >  Non è possibile scegliere un feed di dati diverso. Per utilizzare un feed di dati diverso, è necessario creare una nuova definizione di avviso dati.  
  
3.  Fare clic su **Salva**.  
  
    > [!NOTE]  
    >  Se il report è cambiato e i feed di dati generati dal report sono cambiati, la definizione di avviso potrebbe non essere più valida. Questa condizione si verifica quando una colonna, a cui fa riferimento la definizione di avviso nelle regole, viene eliminata dal report, quando il tipo di dati contenuto in tale colonna viene modificato oppure quando il report viene eliminato o spostato. È possibile aprire una definizione di avviso che non è valida, ma non è possibile salvarla di nuovo fino a quando non diventa valida in base alla versione corrente del feed di dati del report in base a cui è compilata. Per altre informazioni sulla modalità di generazione di feed di dati dai report, vedere [Generazione di feed di dati dai report &#40;Generatore report e SSRS&#41;](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione avvisi dati per gli amministratori di avvisi](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md)   
 [Avvisi dati di Reporting Services](../ssms/agent/alerts.md)  
  
  