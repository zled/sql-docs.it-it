---
title: "Creazione di un&#39;utilit&#224; di distribuzione | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "distribuzione di pacchetti [Integration Services], utilità di distribuzione"
  - "utilità di distribuzione [Integration Services]"
ms.assetid: 354322a4-ae8c-4d92-8e71-42d29dbd0614
caps.latest.revision: 50
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 50
---
# Creazione di un&#39;utilit&#224; di distribuzione
  Il primo passaggio della distribuzione di pacchetti consiste nel creare un'utilità di distribuzione per un progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. L'utilità di distribuzione è una cartella contenente i file necessari per la distribuzione dei pacchetti di un progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] in un altro server. L'utilità di distribuzione viene creata nel computer in cui è archiviato il progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 Per creare l'utilità di distribuzione di pacchetti per un progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], è innanzitutto necessario configurare il processo di compilazione dell'utilità e quindi compilare il progetto. Quando si compila il progetto, tutti i pacchetti e le configurazioni di pacchetto del progetto vengono inclusi automaticamente. Per distribuire file aggiuntivi, ad esempio un file Leggimi per il progetto, è necessario inserirli nella cartella **Varie** del progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Quando si compila il progetto, vengono inclusi automaticamente anche questi file.  
  
 È possibile configurare ogni utilità di distribuzione di progetto in modo diverso. Prima di compilare il progetto e creare l'utilità di distribuzione dei pacchetti, è possibile impostare le proprietà dell'utilità in modo da personalizzare la modalità di distribuzione dei pacchetti. È possibile, ad esempio, specificare se le configurazioni di pacchetto possono essere aggiornate in fase di distribuzione del progetto. Per accedere alle proprietà di un progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], fare clic con il pulsante destro del mouse sul progetto e quindi scegliere **Proprietà**.  
  
 Nella tabella seguente vengono descritte le proprietà dell'utilità di distribuzione.  
  
|Proprietà|Description|  
|--------------|-----------------|  
|AllowConfigurationChange|Valore che specifica se le configurazioni possono essere aggiornate durante la distribuzione.|  
|CreateDeploymentUtility|Valore che specifica se in fase di compilazione del progetto viene creata un'utilità di distribuzione di pacchetti. Per creare un'utilità di distribuzione, la proprietà deve essere impostata su **True**.|  
|DeploymentOutputPath|Posizione relativa al progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dell'utilità di distribuzione.|  
  
 Quando si compila un progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], viene creato un file manifesto, \<nome progetto>.SSISDeploymentManifest.xml, il quale viene aggiunto insieme a copie dei pacchetti di progetto e delle dipendenze di pacchetto nella cartella bin\Deployment del progetto o nel percorso specificato nella proprietà DeploymentOutputPath. Nel file manifesto sono elencati i pacchetti, le configurazioni di pacchetto ed eventuali altri file del progetto.  
  
 Il contenuto della cartella di distribuzione viene aggiornato ogni volta che si compila il progetto. Tutti i file eventualmente salvati in tale cartella e che non vengono nuovamente copiati nella cartella dal processo di compilazione verranno pertanto eliminati. Ad esempio, i file di configurazione del pacchetto salvati nelle cartelle di distribuzione verranno eliminati.  
  
### Per creare un'utilità di distribuzione di pacchetti  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] aprire la soluzione contenente il progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] per il quale si desidera creare un'utilità di distribuzione di pacchetti.  
  
2.  Fare clic con il pulsante destro del mouse sul progetto e quindi scegliere **Proprietà**.  
  
3.  Nella finestra di dialogo **Pagine delle proprietà di \<nome progetto>** fare clic su **Utilità di distribuzione**.  
  
4.  Per aggiornare le configurazioni di pacchetto in fase di distribuzione del pacchetto, impostare **AllowConfigurationChanges** su **True**.  
  
5.  Impostare **CreateDeploymentUtility** su **True**.  
  
6.  Facoltativamente, aggiornare la posizione dell'utilità di distribuzione modificando la proprietà **DeploymentOutputPath**.  
  
7.  Scegliere **OK**.  
  
8.  In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e quindi scegliere **Compila**.  
  
9. Nella finestra **Output** vengono visualizzati lo stato del processo di compilazione e gli eventuali errori di compilazione.  
  
## Vedere anche  
 [Configurazioni di pacchetto](../../integration-services/packages/package-configurations.md)   
 [Creazione di configurazioni dei pacchetti](../../integration-services/packages/create-package-configurations.md)   
 [Distribuzione di pacchetti con l'utilità di distribuzione](../../integration-services/packages/deploy-packages-by-using-the-deployment-utility.md)   
 [Distribuzione del pacchetto legacy &#40;SSIS&#41;](../../integration-services/packages/legacy-package-deployment-ssis.md)  
  
  