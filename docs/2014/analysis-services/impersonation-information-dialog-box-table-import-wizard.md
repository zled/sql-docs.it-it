---
title: Finestra di dialogo informazioni di rappresentazione (importazione guidata tabella) | Documenti Microsoft
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
- sql12.asvs.bidtoolset.impersonationinfo.f1
ms.assetid: bee7eee5-0650-41f1-a372-5076ae97a58c
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c53b71a06904bd3f898efa3dd2d9946670193845
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156588"
---
# <a name="impersonation-information-dialog-box-table-import-wizard"></a>Finestra di dialogo Impostazioni di rappresentazione (Importazione guidata tabella)
  Utilizzare la pagina **Impostazioni di rappresentazione** per specificare le credenziali che verranno utilizzate da [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] per la connessione all'origine dati. Per altre informazioni sulla rappresentazione delle credenziali, vedere [Impersonation &#40;SSAS Tabular&#41;](tabular-models/impersonation-ssas-tabular.md).  
  
## <a name="options"></a>Opzioni  
 **Specifica nome utente di Windows e password**  
 Selezionare questa opzione per fare in modo che le credenziali di sicurezza di un account utente di Windows specificato vengano utilizzate dal modello tabulare.  
  
 **Nome utente**  
 Digitare il dominio e il nome dell'account utente da utilizzare Utilizzare il formato seguente:  
  
 *\<Nome di dominio >* **\\**  *\<nome dell'account utente >*  
  
 Questa opzione è abilitata solo se si seleziona l'opzione **Usa nome utente e password specifici** .  
  
 **Password**  
 Digitare la password dell'account utente che verrà utilizzata dal modello tabulare.  
  
 Questa opzione è abilitata solo se si seleziona l'opzione **Usa nome utente e password specifici** .  
  
 **Account del servizio**  
 Selezionare questa opzione per usare le credenziali di sicurezza associate al servizio [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] tramite cui viene gestito il modello.  
  
## <a name="see-also"></a>Vedere anche  
 [Rappresentazione &#40;tabulare di SSAS&#41;](tabular-models/impersonation-ssas-tabular.md)  
  
  