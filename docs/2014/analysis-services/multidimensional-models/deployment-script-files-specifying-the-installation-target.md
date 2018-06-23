---
title: Specifica la destinazione di installazione | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- input files [Analysis Services]
- installation targets [Analysis Services]
- Analysis Services deployments, installation targets
- Analysis Services Deployment Wizard, installation targets
- deploying [Analysis Services], installation targets
- modifying installation targets
ms.assetid: cb706817-6f63-4771-92c3-b70030bbce3d
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 3e2f46eeb01baa5f6f208a612ecba5ad61dad004
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36166724"
---
# <a name="specifying-the-installation-target"></a>Impostazione della destinazione di installazione
  Il [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] distribuzione guidata di legge le informazioni sulla destinazione di installazione dal \< *nome progetto*>. deploymenttargets file. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] crea questo file quando si compila il progetto [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] utilizza il database e il server specificato nella **distribuzione** pagina del  *\<nome progetto >* **pagine delle proprietà** finestra di dialogo per creare la \< *nome del progetto*> file con estensione targets.  
  
## <a name="modifying-the-installation-target-for-deployment"></a>Modifica della destinazione di installazione per la distribuzione  
 In alcuni casi potrebbe essere necessario distribuire un progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] su un database o un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] diversi da quelli specificati nella pagina **Distribuzione** . Potrebbe essere utile ad esempio distribuire il progetto su un server di prova prima della distribuzione e successivamente distribuire il progetto su un server di produzione dopo il completamento delle prove. Quando il progetto è completato e testato, potrebbe essere opportuno distribuirlo su più server di produzione in un cluster con bilanciamento del carico di rete o su un server dell'area di gestione temporanea e un server di produzione.  
  
 Per distribuire un progetto [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] su un database o un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] diversi, è possibile modificare la destinazione di installazione nel file di input utilizzando uno dei metodi descritti nella procedura seguente.  
  
#### <a name="to-change-the-installation-target-after-the-input-files-have-been-generated"></a>Per modificare la destinazione di installazione dopo la generazione dei file di input.  
  
-   Eseguire Distribuzione guidata di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in modo interattivo. Nella pagina **Destinazione installazione** , specificare una nuova destinazione per il database e l'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
     -oppure-  
  
-   Eseguire Distribuzione guidata di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] attraverso il prompt dei comandi e impostarla in modo che venga eseguita in modalità file di risposte. Per altre informazioni sulla modalità file di risposte, vedere [Esecuzione della Distribuzione guidata Analysis Services](running-the-analysis-services-deployment-wizard.md).  
  
     -oppure-  
  
-   Modificare il \< *nome del progetto*>. deploymenttargets file utilizzando un editor di testo.  
  
## <a name="see-also"></a>Vedere anche  
 [Specifica delle opzioni di distribuzione di ruoli e partizioni](deployment-script-files-partition-and-role-deployment-options.md)   
 [Specificare le impostazioni di configurazione per la distribuzione della soluzione](deployment-script-files-solution-deployment-config-settings.md)   
 [Specifica le opzioni di elaborazione](deployment-script-files-specifying-processing-options.md)  
  
  