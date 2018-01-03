---
title: Inviare commenti e suggerimenti dati di telemetria a Microsoft (SQL Server PDW)
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 40a994f0-7eff-4db9-9572-401d6e1187a0
caps.latest.revision: "18"
ms.openlocfilehash: f78a9e7c1e66085dd84ba71e8e7b5f517131e18a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="send-telemetry-feedback-to-microsoft"></a>Inviare commenti e suggerimenti dati di telemetria a Microsoft
Sistema della piattaforma Analitica dispone di una funzionalità di telemetria facoltativo che invia i dati della Console di amministrazione di Microsoft. È consigliabile abilitare questa opzione per contribuire a migliorare il prodotto.  
  
> [!NOTE]  
> In questa versione, Microsoft non monitora attivamente i dati di telemetria. Il dato viene raccolto solo a scopo di analisi.  
  
## <a name="privacy"></a>Privacy  
Per garantire la protezione della privacy massimo, i punti di accesso viene fornito senza abilitare la telemetria. Prima di abilitare questa funzionalità, esaminare il [informativa sulla Privacy di Microsoft Analitica piattaforma System](http://go.microsoft.com/fwlink/?LinkId=400902). Quindi, per fornire il consenso esplicito eseguire lo script di PowerShell descritto di seguito.  
  
## <a name="enable"></a>Attivare la telemetria  
**Inoltro di DNS:** l'invio di dati di telemetria a Microsoft richiede Analitica di sistema della piattaforma per la connessione a internet tramite un server d'inoltro DNS. Per abilitare questa funzionalità, è necessario abilitare DNS di inoltro in tutti gli host e macchine virtuali del carico di lavoro. Richiamare il `Enable-RemoteMonitoring` comando con il `SetupDnsForwarder` opzione per configurare l'inoltro di DNS e attivare la telemetria correttamente. Richiamare il `Enable-RemoteMonitoring` comando senza il `SetupDnsForwarder` durante l'inoltro di DNS è già configurato e si desidera abilitare il monitoraggio Heartbeat.  
  
> [!IMPORTANT]  
> Attivazione dell'inoltro DNS consente di aprire la connessione a internet per tutti gli host e macchine virtuali del carico di lavoro.  
  
#### <a name="to-enable-feedback"></a>Per abilitare i suggerimenti  
  
1.  Utilizzando un account di amministratore di dominio accessorio, connettersi al nodo di controllo (***appliance_domain*-CTL01**) e aprire un prompt dei comandi utilizzando le credenziali di amministratore di Windows.  
  
2.  Passare alla directory seguente: `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100`.  
  
3.  Importare il modulo`Configure-RemoteMonitoring.ps1`  
  
    > [!NOTE]  
    > Per importare è necessario utilizzare due punti nel comando.  
  
    **Esempio:**  
  
    ```  
    PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> . .\Configure-RemoteMonitoring.ps1  
    ```  
  
4.  Richiamare il `Enable-RemoteMonitoring` comando.  
  
    > [!NOTE]  
    > Lo script si presuppone che la connessione a internet funzioni correttamente e non convalida la connessione a internet.  
  
    1.  La prima volta che si abilita la telemetria, utilizzare il comando seguente per verificare che tutti i server d'inoltro DNS siano configurati correttamente. In questo esempio, sostituire l'indirizzo IP di inoltro DNS `xx.xx.xx.xx` con l'indirizzo IP del server d'inoltro DNS nell'ambiente in uso.  
  
        ```  
        PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> Enable-RemoteMonitoring -SetupDnsForwarder -DnsForwarderIp xx.xx.xx.xx  
        ```  
  
    2.  Quando i server d'inoltro DNS sono già configurati, ad esempio riabilitazione disabilitata in precedenza i dati di telemetria, utilizzare il comando seguente per attivare la telemetria senza configurare DNS di inoltro.  
  
        ```  
        PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> Enable-RemoteMonitoring  
        ```  
  
5.  Verrà richiesto di leggere e riconoscere che i punti di accesso verranno raccolte informazioni sull'accessorio. Sarà presente un collegamento all'informativa sulla privacy di punti di accesso che è possibile copiare e incollare in qualsiasi browser internet per la revisione.  
  
6.  Immettere **Y** per accettare e partecipare a commenti e suggerimenti oppure premere **N** per non accettare.  
  
7.  Se è stato immesso **Y** sarà presente una serie di comandi che verranno eseguiti in modo da consentire la telemetria (e, facoltativamente, il server d'inoltro DNS) funzionalità del dispositivo. Se vengono visualizzati eventuali errori o informazioni che determinano a pensare che il comando non è riuscito per assistenza contattare CSS.  
  
Se è stato immesso **N**, non verrà eseguito alcun comando e la funzionalità non verrà abilitata e non vi sono altre è necessario effettuare.  
  
Non causa problemi nell'esecuzione di `Enable-RemoteMonitoring` comando più volte. Se il server d'inoltro DNS è già impostato si riceverà un messaggio di avviso che indica che è il caso.  
  
## <a name="disable"></a>Disabilitare i dati di telemetria  
La disabilitazione di telemetria smetterà di tutte le operazioni che comunicano informazioni sullo stato del dispositivo per i punti di accesso monitoraggio del servizio nel cloud.  
  
> [!IMPORTANT]  
> Eseguire questa operazione non verrà disabilitato di server d'inoltro DNS o di una connessione internet che può essere utilizzato da altre funzionalità del dispositivo.  
  
#### <a name="to-disable-telemetry"></a>Per disabilitare i dati di telemetria  
  
1.  Utilizzando un account di amministratore di dominio accessorio, connettersi al nodo di controllo (***appliance_domain*-CTL01**) e aprire una finestra di PowerShell con privilegi di amministratore.  
  
2.  Passare alla directory seguente: `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100`.  
  
3.  Importare il modulo`Configure-RemoteMonitoring.ps1`  
  
    > [!NOTE]  
    > Per importare è necessario utilizzare due punti nel comando.  
  
    **Esempio:**  
  
    ```  
    PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> . .\Configure-RemoteMonitoring.ps1  
    ```  
  
4.  Richiamare il `Disable-RemoteMonitoring` comando senza parametri. Questo comando interrompe l'invio di commenti e suggerimenti. (Questa operazione non modificherà il monitoraggio locale.) Tuttavia, il comando verrà non disabilitare il server d'inoltro DNS e/o disabilitare qualsiasi connessione a internet. Questa operazione deve essere eseguita manualmente dopo correttamente la disabilitazione di commenti e suggerimenti.  
  
    **Esempio:**  
  
    ```  
    PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> Disable-RemoteMonitoring  
    ```  
  
Se vengono visualizzati eventuali errori o informazioni che determinano a pensare che il comando non è riuscito per assistenza contattare CSS.  
  
Non causa problemi nell'esecuzione di `Disable-RemoteMonitoring` comando più volte.  
  
## <a name="see-also"></a>Vedere anche  
[Monitorare il dispositivo tramite la Console di amministrazione &#40; Sistema della piattaforma Analitica &#41;](monitor-the-appliance-by-using-the-admin-console.md)  
[Monitorare l'accessorio utilizzando viste di sistema &#40; Sistema della piattaforma Analitica &#41;](monitor-the-appliance-by-using-system-views.md)  
[Monitorare il dispositivo con System Center Operations Manager &#40; Sistema della piattaforma Analitica &#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)  
[Utilizzare un server d'inoltro DNS per risolvere i nomi DNS Non strumento &#40; Sistema della piattaforma Analitica &#41;](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md)  
  
