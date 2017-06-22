---
title: Debug del codice di estensione di recapito | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
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
- delivery extensions [Reporting Services], debugging
- debugging delivery extensions [Reporting Services]
- troubleshooting [Reporting Services], delivery extensions
ms.assetid: a7d959da-5005-4a50-aca7-2cef36aa9947
caps.latest.revision: 35
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: d3e683887f02436ad948b6a6aedb64ef749a7547
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="debugging-delivery-extension-code"></a>Esecuzione del debug del codice dell'estensione per il recapito
  Il [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] offre diversi strumenti di debug che consentono di analizzano il codice di estensione di recapito e individuare gli errori. Gli strumenti più appropriati da utilizzare variano in base alla finalità desiderata. In questo esempio viene utilizzato [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)].  
  
#### <a name="to-debug-your-delivery-extension-code"></a>Per eseguire il debug del codice dell'estensione per il recapito  
  
1.  Avviare [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)] e aprire il progetto di estensione di recapito.  
  
2.  Compilare il progetto e distribuire l'assembly di estensioni per il recapito e il file con estensione pdb associato nel server di report e in Gestione report. Per ulteriori informazioni sulla distribuzione, vedere [distribuzione di un'estensione di recapito](../../../reporting-services/extensions/delivery-extension/deploying-a-delivery-extension.md).  
  
3.  Se è stata scritta un'interfaccia utente di sottoscrizione per estendere Gestione report, aprire Internet Explorer e passare a Gestione report lasciando aperto il codice dell'estensione per il recapito in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]. Se per Gestione report non è stata distribuita un'interfaccia utente di sottoscrizione, aprire semplicemente l'applicazione client dalla quale si chiama l'estensione per il recapito utilizzando l'API SOAP.  
  
4.  Passare a [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] e al progetto di estensione per il recapito e impostare alcuni punti di interruzione nel codice.  
  
5.  Con il progetto di estensione di recapito ancora nella finestra attiva, fare clic su **Connetti a processo** sul **Debug** menu.  
  
     Il **Connetti a processo** verrà visualizzata la finestra di dialogo.  
  
6.  Elenco di processi, selezionare il processo di aspnet_wp.exe (o w3wp.exe, se l'applicazione viene distribuita in IIS 6.0) e fare clic su **collegamento**.  
  
7.  Definire una nuova sottoscrizione utilizzando l'estensione per il recapito. In genere, a tale scopo è possibile utilizzare Gestione report o l'API SOAP. In questo modo, è possibile richiamare il debugger ed eseguire il codice in corrispondenza dei punti di interruzione.  
  
8.  Esaminare il codice utilizzando il **F11** chiave. Per ulteriori informazioni sull'utilizzo di [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] per eseguire il debug, vedere la documentazione di [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di un'estensione di recapito](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Libreria di estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
