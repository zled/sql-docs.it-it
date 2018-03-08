---
title: Creare e gestire ruoli | Documenti Microsoft
ms.custom: 
ms.date: 02/22/2018
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.asvs.bidtoolset.rolemanager.f1
- sql13.asvs.bidtoolset.roledb.f1
ms.assetid: e23d27a8-e968-4082-9dbe-963fc724b5d9
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3787b8a3ee01c11cddb302025e2370085d0c63db
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/23/2018
---
# <a name="create-and-manage-roles"></a>Creare e gestire ruoli 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
I ruoli, nei modelli tabulari, consentono di definire le autorizzazioni dei membri per un modello. I ruoli vengono definiti per un progetto di modello tramite la finestra di dialogo Gestione ruoli di [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Quando viene distribuito un modello, gli amministratori del database possono gestire i ruoli tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 L'attività in questo articolo viene descritto come creare e gestire i ruoli durante la creazione di modelli tramite la finestra di dialogo Gestione ruoli in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Per informazioni sulla gestione dei ruoli in un database modello distribuito, vedere [ruoli nei modelli tabulari](../../analysis-services/tabular-models/tabular-model-roles-ssas-tabular.md).  
  
## <a name="tasks"></a>Attività  
 Per creare, modificare, copiare ed eliminare ruoli, usare la finestra di dialogo **Gestione ruoli** . Per visualizzare la finestra di dialogo **Gestione ruoli** di [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], fare clic sul menu **Modello** e quindi su **Gestione ruoli**.  
  
###  <a name="bkmk_new_role"></a> Per creare un nuovo ruolo  
  
1.  In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]fare clic sul menu **Modello** e quindi su **Gestione ruoli**.  
  
2.  Nella finestra di dialogo **Gestione ruoli** fare clic su **Nuovo**.  
  
     All'elenco Ruoli verrà aggiunto un nuovo ruolo evidenziato.  
  
3.  Nel campo **Nome** dell'elenco **Ruoli** digitare un nome per il ruolo.  
  
     Per impostazione predefinita, il nome del ruolo predefinito sarà numerato in modo incrementale per ogni nuovo ruolo. È consigliabile digitare un nome che consente di identificare chiaramente il tipo di membro, ad esempio Responsabili finanze o Esperti di risorse umane.  
  
4.  Nel campo **Autorizzazioni** fare clic sulla freccia GIÙ e quindi selezionare uno dei tipi di autorizzazioni seguenti:  
  
    |Autorizzazione|Description|  
    |----------------|-----------------|  
    |**Nessuno**|I membri non possono apportare alcuna modifica allo schema del modello, né eseguire query sui dati.|  
    |**Lettura**|I membri possono eseguire query sui dati in base ai filtri di riga, ma non possono apportare alcuna modifica allo schema del modello.|  
    |**Lettura ed elaborazione**|I membri possono eseguire query sui dati in base ai filtri a livello di riga ed effettuare le operazioni relative alle opzioni Elabora ed Elabora tutto, ma non possono apportare alcuna modifica allo schema del modello.|  
    |**Process**|I membri possono effettuare le operazioni relative alle opzioni Elabora ed Elabora tutto, ma non possono modificare lo schema del modello, né eseguire query sui dati.|  
    |**Amministratore**|I membri possono apportare modifiche allo schema del modello ed eseguire query su tutti i dati.|  
  
5.  Per immettere una descrizione per il ruolo, fare clic sul campo **Descrizione** e quindi digitare una descrizione.  
  
6.  Se il ruolo in fase di creazione dispone dell'autorizzazione Lettura o di lettura ed elaborazione, è possibile aggiungere filtri di riga utilizzando una formula DAX. Per aggiungere filtri di riga, fare clic sulla scheda **Filtri di riga** , selezionare una tabella, fare clic sul campo **Filtro DAX** e quindi digitare una formula DAX.  
  
7.  Per aggiungere membri al ruolo, fare clic sulla scheda **Membri** e quindi fare clic su **Aggiungi**.  
  
    > [!NOTE]  
    >  I membri dei ruoli possono anche essere aggiunti a un modello distribuito tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Per ulteriori informazioni, vedere [gestire ruoli tramite SSMS](../../analysis-services/tabular-models/manage-roles-by-using-ssms-ssas-tabular.md).  
  
8.  Nella finestra di dialogo **Selezione utenti o gruppi** immettere oggetti utente o gruppo di Windows come membri.  
  
9. Scegliere **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Ruoli](../../analysis-services/tabular-models/roles-ssas-tabular.md)   
 [Prospettive](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [Analizza in Excel](../../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md)   
 [Funzione USERNAME (DAX)](http://msdn.microsoft.com/en-us/22dddc4b-1648-4c89-8c93-f1151162b93f)   
 [Funzione CUSTOMDATA (DAX)](http://msdn.microsoft.com/en-us/58235ad8-226c-43cc-8a69-5a52ac19dd4e)  
  
  
