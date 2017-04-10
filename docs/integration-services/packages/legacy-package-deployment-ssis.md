---
title: "distribuzione del pacchetto legacy (SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pacchetti di Integration Services, distribuzione"
  - "distribuzione di pacchetti [Integration Services]"
  - "pacchetti di SQL Server Integration Services, distribuzione"
  - "distribuzione di pacchetti [Integration Services], informazioni sulla distribuzione dei pacchetti"
  - "pacchetti [Integration Services], distribuzione"
  - "pacchetti SSIS, distribuzione"
ms.assetid: 0f5fc7be-e37e-4ecd-ba99-697c8ae3436f
caps.latest.revision: 46
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 46
---
# distribuzione del pacchetto legacy (SSIS)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] include strumenti e procedure guidate per la distribuzione di pacchetti dal computer di sviluppo al server di produzione o ad altri computer.  
  
 La procedura per la distribuzione di pacchetti prevede quattro passaggi.  
  
1.  Il primo passaggio è facoltativo e riguarda la creazione delle configurazioni dei pacchetti che aggiornano le proprietà degli elementi dei pacchetti in fase di esecuzione. Le configurazioni vengono incluse automaticamente durante la distribuzione dei pacchetti.  
  
2.  Il secondo passaggio consiste nella compilazione del progetto [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] per creare un'utilità di distribuzione di pacchetti. L'utilità di distribuzione per il progetto contiene i pacchetti che si desidera distribuire.  
  
3.  Il terzo passaggio consiste nel copiare nel computer di destinazione la cartella di distribuzione creata in fase di compilazione del progetto [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
4.  Il quarto passaggio consiste nell'eseguire nel computer di destinazione l'Installazione guidata pacchetti per installare i pacchetti nel file system o in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## Attività correlate  
 Per informazioni su come creare un'utilità di distribuzione, vedere [Creazione di un'utilità di distribuzione](../../integration-services/packages/create-a-deployment-utility.md).  
  
 Per informazioni su come distribuire i pacchetti usando l'utilità di distribuzione, vedere [Distribuzione di pacchetti con l'utilità di distribuzione](../../integration-services/packages/deploy-packages-by-using-the-deployment-utility.md).  
  
 Per informazioni su come creare le configurazioni dei pacchetti, vedere [Creazione di configurazioni dei pacchetti](../../integration-services/packages/create-package-configurations.md).  
  
  