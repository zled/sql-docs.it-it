---
title: Proprietà server (pagina Generale) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.reportserver.serverproperties.general.f1
ms.assetid: 23537d52-4356-450f-a671-5921cef2431f
caps.latest.revision: 33
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 05bcbd306dc29769db143fb4614c01d527144b82
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156622"
---
# <a name="server-properties-general-page"></a>Proprietà server (pagina Generale)
  Questa pagina consente di visualizzare o modificare il titolo utilizzato in Gestione report, abilitare o disabilitare la cartella Report personali, selezionare una definizione di ruolo per la sicurezza della cartella Report personali e abilitare o disabilitare il controllo di stampa client.  
  
 Per aprire questa pagina, avviare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connettersi a un'istanza del server di report, il nome del server di report e quindi scegliere **proprietà**.  
  
 La modalità del server determina le proprietà del server che è possibile impostare. Se si gestisce un server di report configurato per la modalità integrata SharePoint, non è possibile abilitare Report personali o impostare il titolo dell'applicazione per Gestione report.  
  
## <a name="options"></a>Opzioni  
 **Nome**  
 Consente di digitare il nome di un'applicazione che verrà visualizzato in Gestione report. Per impostazione predefinita, il valore è [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Il nome specificato compare solamente in Gestione report.  
  
 **Versione**  
 Questa proprietà è di sola lettura. Specifica la versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in uso.  
  
 **Edizione**  
 Questa proprietà è di sola lettura. Viene specificata l'istanza corrente del server di report. Gestione report non è disponibile in tutte le edizioni di [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per un elenco delle funzionalità supportate dalle edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 **Modalità di autenticazione**  
 Questa proprietà è di sola lettura. che identifica i tipi di richieste di autenticazione accettati dall'istanza del server di report. Per modificare la modalità di autenticazione, è necessario modificare il file RSReportServer.config. Per altre informazioni, vedere [Autenticazione con il server di report](../security/authentication-with-the-report-server.md).  
  
 **URL**  
 Questa proprietà è di sola lettura. che specifica l'URL del servizio Web ReportServer. Questo valore è specificato nello strumento di configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Per altre informazioni, vedere [Configurare un URL &#40;Gestione configurazione SSRS&#41;](../install-windows/configure-a-url-ssrs-configuration-manager.md).  
  
 **Abilita una cartella Report personali per ogni utente**  
 Consente di rendere disponibile la cartella Report personali per gli utenti. Questa opzione è disponibile solo per i server di report in modalità nativa.  
  
 **Selezionare il ruolo da applicare a ogni cartella Report personali**  
 Consente di specificare una definizione di ruolo da utilizzare per la sicurezza della cartella Report personali. La definizione di ruolo identifica il set delle attività che sono supportate in ogni cartella Report personali.  
  
 **Consenti download per il controllo di stampa client ActiveX**  
 Imposta il `EnableClientPrinting` proprietà sistema del server di report. Se si abilita la stampa su client, gli utenti con autorizzazioni di amministrazione nel computer locale possono eseguire il download di un controllo ActiveX firmato per la stampa dei report HTML. Per altre informazioni, vedere [abilitare e disabilitare la stampa lato Client per Reporting Services](../report-server/enable-and-disable-client-side-printing-for-reporting-services.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Impostare le proprietà di un server di report &#40;Management Studio&#41;](set-report-server-properties-management-studio.md)   
 [Eseguire la connessione a un server di report in Management Studio](connect-to-a-report-server-in-management-studio.md)   
 [Abilitare e disabilitare la funzionalità Report personali](../report-server/enable-and-disable-my-reports.md)   
 [Guida sensibile al contesto del server di report in Management Studio](report-server-in-management-studio-f1-help.md)   
 [Proteggere i report personali](../security/secure-my-reports.md)  
  
  