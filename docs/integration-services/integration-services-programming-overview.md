---
title: Cenni preliminari sulla programmazione di Integration Services | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Integration Services, programming
- architecture [Integration Services]
- assemblies [Integration Services]
- SSIS, programming
- SQL Server Integration Services, programming
- run-time engine [Integration Services]
- packages [Integration Services], programming
- data flow engine [Integration Services]
- languages [Integration Services]
ms.assetid: 262babc6-eea5-4609-bc65-07d64cbcfee9
caps.latest.revision: 42
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 47cb31613e30199902335d891b9f5777757feed3
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="integration-services-programming-overview"></a>Panoramica della programmazione di Integration Services
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] un'architettura che separa lo spostamento dei dati e la trasformazione dal flusso di controllo del pacchetto e la gestione. Due motori distinti definiscono questa architettura, che possono essere automatizzati ed estesi quando si programma [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Il motore di runtime implementa l'infrastruttura del flusso di controllo e di gestione dei pacchetti che consente agli sviluppatori di controllare il flusso di esecuzione e impostare le opzioni per la registrazione, la gestione degli eventi e le variabili. Il motore flusso di dati è un motore speciale, a elevate prestazioni, dedicato esclusivamente all'estrazione, alla trasformazione e al caricamento di dati. Quando si programma [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], si utilizzeranno questi due motori.  
  
 Nell'immagine seguente è illustrata l'architettura di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
 ![Architettura di Integration Services](../integration-services/media/mw-dts-01.gif "architettura di Integration Services")  
  
## <a name="integration-services-run-time-engine"></a>Motore di runtime di Integration Services  
 Il motore di runtime di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] controlla la gestione e l'esecuzione di pacchetti, implementando l'infrastruttura che abilita l'ordine di esecuzione, la registrazione, le variabili e la gestione degli eventi. Programmando il motore di runtime di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], gli sviluppatori possono automatizzare la creazione, la configurazione e l'esecuzione di pacchetti, nonché creare attività personalizzate e altre estensioni.  
  
 Per ulteriori informazioni, vedere [estensione del pacchetto con l'attività Script](../integration-services/extending-packages-scripting/task/extending-the-package-with-the-script-task.md), [lo sviluppo di un'attività personalizzata](../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md), e [creazione pacchetti a livello di codice](../integration-services/building-packages-programmatically/building-packages-programmatically.md).  
  
## <a name="integration-services-data-flow-engine"></a>Motore flusso di dati di Integration Services  
 Il motore flusso di dati gestisce l'attività Flusso di dati, un'attività speciale a elevate prestazioni dedicata allo spostamento e alla trasformazione di dati da origini disparate. A differenza di altre attività, l'attività Flusso di dati contiene oggetti aggiuntivi, i componenti flusso di dati, che possono essere origini, trasformazioni o destinazioni. Questi componenti costituiscono le parti mobili principali dell'attività. Definiscono lo spostamento e la trasformazione dei dati. Programmando il motore flusso di dati, gli sviluppatori possono automatizzare la creazione e la configurazione dei componenti in un'attività Flusso di dati, nonché creare componenti personalizzati.  
  
 Per ulteriori informazioni, vedere [estendendo il flusso di dati con il componente Script](../integration-services/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md), [lo sviluppo di un componente del flusso di dati personalizzato](../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md), e [creazione pacchetti a livello di codice](../integration-services/building-packages-programmatically/building-packages-programmatically.md).  
  
## <a name="supported-languages"></a>Lingue supportate  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]supporta completamente il [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. In questo modo gli sviluppatori possono programmare [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] nel linguaggio conforme a .NET che preferiscono. Sebbene il motore di runtime e il motore flusso di dati siano scritti in codice nativo, sono entrambi disponibili tramite un modello a oggetti completamente gestito.  
  
 È possibile programmare [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] pacchetti, attività personalizzate e componenti in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] o in un altro editor di codice o testo. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] offre allo sviluppatore numerosi strumenti e funzionalità per semplificare e accelerare i cicli iterativi di codifica, debug e test. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] semplifica la distribuzione. Tuttavia, non è necessario [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per compilare e ottenere progetti di codice di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK include i compilatori [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] e [!INCLUDE[csprcs](../includes/csprcs-md.md)] e gli strumenti correlati.  
  
> [!IMPORTANT]  
>  Per impostazione predefinita, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] viene installato con [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], a differenza di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK. Se l'SDK non è installato nel computer e la documentazione associata non è inclusa nella documentazione online, non è possibile utilizzare i collegamenti al contenuto dell'SDK presenti in questa sezione. Dopo aver installato il [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK, è possibile aggiungere la documentazione del SDK alla documentazione Online e al sommario seguendo le istruzioni in [aggiungere o rimuovere la documentazione di SQL Server](http://msdn.microsoft.com/library/ef798cc8-87cf-4d60-a7bf-9e061bdd0052).  
  
 Il [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] attività Script e componente di Script utilizzano [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tools for Applications (VSTA) come ambiente di scripting incorporato. VSTA support [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Basic e [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual C#  
  
> [!NOTE]  
>  Le API di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] non sono compatibili con linguaggi di scripting basati su COM come VBScript.  
  
## <a name="locating-assemblies"></a>Individuazione di assembly  
 In [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] gli assembly [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sono stati aggiornati a .NET 4.0. È una global assembly cache separata per .NET 4 in  *\<unità >*: \Windows\Microsoft.net\assembly. Tutti gli assembly di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] possono essere individuati in questo percorso, generalmente nella cartella GAC_MSIL.  
  
 Come nelle versioni precedenti di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], i componenti di base [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] file DLL di estendibilità sono anche disponibili in  *\<unità >*: \Programmi\Microsoft SQL Server\100\SDK\Assemblies.  
  
## <a name="commonly-used-assemblies"></a>Assembly di uso comune  
 Nella tabella seguente sono elencati gli assembly utilizzati di frequente quando si programma [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] utilizzando [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
|Assembly|Description|  
|--------------|-----------------|  
|Microsoft.SqlServer.ManagedDTS.dll|Contiene il motore di runtime gestito.|  
|Microsoft.SqlServer.RuntimeWrapper.dll|Contiene l'assembly di interoperabilità primario, o wrapper, per il motore di runtime nativo.|  
|Microsoft.SqlServer.PipelineHost.dll|Contiene il motore flusso di dati gestito.|  
|Microsoft.SqlServer.PipelineWrapper.dll|Contiene l'assembly di interoperabilità primario, o wrapper, per il motore flusso di dati nativo.|  
  
  
