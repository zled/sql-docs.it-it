---
title: Registrazione di un oggetto Business personalizzato | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom business object in RDS [ADO]
- registering custom business objects in RDS [ADO]
- business objects in RDS [ADO]
ms.assetid: e9032ad8-d14c-42e3-ba13-cb5f00084a79
caps.latest.revision: "19"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c121ddf9e271f4dfb67490d77a719267cfa11a3b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="registering-a-custom-business-object"></a>Registrazione di un oggetto di Business personalizzata
Per avviare correttamente un oggetto business personalizzato (con estensione dll o .exe) tramite il server Web, ProgID dell'oggetto business deve essere immesso nel Registro di sistema, come illustrato in questa procedura. Questa funzionalità di servizi desktop remoto consente di proteggere la sicurezza del server Web tramite l'esecuzione di eseguibili attendibili.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
> [!NOTE]
>  Per MDAC 2.0 e versioni successive e Windows DAC, l'oggetto business predefinito, [RDSServer](../../../ado/reference/rds-api/datafactory-object-rdsserver.md), non è registrato per impostazione predefinita durante l'installazione di MDAC/Windows DAC. Tuttavia, se **RDSServer** è stato registrato come sicuro per l'esecuzione nel computer prima dell'installazione, viene mantenuta la voce del Registro di sistema per la nuova installazione.  
  
### <a name="to-register-a-custom-business-object"></a>Per registrare un oggetto business personalizzato:  
  
1.  Fare clic su **avviare** e quindi fare clic su **eseguire**.  
  
2.  Tipo **RegEdit** e fare clic su **OK**.  
  
3.  Spostarsi nell'Editor del Registro di sistema, il **HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\W3SVC\Parameters\ADCLaunch** chiave del Registro di sistema.  
  
4.  Selezionare il **ADCLaunch** chiave e quindi la **modifica**dal menu **New** e fare clic su **chiave**.  
  
5.  Digitare il ProgID dell'oggetto business personalizzato e fare clic su **invio**. Lasciare il **valore** voce vuota.


