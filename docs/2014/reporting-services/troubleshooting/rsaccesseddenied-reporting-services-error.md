---
title: rsAccessedDenied - Errore di Reporting Services | Microsoft Docs
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
- rsAccessDenied error
ms.assetid: 2f76b1bf-96a2-4755-b76b-84e933220efc
caps.latest.revision: 20
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 920f85eaa3f9bd000f8422d8ad3b454cdfd17813
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36054107"
---
# <a name="rsaccesseddenied---reporting-services-error"></a>rsAccessedDenied - Errore di Reporting Services
  L'errore di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] **rsAccessedDenied** si verifica quando un utente non dispone dell'autorizzazione per eseguire un'azione, ad esempio non dispone di un'assegnazione di ruolo che consenta di aprire un report o non ha aperto il browser con le autorizzazioni necessarie.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Modalità nativa &#124; modalità SharePoint|  
  
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
  
 Questo errore viene causato anche dall'amministratore locale del server di report. Per altre informazioni, vedere [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Assegnazioni di ruolo](../security/role-assignments.md)   
 [Concessione di autorizzazioni in un server di report in modalità nativa](../security/granting-permissions-on-a-native-mode-report-server.md)   
 [Ruoli e autorizzazioni &#40;Reporting Services&#41;](../security/roles-and-permissions-reporting-services.md)  
  
  