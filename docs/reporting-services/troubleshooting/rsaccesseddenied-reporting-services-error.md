---
title: rsAccessedDenied - errore di Reporting Services | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rsAccessDenied error
ms.assetid: 2f76b1bf-96a2-4755-b76b-84e933220efc
caps.latest.revision: 21
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7ece42006b7022bd3fa031cd95ef97767055ad53
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="rsaccesseddenied---reporting-services-error"></a>rsAccessedDenied - Errore di Reporting Services
  L'errore di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] **rsAccessedDenied** si verifica quando un utente non dispone dell'autorizzazione per eseguire un'azione, ad esempio non dispone di un'assegnazione di ruolo che consenta di aprire un report o non ha aperto il browser con le autorizzazioni necessarie.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**Modalità nativa di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] &#124; Modalità SharePoint|  
  
-   Se l'errore si è verificato durante l'accesso diretto al server di report tramite URL, verrà eseguito il mapping tra l'eccezione e un errore HTTP 401.  
  
-   Se si è verificato durante l'utilizzo di Gestione report o un altro strumento, l'errore verrà visualizzato in un'apposita pagina.  
  
-   Se si è verificato durante un'operazione, una sottoscrizione o un recapito pianificato, l'errore verrà indicato solo nel file di log del server di report.  
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|**Nome prodotto**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|**ID evento**|rsAccessedDenied|  
|**Origine evento**|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|**Componente**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|**Testo del messaggio**|Le autorizzazioni concesse all'utente 'mydomain\myAccount' non sono sufficienti per eseguire questa operazione. (rsAccessDenied) (ReportingServicesLibrary)|  
  
## <a name="user-action"></a>Azione dell'utente  
 Le autorizzazioni che consentono di accedere al contenuto e alle operazioni del server di report vengono concesse tramite assegnazioni di ruolo. In una nuova installazione solo gli amministratori locali possono accedere a un server di report. Per concedere l'accesso ad altri utenti, l'amministratore locale deve creare un'assegnazione di ruolo che specifica un account di gruppo o un account utente di dominio, uno o più ruoli che definiscono le attività eseguibili dall'utente, nonché un ambito, ovvero in genere la cartella Home o il nodo radice della gerarchia di cartelle del server di report. Per creare le assegnazioni di ruolo, è possibile usare Gestione report. Per altre informazioni, cercare "assegnazioni di ruolo" nella documentazione online di SQL Server.  
  
 Questo errore viene causato anche dall'amministratore locale del server di report. Per altre informazioni, vedere [Configurare un server di report in modalità nativa per gli amministratori locali &#40;SSRS&#41;](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Assegnazioni di ruolo](../../reporting-services/security/role-assignments.md)   
 [Concessione di autorizzazioni in un Server di Report in modalità nativa](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)   
 [Ruoli e autorizzazioni &#40; Reporting Services &#41;](../../reporting-services/security/roles-and-permissions-reporting-services.md)  
  
  

