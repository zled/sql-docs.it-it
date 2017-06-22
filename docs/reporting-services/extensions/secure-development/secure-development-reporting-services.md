---
title: Sviluppo (Reporting Services) sicuro | Documenti Microsoft
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
- development security [Reporting Services]
- security [Reporting Services], development
- security [Reporting Services], strategies
ms.assetid: 12161a6c-b93b-4312-9d27-0c922561eb9b
caps.latest.revision: 15
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: cb8a4502531dbe3ee23434ea126457196b56c701
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="secure-development-reporting-services"></a>Sviluppo sicuro (Reporting Services)
  Il [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] fornisce un potente sistema di sicurezza che può eseguire codice in contesti di sicurezza soggetti a vincoli definiti dall'amministratore. [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] usano il sistema di sicurezza di [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], noto come sicurezza dall'accesso di codice (o sicurezza basata sull'evidenza). In un sistema con sicurezza dall'accesso di codice un utente può essere considerato attendibile per accedere a una risorsa, ma se il codice eseguito non è attendibile, l'accesso alla risorsa verrà negato.  
  
 A differenza della sicurezza basata su utenti specifici, la sicurezza basata su codice può essere espressa per assembly o dati personalizzati, per il recapito, il rendering e le estensioni di sicurezza sviluppati per [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Il codice dell'estensione può essere eseguito da un numero qualsiasi di utenti di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], ciascuno dei quali non è noto in fase di sviluppo. In [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] le estensioni o gli assembly personalizzati richiedono criteri di sicurezza specifici, rappresentati come tipi in [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Per altre informazioni sulla sicurezza dall'accesso di codice, vedere "Sicurezza dall'accesso di codice" nella documentazione di [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Sicurezza dall'accesso di codice in Reporting Services](../../../reporting-services/extensions/secure-development/code-access-security-in-reporting-services.md)  
 Descrive la sicurezza dall'accesso di codice e la configurazione dei criteri per le estensioni e gli assembly personalizzati in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 [Informazioni sui criteri di sicurezza](../../../reporting-services/extensions/secure-development/understanding-security-policies.md)  
 Descrive i diversi tipi di assembly in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] e il modo in cui la sicurezza dall'accesso di codice influisce sulle autorizzazioni per il codice.  
  
 [Utilizzo di Reporting Services Security Policy Files](../../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md)  
 Descrive i diversi componenti di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] e i corrispondenti file di configurazione dei criteri.  
  
  
