---
title: Abilitare un server di report per l'accesso a Power BI per dispositivi mobili | Microsoft Docs
ms.date: 12/17/2015
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: report-server
ms.reviewer: ''
ms.suite: pro-bi
ms.custom: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c1a71522-394b-46a7-b9ec-f964bdd81d82
caps.latest.revision: 7
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 75c076dc02b7f268472a61270f8a1053d1a391cd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33025358"
---
# <a name="enable-a-report-server-for-power-bi-mobile-access"></a>Abilitare un server di report per l'accesso a Power BI per dispositivi mobili
Per utilizzare i report per dispositivi mobili, è possibile usare l'app Power BI per dispositivi mobili. Per consentire all'app Power BI per dispositivi mobili di connettersi a Reporting Services, è necessario configurare alcuni aspetti.  
  
-   [Modalità nativa di Reporting Services per i report per dispositivi mobili](#nativemode)  
-   [Abilitare l'autenticazione di base per Reporting Services](#basicauth) (per CTP 3.2)  
-   [Abilitare HTTPS con un certificato attendibile valido per il dispositivo client](#https)  
-   [Esaminare le impostazioni del firewall](#firewall)  
  
<a name="nativemode"/>  
## <a name="reporting-services-native-mode-required"></a>Modalità nativa di Reporting Services  
I report per dispositivi mobili sono una funzionalità della modalità nativa. Non sono disponibili nella modalità integrata di SharePoint. L'app Power BI per dispositivi mobili funziona solo con un'istanza in modalità nativa.  
  
<a name="basicauth"/>  
## <a name="enable-basic-authentication"></a>Abilitare l'autenticazione di base  
L'app Power BI per dispositivi mobili iOS richiede l'autenticazione di base per connettersi e utilizzare i report per dispositivi mobili. Reporting Services non è configurato con l'autenticazione di base abilitata per impostazione predefinita. Per informazioni su come configurare l'autenticazione di base, vedere l'articolo relativo alla [configurazione dell'autenticazione di base nel server di report](../../reporting-services/security/configure-windows-authentication-on-the-report-server.md).  
  
Per consentire all'applicazione di pubblicazione di pubblicare i report per dispositivi mobili, è necessario abilitare anche l'autenticazione di Windows.  
  
<a name="https"/>  
## <a name="enable-https"></a>Abilitare HTTPS  
Se si abilita l'autenticazione di base, in Reporting Services è consigliabile abilitare HTTPS. Se si abilita HTTPS, assicurarsi che i certificati usati possano essere considerati attendibili con i dispositivi client che eseguono l'app Power BI per dispositivi mobili iOS. Ciò significa che la catena di certificazione deve essere valida e disponibile per il dispositivo client.  
  
Se è necessario usare un certificato autofirmato per scopi di sviluppo o valutazione, è possibile esportare il certificato dal server di report e installarlo nel dispositivo mobile. Per informazioni sull'installazione del certificato nel dispositivo, consultare la documentazione del dispositivo.  
  
Per altre informazioni sull'abilitazione di SSL, vedere [Configurare connessioni SSL in un server di report in modalità nativa](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md).  
  
<a name="firewall"/>  
## <a name="review-firewall-settings"></a>Esaminare le impostazioni del firewall  
Si consiglia di controllare le impostazioni del firewall per assicurarsi che tutti i dispositivi possano connettersi correttamente a Reporting Services.   
  
Per altre informazioni su come configurare Windows Firewall, vedere [Configurare un firewall per l'accesso al server di report](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md).  
  
## <a name="see-also"></a>Vedere anche  
  
[configurazione dell'autenticazione di base nel server di report](../../reporting-services/security/configure-windows-authentication-on-the-report-server.md)  
[Configurare connessioni SSL in un server di report in modalità nativa](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md)  
[Configurare un firewall per l'accesso al server di report](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md)  
  
  
  
  
  
  

