---
title: 'Procedura: eseguire il Debug di assembly personalizzati | Documenti Microsoft'
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom assemblies [Reporting Services], debugging
- debugging custom assemblies [Reporting Services]
- troubleshooting [Reporting Services], custom assemblies
ms.assetid: 3a3215b3-548c-4474-81ba-3a98dd3912bf
caps.latest.revision: 44
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: b6cdc41f90765a3fc1a568bc76ddf0d41c15b38a
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="how-to-debug-custom-assemblies"></a>Procedura: Debug di assembly personalizzati
  Il [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] disponibili diversi strumenti di debug che consentono di analizzano il codice assembly personalizzato e individuare gli errori. Per ogni attività specifica è disponibile uno strumento appropriato. In questo esempio viene utilizzato [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)].  
  
 Il modo migliore per progettare, sviluppare e testare assembly personalizzati per [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] consiste nel creare una soluzione che contiene sia i report di test che l'assembly personalizzato.  
  
### <a name="to-debug-assemblies-using-a-single-instance-of-visual-studio"></a>Per eseguire il debug di assembly utilizzando un'unica istanza di Visual Studio  
  
1.  Creare un nuovo progetto report utilizzando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
     Quando viene creato un progetto report, in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] viene creata anche una soluzione che lo contenga.  
  
2.  Aggiungere un nuovo progetto Libreria di classi alla soluzione esistente. Verificare che il progetto report venga impostato come progetto di avvio. Per ulteriori informazioni sull'esecuzione di questa operazione, vedere la documentazione di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
3.  Selezionare la soluzione in Esplora soluzioni.  
  
4.  Nel **vista** menu, fare clic su **pagine delle proprietà**.  
  
     Il **pagine proprietà soluzione** verrà visualizzata la finestra di dialogo.  
  
5.  Nel riquadro sinistro, espandere **proprietà comuni** se necessario, fare clic su **dipendenze progetto**. Selezionare il progetto report dal **progetto** elenco a discesa. Selezionare il progetto assembly il **dipende** elenco.  
  
6.  Fare clic su **OK** per salvare le modifiche e chiudere il **pagine delle proprietà** finestra di dialogo.  
  
7.  In Esplora soluzioni selezionare il progetto assembly personalizzato.  
  
8.  Nel **vista** menu, fare clic su **pagine delle proprietà**.  
  
     Il **pagine delle proprietà del progetto** verrà visualizzata la finestra di dialogo.  
  
9. Fare clic sul **compilare** scheda in un progetto c# o **compilare** scheda se è attiva una [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] progetto.  
  
10. Nel **compilare**/**compilare** pagina, immettere il percorso della cartella di progettazione Report. Per impostazione predefinita, questo è C:\Program Files\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE) nei **percorso di Output** casella di testo. In tal modo verrà compilata e distribuita una versione aggiornata dell'assembly personalizzato direttamente in Progettazione report prima che il report venga eseguito.  
  
11. Dopo avere progettato il report e sviluppato l'assembly personalizzato, impostare i punti di interruzione nel codice assembly personalizzato.  
  
12. Eseguire il report in **DebugLocal** modalità premendo il tasto F5. Durante l'esecuzione del report nella finestra popup di anteprima, il debugger rileva tutti i punti di interruzione che corrispondono a codice eseguibile nell'assembly. Utilizzare F11 per passare al codice assembly personalizzato.  
  
### <a name="to-debug-assemblies-using-two-instances-of-visual-studio"></a>Per eseguire il debug di assembly utilizzando due istanze di Visual Studio  
  
1.  Avviare [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] e aprire il progetto assembly personalizzato.  
  
2.  Compilare il progetto e distribuire l'assembly personalizzato e il file pdb associato in Progettazione report. Per ulteriori informazioni sulla distribuzione, vedere [distribuzione di un Assembly personalizzato](../../reporting-services/custom-assemblies/deploying-a-custom-assembly.md).  
  
3.  Aprire un progetto report che utilizza l'assembly personalizzato lasciando il codice assembly personalizzato aperto in un'altra istanza di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
4.  Passare all'istanza di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] contenente il progetto assembly personalizzato e impostare alcuni punti di interruzione nel codice.  
  
5.  Con il progetto assembly personalizzato nella finestra attiva, fare clic su **Connetti a processo** sul **Debug** menu.  
  
     Il **Connetti a processo** verrà visualizzata la finestra di dialogo.  
  
6.  Nell'elenco dei processi, selezionare il processo devenv.exe che corrisponde al progetto Report e fare clic su **collegamento**.  
  
7.  Definire le espressioni che verranno utilizzate nel report dall'assembly personalizzato e progettare il report.  
  
8.  Al termine della progettazione del report, fare clic su di **anteprima** scheda.  
  
     Il report verrà eseguito. Il codice assembly personalizzato dovrebbe interrompersi in corrispondenza dei punti di interruzione definiti in precedenza.  
  
    > [!NOTE]  
    >  Utilizzo di **anteprima** scheda non impongono le autorizzazioni di codice per l'assembly. Per un test completo, che include eventuali errori di sicurezza di accesso di codice, avviare il progetto report sotto il **DebugLocal** impostazione di configurazione.  
  
9. Esaminare il codice istruzione per istruzione premendo F11 Per ulteriori informazioni sull'esecuzione del debug in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], vedere la documentazione di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di assembly personalizzati con i report](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
