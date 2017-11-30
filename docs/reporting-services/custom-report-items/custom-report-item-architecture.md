---
title: Architettura di un elemento del report personalizzato | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords: custom report items, architecture
ms.assetid: 2a88ea46-c9f8-4dd7-aad1-16de11da4f06
caps.latest.revision: "16"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: f434dabada5fbe9e7f1c9f07008dd7c3f5ec0ff1
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="custom-report-item-architecture"></a>Architettura di un elemento del report personalizzato
  Un elemento del report personalizzato è un'estensione di RDL (Report Definition Language) che consente agli sviluppatori di aggiungere funzionalità per le quali non è disponibile il supporto nativo in RDL o di estendere le funzionalità dei controlli esistenti. Un elemento del report personalizzato è costituito da due componenti principali: il componente della fase di esecuzione e quello della fase di progettazione. Questi componenti vengono implementati come assembly [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] e possono essere scritti in qualsiasi linguaggio conforme a CLS.  
  
## <a name="the-run-time-component"></a>Componente della fase di esecuzione  
 Il componente della fase di esecuzione per un elemento del report personalizzato viene chiamato da Elaborazione report in fase di esecuzione. Questo componente accetta i dati passati da Elaborazione report in fase di esecuzione, elabora tali dati e restituisce un'immagine contenente l'elemento del report personalizzato di cui è stato eseguito il rendering.  
  
 ![Componente runtime dell'elemento del report personalizzato](../../reporting-services/custom-report-items/media/customreportitemrun-timecomponentarchitecture.gif "Componente runtime dell'elemento del report personalizzato")  
  
## <a name="the-design-time-component"></a>Componente della fase di progettazione  
 Il componente della fase di progettazione consente la definizione e la modifica dell'elemento del report personalizzato nell'interfaccia di Progettazione report in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Questo componente è costituito da diversi controlli secondari che definiscono l'aspetto e le proprietà dell'elemento del report personalizzato nell'ambiente di progettazione.  
  
 ![Componente dell'elemento del report personalizzato per la fase di progettazione](../../reporting-services/custom-report-items/media/customreportitemdesign-timecomponentarchitecture.gif "Componente dell'elemento del report personalizzato per la fase di progettazione")  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un componente runtime dell'elemento del report personalizzato](../../reporting-services/custom-report-items/creating-a-custom-report-item-run-time-component.md)   
 [Creazione di un componente dell'elemento del report personalizzato per la fase di progettazione](../../reporting-services/custom-report-items/creating-a-custom-report-item-design-time-component.md)   
 [Procedura: Distribuzione di un elemento del report personalizzato](../../reporting-services/custom-report-items/how-to-deploy-a-custom-report-item.md)  
  
  
