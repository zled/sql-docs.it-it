---
title: Finestra di dialogo Importa criteri | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.dmf.importpolicy.f1
ms.assetid: 78ab5f6e-2f13-4788-937e-8892ef4e2345
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1d8bcdd179434c273c37ce2bb6a00d53ea7c75b0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067364"
---
# <a name="import-policies-dialog-box"></a>Finestra di dialogo Importa criteri
  Utilizzare questa finestra di dialogo per importare nell'istanza corrente del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] i criteri salvati come file XML e le relative condizioni di riferimento.  
  
## <a name="options"></a>Opzioni  
 **File da importare**  
 Per importare i criteri da un file XML, digitare il percorso e il nome del file oppure usare il pulsante Sfoglia (**...**).  
  
 **Sostituisci duplicati con gli elementi importati**  
 Selezionare questa opzione per sovrascrivere eventuali criteri o condizioni con lo stesso nome che esistono già nell'istanza corrente del [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Non è possibile sovrascrivere una condizione con criteri dipendenti, a meno che non vengano sovrascritti anche questi ultimi. Se questa opzione non viene selezionata, una condizione esistente che utilizza la stessa espressione di condizione non genererà un errore.  
  
 **Stato criteri**  
 Consente di selezionare lo stato desiderato per i criteri importati:  
  
-   **Mantieni lo stato dei criteri durante l'importazione**  
  
-   **Abilita tutti i criteri durante l'importazione**  
  
-   **Disabilita tutti i criteri durante l'importazione**  
  
## <a name="see-also"></a>Vedere anche  
 [Amministrazione di server tramite la gestione basata su criteri](administer-servers-by-using-policy-based-management.md)   
 [Importare i criteri della gestione basata su criteri](import-a-policy-based-management-policy.md)   
 [Esportare i criteri della gestione basata su criteri](export-a-policy-based-management-policy.md)  
  
  