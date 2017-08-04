---
title: "Proprietà SQL Server Browser (scheda accesso) | Documenti Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c77871ec-c2f4-4e4a-9a10-5aeb4ae70507
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ac257d9a9044be9d1d7003fe066337fff116dcf0
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="sql-server-browser-properties-log-on-tab"></a>Proprietà - SQL Server Browser (scheda Accesso)
  Il programma [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser viene eseguito come servizio nel server. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser rimane in attesa delle richieste in entrata di risorse di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e fornisce informazioni sulle istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installate nel computer.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser rimane in attesa su una porta UDP e accetta le richieste non autenticate tramite il protocollo SSRP ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Resolution Protocol).  
  
 La modifica della password di un account diventa effettiva immediatamente, senza dover riavviare il servizio.  
  
## <a name="options"></a>Opzioni  
 **Account di sistema locale**  
 Consente di eseguire il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser nel contesto di sicurezza dell'account di sistema locale. È tuttavia consigliabile utilizzare un account con poche autorizzazioni, se possibile.  
  
 **Account seguente**  
 Specificare un account utente locale o di dominio che utilizza l’autenticazione di Windows. È consigliabile usare un account utente di dominio con diritti minimi per i servizi. Per ulteriori informazioni sulla selezione di un account, vedere "Impostazione di account di servizio Windows" nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Sfoglia**  
 Consente di individuare un utente o un'entità di sicurezza predefinita.  
  
> [!IMPORTANT]  
>  Utilizzare un account con poche autorizzazioni. Per informazioni sulle autorizzazioni necessarie per il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser, vedere la sezione relativa alla sicurezza in [Servizio SQL Server Browser](../../tools/configuration-manager/sql-server-browser-service.md).  
  
 **Password**  
 Immettere la password dell'entità di sicurezza.  
  
 **Conferma password**  
 Confermare la password dell'entità di sicurezza.  
  
 **Stato del servizio**  
 Indica se il servizio è in esecuzione, arrestato o disabilitato. "**…**" indica una modifica di stato in sospeso.  
  
 **Start**  
 Consente di avviare il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser.  
  
 **Arresta**  
 Consente di arrestare il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser.  
  
 **Sospendi**  
 Consente di sospendere il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser.  
  
 **Riprendi**  
 Consente di riprendere un'istanza del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser sospesa.  
  
## <a name="see-also"></a>Vedere anche  
 [Servizio SQL Server Browser](../../tools/configuration-manager/sql-server-browser-service.md)  
  
  
