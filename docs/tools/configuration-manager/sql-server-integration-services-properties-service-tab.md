---
title: "Proprietà (scheda servizio) SQL Server Integration Services | Documenti Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37f0acd9-c96f-48fd-9b53-2ca0097af242
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 53b926557561d244dbef987aaabe3fdcfeabbf70
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="sql-server-integration-services-properties-service-tab"></a>Proprietà - SQL Server Integration Services (scheda Servizio)
  Usare la scheda **Servizio**nella finestra di dialogo [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] **Proprietà** per visualizzare o specificare le opzioni seguenti.  
  
## <a name="options"></a>Opzioni  
 **Percorso binario**  
 Visualizza il percorso dei file di programma utilizzati dal servizio.  
  
 **Controllo errori**  
 1 indica `SERVICE_ERROR_NORMAL`. In caso di problemi di avvio del servizio durante l'avvio del computer, il programma di avvio registra l'errore e visualizza una finestra di messaggio popup ma continua l'operazione di avvio. Questo valore non può essere modificato.  
  
 **Codice di uscita**  
 Codice di errore di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows che definisce eventuali problemi verificatisi durante l'avvio o l'arresto del servizio. Questa proprietà viene impostata su **ERROR_SERVICE_SPECIFIC_ERROR** (1066) quando l'errore è univoco per il servizio rappresentato da questa classe. Le informazioni relative all'errore sono disponibili nella proprietà **ServiceSpecificExitCode** . Il servizio imposta questo valore su NO_ERROR (0) in fase di esecuzione e di nuovo al termine.  
  
 **Host Name**  
 Visualizza il nome del computer o del cluster che esegue il servizio [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 **Nome**  
 Indica il nome visualizzato del servizio.  
  
 **ID processo**  
 Visualizza l'ID di processo di Windows.  
  
 **Tipo di servizio SQL Server**  
 Visualizza il tipo di servizio fornito ai processi chiamanti. [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono installati diversi servizi.  
  
 **Modalità di avvio**  
 Impostare una delle opzioni seguenti per il servizio:  
  
-   Manuale: il servizio non viene avviato automaticamente all'avvio del computer. In questo caso è necessario avviare il servizio tramite Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o un altro strumento.  
  
-   Automatico: viene eseguito un tentativo automatico di avvio del servizio all'avvio del computer.  
  
-   Disabilitato: il servizio non può essere avviato.  
  
 **State**  
 Indica se il servizio è in esecuzione, arrestato o disabilitato. "**…**" indica una modifica di stato in sospeso.  
  
  

