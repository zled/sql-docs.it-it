---
title: Concedere le autorizzazioni per strutture di data mining e modelli (Analysis Services) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.roledesignerdialog.miningmodels.f1
helpviewer_keywords:
- data mining [Analysis Services], security
- permissions [Analysis Services], mining models
- mining models [Analysis Services], security
- mining structures [Analysis Services], security
- permissions [Analysis Services], mining structures
- user access rights [Analysis Services], mining structures
- user access rights [Analysis Services], mining models
ms.assetid: a0008004-e2b7-47db-acad-5fe7e12b130f
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5558e0ca08d13a5f746eb4694fdafc271e49df9a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36054654"
---
# <a name="grant-permissions-on-data-mining-structures-and-models-analysis-services"></a>Concedere le autorizzazioni per le strutture e i modelli di data mining (Analysis Services)
  Per impostazione predefinita, solo un amministratore del server di Analysis Services dispone delle autorizzazioni per visualizzare strutture di data mining o modelli di data mining nel database. Seguire le istruzioni riportate di seguito per concedere le autorizzazioni agli utenti non amministratori.  
  
## <a name="set-permissions-to-access-a-mining-structure"></a>Impostare le autorizzazioni per accedere a una struttura di data mining  
  
1.  In SSMS connettersi ad Analysis Services. Se è necessaria assistenza per la procedura, vedere [Connettersi dalle applicazioni client &#40;Analysis Services&#41;](../instances/connect-from-client-applications-analysis-services.md).  
  
2.  Aprire la cartella **Database** e selezionare un database in Esplora oggetti.  
  
3.  Fare clic con il pulsante destro del mouse su **Ruoli** e scegliere **Nuovo ruolo**.  
  
4.  Nella pagina Generale immettere un nome e, se si vuole, una descrizione. Questa pagina contiene anche diverse autorizzazioni per il database quali Controllo completo, Elaborazione database e Lettura definizione. Nessuna di tali autorizzazioni è necessaria per l'accesso al data mining. Per altre informazioni sulle autorizzazioni per il database, vedere [Concedere autorizzazioni per il database &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md).  
  
5.  Nel riquadro **Struttura di data mining** selezionare **Lettura** o **Lettura/Scrittura** per ogni struttura di data mining.  
  
6.  Nel riquadro **Appartenenza** immettere gli account utente e di gruppo di Windows che si connettono ad Analysis Services con questo ruolo.  
  
7.  Fare clic su **OK** per completare la creazione del ruolo.  
  
## <a name="set-permissions-to-access-a-mining-model"></a>Impostare le autorizzazione per accedere a un modello di data mining  
 Un ruolo per un modello di data mining può disporre di autorizzazioni di **Lettura** o **Lettura/Scrittura** , nonché di autorizzazioni di **Drill-through** e **Lettura definizione** che consentono di visualizzare ed esplorare i dati sottostanti.  
  
 **Nota** Se si abilita il drill-through nella struttura di data mining e nel modello di data mining, qualsiasi utente membro di un ruolo con autorizzazioni drill-through per il modello di data mining e per la struttura di data mining può anche visualizzare le colonne nella struttura di data mining, anche se tali colonne non sono incluse nel modello di data mining. Pertanto, per proteggere le informazioni riservate, è necessario configurare la vista origine dati per mascherare le informazioni personali e consentire l'accesso drill-through alla struttura di data mining solo quando necessario.  
  
 Per concedere autorizzazioni di lettura o lettura/scrittura a un ruolo del database, un utente deve essere membro del ruolo del server di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] oppure di un ruolo del database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] che disponga di autorizzazioni Controllo completo (amministratore).  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]connettersi all'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], espandere il nodo **Ruoli** per il database appropriato in Esplora oggetti e quindi fare clic su un ruolo del database oppure creare un nuovo ruolo del database.  
  
2.  Nel riquadro **Struttura di data mining** individuare il modello di data mining nell'elenco **Modelli di data mining** e quindi selezionare **Lettura**, **Lettura/Scrittura**, **Drill-through**o **Esplorazione** per il modello di data mining.  
  
3.  Nel riquadro **Appartenenza** immettere gli account utente e di gruppo di Windows che si connettono ad Analysis Services con questo ruolo.  
  
4.  Fare clic su **OK** per completare la creazione del ruolo.  
  
 Per usare un'origine dei dati in una query drill-through che usa la clausola OPENQUERY DMX (Data Mining Extensions), è necessario che il ruolo del database abbia anche l'autorizzazione di lettura/scrittura per l'oggetto origine dati appropriato. Per altre informazioni, vedere [Concedere le autorizzazioni per un oggetto origine dati &#40;Analysis Services&#41;](grant-permissions-on-a-data-source-object-analysis-services.md) e [OPENQUERY &#40;DMX&#41;](/sql/dmx/source-data-query-openquery).  
  
> [!NOTE]  
>  Per impostazione predefinita, l'invio delle query DMX tramite OPENROWSET è disabilitata.  
  
## <a name="see-also"></a>Vedere anche  
 [Concedere le autorizzazioni di amministratore del Server &#40;Analysis Services&#41;](../instances/grant-server-admin-rights-to-an-analysis-services-instance.md)   
 [Concedere le autorizzazioni del cubo o modello di &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md)   
 [Concedere l'accesso personalizzato ai dati della dimensione &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md)   
 [Concedere l'accesso personalizzato ai dati delle celle &#40;Analysis Services&#41;](grant-custom-access-to-cell-data-analysis-services.md)  
  
  
