---
title: Configurazione di servizi desktop remoto in Windows 2000 | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS configuration [ADO], Windows 2000
ms.assetid: ef37e858-c05f-4f52-a65f-3ce6037e0d03
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c1a85b322b48a19bd8b8d7bbf8777fe03c780371
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="configuring-rds-on-windows-2000"></a>Configurazione di servizi desktop remoto in Windows 2000
Se si riscontrano difficoltà nella Guida di servizi desktop remoto per funzionare correttamente dopo l'aggiornamento a Windows 2000, seguire questi passaggi per risolvere il problema:  
  
1.  Assicurarsi che il servizio pubblicazione sul Web sia in esecuzione, passare a http:// server con Internet Explorer. Se è Impossibile accedere al server Web in questo modo, aprire un prompt dei comandi e immettere il comando seguente, "NET START W3SVC".  
  
2.  Nel menu Start, scegliere Esegui. Digitare msdfmap e quindi fare clic su OK per aprire il file MSDFMAP nel blocco note. Controllare la sezione [CONNECT DEFAULT] e se il parametro di accesso è impostato su NOACCESS, modificarlo in sola lettura.  
  
3.  Tramite l'utilità RegEdit passare a "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DataFactory\HandlerInfo" e assicurarsi che **HandlerRequired** è impostato su 0 e **DefaultHandler** è "" (stringa Null).  
  
     **Nota** se si apportano modifiche a questa sezione del Registro di sistema, è necessario arrestare e riavviare il servizio pubblicazione sul Web immettendo i comandi seguenti al prompt dei comandi: "NET STOP W3SVC" e "NET START W3SVC".  
  
4.  Tramite l'utilità RegEdit passare nel Registro di sistema "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\W3SVC\Parameters\ADCLaunch" e verificare che sia presente una chiave denominata **RDSServer**. In caso contrario, crearla.  
  
5.  Utilizzando Gestione servizi Internet, individuare il sito Web predefinito e visualizzare le proprietà della radice virtuale MSADC. Controllare la Directory sicurezza/indirizzo IP e restrizioni nome dominio. Se il "accesso negato" è selezionato, quindi selezionare "Granted".  
  
 Assicurarsi di provare a riavviare il server se le modifiche non vengono visualizzati per risolvere il problema prima.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565). A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows. Eseguire la migrazione di applicazioni che utilizzano servizi desktop remoto per [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni fondamentali su RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


