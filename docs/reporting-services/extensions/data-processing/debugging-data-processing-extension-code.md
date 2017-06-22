---
title: Debug del codice di estensione per l'elaborazione dati | Documenti Microsoft
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
- debugging data processing extensions [Reporting Services]
- troubleshooting [Reporting Services], data processing extensions
- data processing extensions [Reporting Services], debugging
ms.assetid: e963e205-9ae0-446d-97df-028a1d2727d9
caps.latest.revision: 40
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 7af6b33039d19029d1595ac08f5d5345cdaa1c58
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="debugging-data-processing-extension-code"></a>Debug del codice di un'estensione per l'elaborazione dati
  Il [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] offre diversi strumenti di debug che consentono di analizzano il codice di estensione per l'elaborazione dati e individuare gli errori. Gli strumenti più appropriati da utilizzare variano in base alla finalità desiderata. In questo esempio viene utilizzato [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)].  
  
#### <a name="to-debug-your-data-processing-extension-code"></a>Per eseguire il debug del codice di un'estensione per l'elaborazione dati  
  
1.  Avviare [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)] e aprire il progetto di estensione per l'elaborazione dati.  
  
2.  Compilare il progetto e distribuire l'assembly di estensioni per l'elaborazione dati e il file con estensione pdb associato in Gestione report. Per ulteriori informazioni sulla distribuzione, vedere [procedura: distribuire un'estensione per l'elaborazione dati in Progettazione Report](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension-to-report-designer.md).  
  
3.  Aprire un nuovo progetto report in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] lasciando aperto il codice dell'estensione per l'elaborazione dati in una finestra separata di [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
4.  Passare alla finestra di [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] che contiene il progetto di estensione per l'elaborazione dati e impostare alcuni punti di interruzione nel codice.  
  
5.  Con l'elaborazione dati estensione finestra progetto ancora attiva, fare clic su **Connetti a processo** sul **Debug** menu.  
  
     Il **Connetti a processo** verrà visualizzata la finestra di dialogo.  
  
6.  Nell'elenco dei processi, selezionare il processo devenv.exe che corrisponde al progetto Report e fare clic su **collegamento**.  
  
7.  Definire l'origine dati del report utilizzando il **dati del Report** scheda del progetto Report. In genere, si utilizza lo strumento generico Progettazione query per eseguire una query sull'origine dati personalizzata. In questo modo, è possibile richiamare il debugger ed eseguire il codice in corrispondenza dei punti di interruzione.  
  
8.  Esaminare il codice istruzione per istruzione premendo F11 Per ulteriori informazioni sull'utilizzo di [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] per eseguire il debug, vedere la documentazione di [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione di un'estensione per l'elaborazione dati](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md)   
 [Estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Implementazione di un'estensione per l'elaborazione dati](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Libreria di estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
