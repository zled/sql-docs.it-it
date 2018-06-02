---
title: Risoluzione dei problemi e domande frequenti per machine learning in SQL Server | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 6ef72ae56973e695b96f0dfac7c0a3414bca5225
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/01/2018
ms.locfileid: "34707359"
---
# <a name="troubleshoot-machine-learning-in-sql-server"></a>Risolvere i problemi di apprendimento automatico in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Utilizzare questa pagina come punto di partenza per affrontare i problemi noti.

**Si applica a:** R Services SQL Server 2016, SQL Server 2017 di Machine Learning Services (R e Python)

## <a name="known-issues"></a>Problemi noti

Gli articoli seguenti descrivono i problemi noti con le versioni corrente e precedente:

+ [Problemi noti per R Services](../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)
+ [Note sulla versione di SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)
+ [Note sulla versione di SQL Server 2017](../sql-server/sql-server-2017-release-notes.md)

## <a name="how-to-gather-system-information"></a>Come raccogliere informazioni di sistema

Se si è verificato un errore o necessario comprendere un problema nell'ambiente in uso, è importante raccogliere le informazioni correlate in modo sistematico. Il seguente articolo fornisce un elenco di informazioni che facilita la risoluzione dei problemi di risolvere autonomamente il problema o una richiesta per il supporto tecnico.

+ [Raccolta dei dati per la risoluzione dei problemi di apprendimento automatico](data-collection-ml-troubleshooting-process.md)

## <a name="setup-and-configuration-guides"></a>Guide di installazione e configurazione

Iniziare da qui se non è stato configurato l'apprendimento con SQL Server o se si desidera aggiungere la funzionalità:

+ [Installare SQL Server 2017 Machine Learning Services (In-Database)](install/sql-machine-learning-services-windows-install.md)
+ [Installazione di SQL Server 2017 Machine Learning Server (Standalone)](install/sql-machine-learning-standalone-windows-install.md)
+ [Installare SQL Server 2016 R Services (In-Database)](install/sql-r-services-windows-install.md)
+ [Installare SQL Server 2016 R Server (Standalone)](install/sql-r-standalone-windows-install.md)
+ [Programma di installazione di prompt dei comandi](install/sql-ml-component-commandline-install.md)
+ [Installazione offline (senza Internet)](install/sql-ml-component-install-without-internet-access.md)

### <a name="configuration"></a>Configurazione

Gli articoli seguenti contengono informazioni sulle impostazioni predefinite e come personalizzare la configurazione per machine learning in un'istanza di:

+ [Modificare il pool di account utente per SQL Server R Services](r/modify-the-user-account-pool-for-sql-server-r-services.md)  
+ [Configurare e gestire le estensioni analitica avanzate](r/configure-and-manage-advanced-analytics-extensions.md)  
+ [Come creare un pool di risorse](r/how-to-create-a-resource-pool-for-r.md)
+ [Ottimizzazione per carichi di lavoro R](r/operationalizing-your-r-code.md)
