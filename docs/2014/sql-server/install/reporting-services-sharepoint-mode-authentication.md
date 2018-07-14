---
title: L'autenticazione in modalità SharePoint di Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Upgrade SharePoint Mode [Reporting Services]
- SharePoint integration
- SharePoint Mode
ms.assetid: 2c19794a-dd55-4fe5-b901-6dd93e9f6beb
caps.latest.revision: 8
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 704d104b8834675f7511c952db7fafb9fcccafd3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37247811"
---
# <a name="reporting-services-sharepoint-mode-authentication"></a>Autenticazione in modalità SharePoint di Reporting Services
  Utilizzare la pagina **Autenticazione in modalità SharePoint di Reporting Services** dell'Installazione guidata di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per specificare le credenziali dell'account del servizio utilizzato nell'installazione attuale di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Le credenziali verranno utilizzate per creare un nuovo pool di applicazioni SharePoint. Verrà inoltre creata una nuova applicazione di servizi [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint. Il nome dell'applicazione conterrà il nome dell'istanza di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] precedente.  
  
## <a name="options"></a>Opzioni  
  
-   L'opzione **Nome account pool di applicazioni SSRS** è di sola lettura. Il valore viene automaticamente popolato con il valore attuale dall'installazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] esistente in fase di aggiornamento.  
  
-   L'opzione **Password account pool di applicazioni SSRS** verrà disabilitata se l'account del pool di applicazioni non richiede una password (ad esempio, "NT Authority\NetworkService". Se per l'account del pool di applicazioni è richiesta una password, digitare la password corretta per procedere con l'aggiornamento.  
  
 Per altre informazioni, vedere [Upgrade and Migrate Reporting Services](http://go.microsoft.com/fwlink/?LinkID=245628) (http://go.microsoft.com/fwlink/?LinkID=245628).  
  
## <a name="see-also"></a>Vedere anche  
 [Eseguire l'aggiornamento e la migrazione di Reporting Services](http://go.microsoft.com/fwlink/?LinkID=245628)  
  
  
