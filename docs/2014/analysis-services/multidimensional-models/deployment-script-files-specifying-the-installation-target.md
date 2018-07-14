---
title: Impostazione della destinazione di installazione | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- input files [Analysis Services]
- installation targets [Analysis Services]
- Analysis Services deployments, installation targets
- Analysis Services Deployment Wizard, installation targets
- deploying [Analysis Services], installation targets
- modifying installation targets
ms.assetid: cb706817-6f63-4771-92c3-b70030bbce3d
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a779e6ecbc32316d6d22ef8f270d9d0d2af6738e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37254953"
---
# <a name="specifying-the-installation-target"></a>Impostazione della destinazione di installazione
  Il [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] distribuzione guidata di legge le informazioni sulla destinazione di installazione dal \< *nome del progetto*>. deploymenttargets file. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] crea questo file quando si compila il progetto [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] Usa il database e server specificati nella **distribuzione** pagina della  *\<nome progetto >* **le pagine delle proprietà** finestra di dialogo per creare la \< *nome progetto*> file con estensione targets.  
  
## <a name="modifying-the-installation-target-for-deployment"></a>Modifica della destinazione di installazione per la distribuzione  
 In alcuni casi potrebbe essere necessario distribuire un progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] su un database o un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] diversi da quelli specificati nella pagina **Distribuzione** . Potrebbe essere utile ad esempio distribuire il progetto su un server di prova prima della distribuzione e successivamente distribuire il progetto su un server di produzione dopo il completamento delle prove. Quando il progetto è completato e testato, potrebbe essere opportuno distribuirlo su più server di produzione in un cluster con bilanciamento del carico di rete o su un server dell'area di gestione temporanea e un server di produzione.  
  
 Per distribuire un progetto [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] su un database o un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] diversi, è possibile modificare la destinazione di installazione nel file di input utilizzando uno dei metodi descritti nella procedura seguente.  
  
#### <a name="to-change-the-installation-target-after-the-input-files-have-been-generated"></a>Per modificare la destinazione di installazione dopo la generazione dei file di input.  
  
-   Eseguire Distribuzione guidata di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in modo interattivo. Nella pagina **Destinazione installazione** , specificare una nuova destinazione per il database e l'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
     -oppure-  
  
-   Eseguire Distribuzione guidata di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] attraverso il prompt dei comandi e impostarla in modo che venga eseguita in modalità file di risposte. Per altre informazioni sulla modalità file di risposte, vedere [Esecuzione della Distribuzione guidata Analysis Services](running-the-analysis-services-deployment-wizard.md).  
  
     -oppure-  
  
-   Modificare il \< *nome progetto*> file. deploymenttargets utilizzando un editor di testo.  
  
## <a name="see-also"></a>Vedere anche  
 [Impostazione opzioni di distribuzione dei ruoli e delle partizioni](deployment-script-files-partition-and-role-deployment-options.md)   
 [Specificare le impostazioni di configurazione per la distribuzione della soluzione](deployment-script-files-solution-deployment-config-settings.md)   
 [Impostazione delle opzioni di elaborazione](deployment-script-files-specifying-processing-options.md)  
  
  
