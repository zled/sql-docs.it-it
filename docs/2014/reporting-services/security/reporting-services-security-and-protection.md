---
title: Sicurezza e protezione di Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security [Reporting Services]
- Reporting Services, security
ms.assetid: 270075c5-bf12-4467-a775-abbda3d954a5
caps.latest.revision: 20
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 9a993f574cbf272e4fdf47066360bd09299cd7d1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36167183"
---
# <a name="reporting-services-security-and-protection"></a>Sicurezza e protezione di Reporting Services
  È possibile usare le informazioni contenute in questa sezione per ottenere altre informazioni sulle caratteristiche di sicurezza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Questa sezione descrive inoltre i modelli di autorizzazione e i provider di autenticazione supportati in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
## <a name="extended-protection-for-authentication"></a>Protezione estesa per l'autenticazione  
 A partire da [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], è disponibile il supporto per la protezione estesa per l'autenticazione. La caratteristica di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta l'uso del binding di canale e dell'associazione al servizio per migliorare la protezione dell'autenticazione. Le funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] devono essere utilizzate con un sistema operativo che supporti la protezione estesa. Per altre informazioni, vedere [protezione estesa per l'autenticazione con Reporting Services](extended-protection-for-authentication-with-reporting-services.md).  
  
## <a name="authentication-and-authorization"></a>Autenticazione e autorizzazione  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] offre diversi tipi di autenticazione per utenti e applicazioni client da autenticare con il server di report. L'utilizzo del tipo di autenticazione corretto per il server di report consente all'organizzazione di ottenere il livello di sicurezza appropriato richiesto dall'organizzazione. Per altre informazioni, vedere [Autenticazione con il server di report](authentication-with-the-report-server.md).  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] usa inoltre ruoli e autorizzazioni per controllare l'accesso dell'utente al contenuto nel catalogo del server di report (in altre parole chi può accedere a che cosa e in che modo può accedervi). Per altre informazioni, vedere [Ruoli e autorizzazioni &#40;Reporting Services&#41;](roles-and-permissions-reporting-services.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Descrizioni delle attività|Collegamenti|  
|-----------------------|-----------|  
|Configurare Secure Socket Layer (SSL) per proteggere le connessioni client al server di report.|[Configurare connessioni SSL in un server di report in modalità nativa](configure-ssl-connections-on-a-native-mode-report-server.md)|  
  
  