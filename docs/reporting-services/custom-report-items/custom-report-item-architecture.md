---
title: Architettura di un elemento del Report personalizzato | Documenti Microsoft
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
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom report items, architecture
ms.assetid: 2a88ea46-c9f8-4dd7-aad1-16de11da4f06
caps.latest.revision: 16
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 8b79071c67e3ada6fcfc0f588d9cba4580a981e8
ms.contentlocale: it-it
ms.lasthandoff: 06/13/2017

---
# <a name="custom-report-item-architecture"></a>Architettura di un elemento del report personalizzato
  Un elemento del report personalizzato è un'estensione di RDL (Report Definition Language) che consente agli sviluppatori di aggiungere funzionalità per le quali non è disponibile il supporto nativo in RDL o di estendere le funzionalità dei controlli esistenti. Un elemento del report personalizzato è costituito da due componenti principali: il componente della fase di esecuzione e quello della fase di progettazione. Questi componenti vengono implementati come assembly [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] e possono essere scritti in qualsiasi linguaggio conforme a CLS.  
  
## <a name="the-run-time-component"></a>Componente della fase di esecuzione  
 Il componente della fase di esecuzione per un elemento del report personalizzato viene chiamato da Elaborazione report in fase di esecuzione. Questo componente accetta i dati passati da Elaborazione report in fase di esecuzione, elabora tali dati e restituisce un'immagine contenente l'elemento del report personalizzato di cui è stato eseguito il rendering.  
  
 ![Componente runtime dell'elemento del report personalizzato](../../reporting-services/custom-report-items/media/customreportitemrun-timecomponentarchitecture.gif "componente in fase di esecuzione elemento del report personalizzato")  
  
## <a name="the-design-time-component"></a>Componente della fase di progettazione  
 Il componente della fase di progettazione consente la definizione e la modifica dell'elemento del report personalizzato nell'interfaccia di Progettazione report in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Questo componente è costituito da diversi controlli secondari che definiscono l'aspetto e le proprietà dell'elemento del report personalizzato nell'ambiente di progettazione.  
  
 ![Componente in fase di progettazione del report personalizzato elemento](../../reporting-services/custom-report-items/media/customreportitemdesign-timecomponentarchitecture.gif "componente in fase di progettazione elemento del report personalizzato")  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un componente di Run-Time di elemento di Report personalizzato](../../reporting-services/custom-report-items/creating-a-custom-report-item-run-time-component.md)   
 [Creazione di un componente in fase di progettazione dell'elemento del Report personalizzato](../../reporting-services/custom-report-items/creating-a-custom-report-item-design-time-component.md)   
 [Procedura: distribuire un elemento del Report personalizzato](../../reporting-services/custom-report-items/how-to-deploy-a-custom-report-item.md)  
  
  
