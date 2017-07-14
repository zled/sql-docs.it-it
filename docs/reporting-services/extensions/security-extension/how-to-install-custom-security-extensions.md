---
title: Come installare le estensioni di sicurezza personalizzato | Documenti Microsoft
ms.custom: 
ms.date: 07/10/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: bfa0a35b-ccfb-4279-bae6-106c227c5f16
caps.latest.revision: 3
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 47182ebd082dfae0963d761e54c4045be927d627
ms.openlocfilehash: 58cfeef7d74e0641b965c307551f0fba4a7ff09c
ms.contentlocale: it-it
ms.lasthandoff: 07/11/2017

---

# Come installare le estensioni di sicurezza personalizzato
<a id="how-to-install-custom-security-extensions" class="xliff"></a>

[!INCLUDE[ssrs-appliesto](../../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../../includes/ssrs-appliesto-pbirs.md)]

Reporting Services 2016 è stato introdotto un nuovo portale web per ospitare nuovi APIs Odata e inoltre ospitare nuovi carichi di lavoro di report, ad esempio report per dispositivi mobili e indicatori KPI. Questo nuovo portale si basa su tecnologie più recenti e sia isolato dalla familiarità ReportingServicesService mediante l'esecuzione in un processo separato. Questo processo non è un'applicazione ASP.NET ospitata e in quanto tali interruzioni presupposti dalle estensioni di sicurezza personalizzato esistente. Inoltre, non consentono le interfacce corrente per estensioni di sicurezza personalizzate per qualsiasi contesto esterno in passato, lasciando i responsabili dell'implementazione con l'unica scelta per controllare oggetti ASP.NET globale noti, questa richiesta alcune modifiche all'interfaccia.

## Le novità?
<a id="what-changed" class="xliff"></a>

È stata introdotta una nuova interfaccia che può essere implementata che fornisce un IRSRequestContext che fornisce le proprietà più comuni utilizzate dalle estensioni per prendere decisioni relative all'autenticazione.

Nelle versioni precedenti, gestione Report è stato front-end e potrebbe essere configurato con la propria pagina di accesso personalizzata. In Reporting Services 2016, solo una pagina ospitata da reportserver è supportata e deve eseguire l'autenticazione in entrambe le applicazioni.

## Implementazione
<a id="implementation" class="xliff"></a>

Nelle versioni precedenti, le estensioni possono avvalersi un presupposto comune che gli oggetti ASP.NET deve essere immediatamente disponibili. Poiché il nuovo portale non viene eseguito in ASP.NET, l'estensione potrebbe riscontri problemi con gli oggetti che sono NULL.

L'esempio più generico accede HttpContext. Current per leggere le informazioni sulla richiesta, ad esempio le intestazioni e sui cookie. Per consentire le estensioni di prendere decisioni stesso è stato introdotto un nuovo metodo di estensione che fornisce informazioni sulla richiesta e viene chiamato quando l'autenticazione dal portale. 

Le estensioni sono necessario implementare la <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension2> interfaccia per sfruttare questa. Le estensioni dovranno implementare entrambe le versioni di <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension.GetUserInfo%2A> (metodo), come viene chiamato dal contesto reportserver e altri utilizzato nel processo di webhost. Nell'esempio seguente viene illustrata una delle implementazioni semplici per il portale in cui l'identità di risolvere il reportserver viene utilizzata.

``` 
public void GetUserInfo(IRSRequestContext requestContext, out IIdentity userIdentity, out IntPtr userId)
{
    userIdentity = null;
    if (requestContext.User != null)
    {
        userIdentity = requestContext.User;
    }

    // initialize a pointer to the current user id to zero
    userId = IntPtr.Zero;
}
```

## Distribuzione e configurazione
<a id="deployment-and-configuration" class="xliff"></a>

Le configurazioni di base necessari per l'estensione di sicurezza personalizzata sono le stesse versioni precedenti. Sono necessarie modifiche per Web. config e RSReportServer. config: per ulteriori informazioni, vedere [configurare personalizzata o autenticazione basata su form nel Server di Report](../../../reporting-services/security/configure-custom-or-forms-authentication-on-the-report-server.md).

Non è più un file Web. config per gestione Report separato, il portale erediteranno le stesse impostazioni dell'endpoint reportserver.

## Chiavi del computer
<a id="machine-keys" class="xliff"></a>

Nel caso dell'autenticazione basata su form che richiede la decrittografia del cookie di autenticazione, è necessario essere configurato con lo stesso algoritmo di chiave e la decrittografia macchina entrambi i processi. Si tratta di un passaggio familiare a coloro che aveva in precedenza l'installazione Reporting Services per funzionare in ambienti di scalabilità orizzontale, ma ora è un requisito anche per le distribuzioni in un singolo computer.

È consigliabile utilizzare una specifica chiave di convalida per la distribuzione, sono disponibili diversi strumenti per generare le chiavi, ad esempio Internet Information Services Manager (IIS). Altri strumenti sono disponibili su internet.

### SQL Server Reporting Services 2017 e versioni successive
<a id="sql-server-reporting-services-2017-and-later" class="xliff"></a>

**\ReportServer\rsReportServer.config**

Aggiungere sotto `<configuration>`.

```
<machineKey validationKey="[YOUR KEY]" decryptionKey=="[YOUR KEY]" validation="AES" decryption="AES" />
```

### SQL Server Reporting Services 2016
<a id="sql-server-reporting-services-2016" class="xliff"></a>

**\ReportServer\web.config**

Aggiungere sotto `<system.web>`.
    
```
    <machineKey validationKey="[YOUR KEY]" decryptionKey=="[YOUR KEY]" validation="AES" decryption="AES" />
```

**\RSWebApp\Microsoft.ReportingServices.Portal.Webhost.exe.config**

Aggiungere sotto `<configuration>`.

```
    <system.web>
        <machineKey validationKey=="[YOUR KEY]" decryptionKey=="[YOUR KEY]" validation="AES" decryption="AES" />
    </system.web>
```

### Server di report di Power BI
<a id="power-bi-report-server" class="xliff"></a>

È disponibile a partire dalla versione di giugno 2017 (Build 14.0.600.301).

**\ReportServer\rsReportServer.config**

Aggiungere sotto `<configuration>`.

```
<machineKey validationKey="[YOUR KEY]" decryptionKey=="[YOUR KEY]" validation="AES" decryption="AES" />
```

## Configurare i cookie pass-through
<a id="configure-passthrough-cookies" class="xliff"></a>

Il nuovo portale e il reportserver comunicano tramite soap interno API per alcune delle relative operazioni (simile alla precedente versione di gestione Report). Se sono richieste ulteriori cookie deve essere passato dal portale al server le proprietà PassThroughCookies è ancora disponibile. Per ulteriori informazioni, vedere [configurare il portale Web per passare i cookie di autenticazione personalizzato](../../../reporting-services/security/configure-the-web-portal-to-pass-custom-authentication-cookies.md).

```
<UI>
   <CustomAuthenticationUI>
      <PassThroughCookies>
         <PassThroughCookie>sqlAuthCookie</PassThroughCookie>
      </PassThroughCookies>
   </CustomAuthenticationUI>
</UI>
```

## Passaggi successivi
<a id="next-steps" class="xliff"></a>

[Configurazione personalizzata o autenticazione basata su form nel Server di Report](../../../reporting-services/security/configure-custom-or-forms-authentication-on-the-report-server.md)  
[Configurare Gestione Report per passare i cookie di autenticazione personalizzati](https://msdn.microsoft.com/library/ms345241(v=sql.120).aspx)

Ulteriori domande? [Provare a porre il forum di Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
