---
title: I requisiti di implementazione di elemento di Report personalizzato | Documenti Microsoft
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
- custom report items
ms.assetid: cfacd816-00d6-4a3d-be72-1bba6f7f6886
caps.latest.revision: 22
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 43770b0b167e2a40874d1b8f31b3b146e62ec2b5
ms.contentlocale: it-it
ms.lasthandoff: 08/12/2017

---
# <a name="custom-report-item-implementation-requirements"></a>Requisiti per l'implementazione di elementi dei report personalizzati
  In questo argomento vengono illustrati i prerequisiti per lo sviluppo e la distribuzione di elementi dei report personalizzati.  
  
## <a name="development-and-deployment-requirements"></a>Requisiti relativi a sviluppo e distribuzione  
 Sviluppo di un elemento del report personalizzato per [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] richiede le seguenti condizioni:  
  
-   Accesso amministrativo a un server che esegue [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
-   [!INCLUDE[vsprvsext](../../includes/vsprvsext-md.md)]o versione successiva con il [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] software development kit SDK installato.  
  
-   Accesso alla documentazione di [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.  
  
-   Familiarità con le attività di creazione dei componenti e gli spazi dei nomi del modello di componente in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Per ulteriori informazioni, vedere gli argomenti relativi alla creazione di componenti e agli spazi dei nomi del modello di componente in Visual Studio nel sito msdn.microsoft.com.  
  
## <a name="language-and-namespace-requirements"></a>Requisiti relativi a linguaggio e spazio dei nomi  
 Gli elementi dei report personalizzati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] offrono supporto completo per [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. È possibile sviluppare elementi dei report personalizzati utilizzando un linguaggio di propria scelta conforme a .NET.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] offre allo sviluppatore numerosi strumenti e caratteristiche per semplificare e accelerare i cicli iterativi di codifica, di debug e test, nonché per semplificare la distribuzione. [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK include i compilatori [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] e C# e gli strumenti correlati.  
  
-   Elementi di report personalizzati utilizzano il **Microsoft.ReportDesigner** e <xref:Microsoft.ReportingServices.Interfaces> gli spazi dei nomi. Questi elementi sono archiviati negli assembly Microsoft.ReportingServices.Designer.DLL e Microsoft.ReportingServices.Interfaces.DLL, installati con [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
-   I componenti della fase di progettazione degli elementi dei report personalizzati devono implementare le interfacce dallo spazio dei nomi <xref:System.ComponentModel> in [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. La documentazione relativa a <xref:System.ComponentModel> è disponibile in [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.  
  
> [!IMPORTANT]  
>  Per impostazione predefinita, [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] viene installato con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a differenza di [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK. Se l'SDK non è installato nel computer e la documentazione associata non è inclusa nella documentazione online, non è possibile utilizzare i collegamenti al contenuto dell'SDK presenti in questa sezione. Dopo aver installato il [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK, è possibile aggiungere la documentazione del SDK alla documentazione Online e al sommario seguendo le istruzioni in [aggiungere o rimuovere la documentazione di SQL Server](http://msdn.microsoft.com/library/ef798cc8-87cf-4d60-a7bf-9e061bdd0052).  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un componente di Run-Time di elemento di Report personalizzato](../../reporting-services/custom-report-items/creating-a-custom-report-item-run-time-component.md)   
 [Creazione di un componente in fase di progettazione dell'elemento del Report personalizzato](../../reporting-services/custom-report-items/creating-a-custom-report-item-design-time-component.md)   
 [Procedura: distribuire un elemento del Report personalizzato](../../reporting-services/custom-report-items/how-to-deploy-a-custom-report-item.md)   
 [Librerie di classi di elemento di Report personalizzato](../../reporting-services/custom-report-items/custom-report-item-class-libraries.md)  
  
  

