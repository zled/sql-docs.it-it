---
title: Cenni preliminari sulle estensioni di sicurezza | Documenti Microsoft
ms.custom: 
ms.date: 03/15/2017
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
- security [Reporting Services], extensions
ms.assetid: 24ccd795-6506-457c-93ac-6a9dd6bb9a46
caps.latest.revision: 22
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: f7e8c95a478e733722d3c80da4b5e12e992ef4da
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="security-extensions-overview"></a>Panoramica sulle estensioni di sicurezza
  Un'estensione di sicurezza di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] consente l'autenticazione e l'autorizzazione di utenti o gruppi, ovvero consente a utenti diversi di accedere a un server di report e, sulla base delle relative identità, di eseguire diverse attività o operazioni. Per impostazione predefinita, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] utilizza un'estensione di autenticazione basata su Windows che verifica le identità degli utenti che dichiarano di avere account nel sistema tramite i protocolli degli account di Windows. In [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] l'autorizzazione degli utenti viene effettuata tramite un sistema di sicurezza basato sui ruoli. Il modello di sicurezza basato sui ruoli di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] è simile ai modelli di sicurezza basati sui ruoli di altre tecnologie.  
  
 Poiché le estensioni di sicurezza si basano su un'API aperta ed estensibile, è possibile creare nuove estensioni di autenticazione e autorizzazione in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Di seguito viene fornito un esempio di una tipica implementazione dell'estensione di sicurezza in cui l'autenticazione e l'autorizzazione sono basate su form:  
  
 ![Processo di estensione di sicurezza di servizi di reporting](../../../reporting-services/extensions/security-extension/media/rosettasecurityextensionflow.gif "processo di estensione di sicurezza di Reporting Services")  
  
 Come illustrato nella figura, l'autenticazione e l'autorizzazione vengono effettuate nel modo seguente:  
  
1.  Un utente tenta di accedere a Gestione report mediante un URL e viene reindirizzato a un form che ne raccoglie le credenziali per l'applicazione client.  
  
2.  L'utente invia le credenziali al form.  
  
3.  Le credenziali utente vengono inviate al servizio Web Reporting Services tramite il metodo <xref:ReportService2010.ReportingService2010.LogonUser%2A>.  
  
4.  Il servizio Web chiama l'estensione di sicurezza fornita dal cliente e verifica che nome utente e password siano presenti nell'autorità di sicurezza personalizzata.  
  
5.  Dopo l'autenticazione, il servizio Web crea e gestisce un ticket di autenticazione (noto come "cookie"), quindi verifica il ruolo dell'utente per la home page di Gestione report.  
  
6.  Il servizio Web restituisce il cookie al browser e visualizza l'interfaccia utente appropriata in Gestione report.  
  
7.  Dopo l'autenticazione dell'utente, il browser invia richieste a Gestione report durante la trasmissione del cookie nell'intestazione HTTP. Queste richieste vengono inviate in risposta alle azioni dell'utente all'interno dell'applicazione Gestione report.  
  
8.  Il cookie viene trasmesso nell'intestazione HTTP al servizio Web insieme all'operazione utente richiesta.  
  
9. Il cookie viene convalidato e, se valido, il server di report restituisce il descrittore di sicurezza e altre informazioni relative all'operazione richiesta dal database del server di report.  
  
10. Se il cookie è valido, il server di report effettua una chiamata all'estensione di sicurezza per controllare se l'utente è autorizzato a eseguire l'operazione specifica.  
  
11. Se l'utente è autorizzato, il server di report esegue l'operazione richiesta e restituisce il controllo al chiamante.  
  
12. Dopo l'autenticazione dell'utente, l'accesso all'URL per il server di report utilizza lo stesso cookie. Il cookie viene trasmesso nell'intestazione HTTP.  
  
13. L'utente continua a richiedere operazioni sul server di report fino al termine della sessione.  
  
## <a name="when-to-implement-a-security-extension"></a>Quando implementare un'estensione di sicurezza  
 Se possibile, si consiglia di utilizzare l'autenticazione di Windows. Tuttavia, l'autenticazione e l'autorizzazione personalizzate per [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] possono essere appropriate nei due casi seguenti:  
  
-   Si dispone di un'applicazione Internet o Extranet in cui non è possibile utilizzare gli account di Windows.  
  
-   Si dispone di utenti e ruoli personalizzati ed è necessario fornire uno schema di autorizzazione corrispondente in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di un'estensione di sicurezza](../../../reporting-services/extensions/security-extension/implementing-a-security-extension.md)   
 [Configurare Gestione Report per passare i cookie di autenticazione personalizzati](https://msdn.microsoft.com/library/ms345241(v=sql.110).aspx)  
  
  
