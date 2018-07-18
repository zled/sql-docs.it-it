---
title: Aggiornamento dei report mediante le classi generate dallo Schema RDL (esercitazione su SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- RDL [Reporting Services], generating
- RDL [Reporting Services], tutorials
- RDL [Reporting Services], serializing
ms.assetid: 8f81d48f-7ab9-4ef8-bce0-7d16d9a47fbd
caps.latest.revision: 26
author: craigg-msft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 96d125a3d69b564c94b64d23f825778c55068991
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37297561"
---
# <a name="updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial"></a>Aggiornamento dei report mediante le classi generate dallo schema RDL (esercitazione SSRS)
  Questa esercitazione illustra come usare lo strumento XML Schema Definition (Xsd.exe.) per generare le classi che consentono di serializzare e deserializzare i file di definizione del report (con estensione rdl e rdlc) con i [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.Xml.Serialization.XmlSerializer> classe.  
  
## <a name="what-you-will-learn"></a>Lezioni dell'esercitazione  
 Durante questa esercitazione verranno eseguite le attività seguenti:  
  
-   Creare un'applicazione usando il [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] modello di progetto applicazione Console.  
  
-   Generare classi dallo schema di definizione del linguaggio RDL (Report) mediante il **xsd** dello strumento.  
  
-   Connessione a un server di report e recupero di una definizione del report.  
  
-   Scrittura di codice per l'aggiornamento del file di definizione del report.  
  
-   Salvataggio della definizione aggiornata del report nel server di report.  
  
-   Eseguire l'applicazione dello schema RDL (VB/C#).  
  
> [!NOTE]  
>  Gli esempi di codice forniti in questa esercitazione potrebbero non funzionare per i report in cui non è disponibile alcuna descrizione. L'errore si verifica perché la proprietà di descrizione non è disponibile per i report privi di descrizione specificata.  
  
## <a name="requirements"></a>Requisiti  
 Per eseguire l'esercitazione, occorre:  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].  
  
-   Autorizzazioni sufficienti per l'accesso al servizio Web ReportServer e la pubblicazione di report sul servizio nel computer in cui è installato il server di report.  
  
-   Il database di esempio [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] installato in un'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Un report installato nel server di report. In questa esercitazione viene utilizzato il report di esempio Company Sales 2012. Per altre informazioni sui report di esempio, vedere [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
> [!NOTE]  
>  Gli esempi non vengono installati automaticamente durante l'installazione, ma possono essere installati in qualsiasi momento. Per informazioni sugli esempi, vedere [SQL Server Product Samples](http://go.microsoft.com/fwlink/?LinkId=182887).  
  
 **Tempo stimato per completare l'esercitazione:** 30 minuti  
  
## <a name="tasks"></a>Attività  
 [Lezione 1: Creazione del progetto di Visual Studio per lo schema RDL](../../2014/tutorials/lesson-1-create-the-rdl-schema-visual-studio-project.md)  
  
 [Lezione 2: Generazione delle classi dallo schema RDL mediante lo strumento xsd](../../2014/tutorials/lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool.md)  
  
 [Lezione 3: Caricamento della definizione di un report dal Server report](../../2014/tutorials/lesson-3-load-a-report-definition-from-the-report-server.md)  
  
 [Lezione 4: Aggiornamento della definizione del report a livello di programmazione](../../2014/tutorials/lesson-4-update-the-report-definition-programmatically.md)  
  
 [Lezione 5: Pubblicazione della definizione del report nel Server report](../../2014/tutorials/lesson-5-publish-the-report-definition-to-the-report-server.md)  
  
 [Lezione 6: Eseguire l'applicazione dello Schema RDL &#40;Visual Basic-C&#35;&#41;](../../2014/tutorials/lesson-6-run-the-rdl-schema-application-vb-csharp.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Report Definition Language &#40;SSRS&#41;](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
