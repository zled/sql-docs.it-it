---
title: Salvare pacchetti | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Integration Services packages, saving
- packages [Integration Services], saving
- saving packages
- SSIS packages, saving
- SQL Server Integration Services packages, saving
ms.assetid: 17c1de2c-637f-45c2-a148-79294bae0af4
caps.latest.revision: 47
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: f938400661c97c842149f958f9660fef20085a8b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064776"
---
# <a name="save-packages"></a>Salvataggio di pacchetti
  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] è possibile usare Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] per compilare i pacchetti e quindi salvarli nel file system come file XML, con estensione dtsx. È inoltre possibile salvare copie del file XML di un pacchetto nel database msdb in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] o nell'archivio pacchetti. L'archivio pacchetti è costituito dalle cartelle del percorso del file system gestito dal servizio [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
 Se si salva un pacchetto nel file system, successivamente sarà possibile utilizzare il servizio [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] per importarlo in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] o nell'archivio pacchetti. Per altre informazioni, vedere [Importare ed esportare pacchetti &#40;servizio SSIS&#41;](../../2014/integration-services/import-and-export-packages-ssis-service.md).  
  
 È inoltre possibile usare l'utilità della riga di comando **dtutil** per copiare un pacchetto dal file system al database msdb e viceversa. Per altre informazioni, vedere [dtutil Utility](dtutil-utility.md).  
  
### <a name="to-save-a-package"></a>Per salvare un pacchetto  
  
-   [Salvare un pacchetto nel File System](../../2014/integration-services/save-a-package-to-the-file-system.md)  
  
-   [Salvare una copia di un pacchetto](../../2014/integration-services/save-a-copy-of-a-package.md)  
  
  