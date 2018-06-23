---
title: Creare e gestire ruoli (SSAS tabulare) | Documenti Microsoft
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
- sql12.asvs.bidtoolset.rolemanager.f1
- sql12.asvs.bidtoolset.roledb.f1
ms.assetid: e23d27a8-e968-4082-9dbe-963fc724b5d9
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: b1cc9692f7eb74cadb89b7b3a439600db775913b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36158297"
---
# <a name="create-and-manage-roles-ssas-tabular"></a>Creare e gestire ruoli (SSAS tabulare)
  I ruoli, nei modelli tabulari, consentono di definire le autorizzazioni dei membri per un modello. I ruoli vengono definiti per un progetto di modello tramite la finestra di dialogo Gestione ruoli di [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Quando viene distribuito un modello, gli amministratori del database possono gestire i ruoli tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Le attività di questo argomento descrivono come creare e gestire i ruoli durante la creazione di modelli tramite la finestra di dialogo Gestione ruoli in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Per altre informazioni sulla gestione dei ruoli in un database modello distribuito, vedere [Ruoli nei modelli tabulari &#40;SSAS Tabulare&#41;](roles-ssas-tabular.md).  
  
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
    >  I membri dei ruoli possono anche essere aggiunti a un modello distribuito tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Per altre informazioni, vedere [Gestire ruoli tramite SSMS &#40;SSAS tabulare&#41;](manage-roles-by-using-ssms-ssas-tabular.md).  
  
8.  Nella finestra di dialogo **Selezione utenti o gruppi** immettere oggetti utente o gruppo di Windows come membri.  
  
9. Scegliere **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Ruoli &#40;tabulare di SSAS&#41;](roles-ssas-tabular.md)   
 [Prospettive &#40;tabulare di SSAS&#41;](perspectives-ssas-tabular.md)   
 [Analizza in Excel &#40;tabulare di SSAS&#41;](analyze-in-excel-ssas-tabular.md)   
 [Funzione USERNAME &#40;DAX&#41;](https://msdn.microsoft.com/library/hh230954.aspx)   
 [Funzione CUSTOMDATA &#40;DAX&#41;](https://msdn.microsoft.com/library/hh213140.aspx)  
  
  