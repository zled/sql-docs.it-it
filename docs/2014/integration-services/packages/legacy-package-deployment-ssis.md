---
title: Pacchetto di distribuzione (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, deploying
- deploying packages [Integration Services]
- SQL Server Integration Services packages, deploying
- deploying packages [Integration Services], about deploying packages
- packages [Integration Services], deploying
- SSIS packages, deploying
ms.assetid: 0f5fc7be-e37e-4ecd-ba99-697c8ae3436f
caps.latest.revision: 45
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 26c5f0af58ea602a8a0d5e73512b5fa2df2a013b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37276957"
---
# <a name="package-deployment-ssis"></a>Distribuzione di pacchetti (SSIS)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] include strumenti e procedure guidate per la distribuzione di pacchetti dal computer di sviluppo al server di produzione o ad altri computer.  
  
 La procedura per la distribuzione di pacchetti prevede quattro passaggi.  
  
1.  Il primo passaggio è facoltativo e riguarda la creazione delle configurazioni dei pacchetti che aggiornano le proprietà degli elementi dei pacchetti in fase di esecuzione. Le configurazioni vengono incluse automaticamente durante la distribuzione dei pacchetti.  
  
2.  Il secondo passaggio consiste nella compilazione del progetto [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] per creare un'utilità di distribuzione di pacchetti. L'utilità di distribuzione per il progetto contiene i pacchetti che si desidera distribuire.  
  
3.  Il terzo passaggio consiste nel copiare nel computer di destinazione la cartella di distribuzione creata in fase di compilazione del progetto [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
4.  Il quarto passaggio consiste nell'eseguire nel computer di destinazione l'Installazione guidata pacchetti per installare i pacchetti nel file system o in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="related-tasks"></a>Related Tasks  
 Per informazioni su come creare un'utilità di distribuzione, vedere [Creazione di un'utilità di distribuzione](../create-a-deployment-utility.md).  
  
 Per informazioni su come distribuire i pacchetti usando l'utilità di distribuzione, vedere [Distribuzione di pacchetti con l'utilità di distribuzione](../deploy-packages-by-using-the-deployment-utility.md).  
  
 Per informazioni su come creare le configurazioni dei pacchetti, vedere [Creazione di configurazioni dei pacchetti](../create-package-configurations.md).  
  
  
