---
title: Specifica opzioni di distribuzione di ruoli e partizioni | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 01cab4f372335ddeb2f3798b635b661c5469b43c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="deployment-script-files---partition-and-role-deployment-options"></a>File di Script di distribuzione - opzioni di distribuzione di ruoli e partizioni
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  Il [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] distribuzione guidata di legge le opzioni di distribuzione di ruoli e delle partizioni dal \< *nome progetto*>. deploymentoptions. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]tale file viene creato quando si compila il [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] progetto. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] utilizza le opzioni di distribuzione di ruoli e delle partizioni dell'oggetto corrente progetto quando il \< *nome progetto*>. deploymentoptions viene creato. Per altre informazioni sulle impostazioni di configurazione, vedere [Informazioni sui file di input utilizzati per creare uno script di distribuzione](../../analysis-services/multidimensional-models/deployment-script-files-input-used-to-create-deployment-script.md).  
  
## <a name="reviewing-the-partition-and-role-deployment-options"></a>Esame delle opzioni di distribuzione dei ruoli e delle partizioni  
 Le opzioni di \< *nome progetto*>. deploymentoptions includono quanto segue:  
  
 **Opzioni di distribuzione delle partizioni**  
 Il \< *nome progetto*>. deploymentoptions specifica se le partizioni esistenti nel database di destinazione vengono mantenute o vengono sovrascritte (impostazione predefinita). Se le partizioni esistenti vengono mantenute, verranno distribuite solo le nuove partizioni, e le partizioni e le progettazioni delle aggregazioni in tutti i gruppi di misure esistenti non saranno modificate.  
  
> [!NOTE]  
>  Se il gruppo di misure contenente la partizione viene eliminato, la partizione viene eliminata automaticamente.  
  
 **Opzioni di distribuzione dei ruoli**  
 Il \< *nome progetto*>. deploymentoptions specifica una delle seguenti opzioni di distribuzione ruolo:  
  
-   I ruoli e i membri di ruolo esistenti contenuti nel database di destinazione vengono mantenuti e vengono distribuiti solo i nuovi ruoli e membri di ruolo.  
  
-   Tutti i membri e ruoli esistenti contenuti nel database di destinazione vengono sostituiti dai ruoli e dai membri distribuiti.  
  
-   I ruoli e i membri di ruolo esistenti contenuti nel database di destinazione vengono mantenuti e non viene distribuito nessun nuovo ruolo.  
  
-   **Nota** Quando vengono mantenuti i ruoli e i membri esistenti, le autorizzazioni associate a tali ruoli vengono reimpostate su nessuna autorizzazione. Le autorizzazioni di sicurezza sono contenute negli oggetti da esse protetti, non nei ruoli di sicurezza a cui sono associate. Per ulteriori informazioni su come gestire tale comportamento utilizzando la Distribuzione guidata Analysis Services, vedere "Mantieni ruoli e membri" nella Microsoft Knowledge Base.  
  
## <a name="modifying-the-partition-and-role-deployment-options"></a>Modifica delle opzioni di distribuzione dei ruoli e delle partizioni  
 È possibile distribuire il [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] progetto utilizzando opzioni per ruoli e partizioni diverse da quelle archiviate nel \< *nome progetto*>. deploymentoptions. Ad esempio, si desidera mantenere le partizioni esistenti, i ruoli e i membri del ruolo, invece che sostituire tutte le partizioni esistenti, i ruoli e membri come indicato nella \< *nome progetto*>. deploymentoptions.  
  
 Per modificare la distribuzione di partizioni e ruoli in un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] progetto, è possibile modificare le impostazioni di partizioni e dei ruoli all'interno del progetto poiché il  *\<nome progetto >* **pagine delle proprietà**  nella finestra di dialogo [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] queste opzioni non sono visualizzate. Se si desidera modificare le opzioni di distribuzione per i ruoli e partizioni, è necessario modificare queste informazioni all'interno di \< *nome progetto*>. deploymentoptions stesso. La procedura seguente viene descritto come modificare le opzioni di distribuzione di ruoli e delle partizioni all'interno di \< *nome progetto*>. deploymentoptions.  
  
#### <a name="to-change-the-deployment-of-partitions-or-roles-after-the-input-files-have-been-generated"></a>Per modificare la distribuzione delle partizioni o dei ruoli dopo la generazione dei file di input  
  
-   Eseguire Distribuzione guidata di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in modo interattivo e specificare nuove opzioni di distribuzione delle partizioni e dei ruoli nella pagina relativa alle **opzioni partizioni e ruoli della distribuzione** .  
  
     -oppure-  
  
-   Eseguire Distribuzione guidata di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] attraverso il prompt dei comandi e impostarla in modo che venga eseguita in modalità file di risposte. Per altre informazioni sulla modalità file di risposte, vedere [Esecuzione della Distribuzione guidata Analysis Services](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md).  
  
     -oppure-  
  
-   Aprire il \< *nome progetto*>. deploymentoptions in un editor di testo e manualmente modificare le opzioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Specifica la destinazione di installazione](../../analysis-services/multidimensional-models/deployment-script-files-specifying-the-installation-target.md)   
 [Specificare le impostazioni di configurazione per la distribuzione della soluzione](../../analysis-services/multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)   
 [Specifica le opzioni di elaborazione](../../analysis-services/multidimensional-models/deployment-script-files-specifying-processing-options.md)  
  
  
