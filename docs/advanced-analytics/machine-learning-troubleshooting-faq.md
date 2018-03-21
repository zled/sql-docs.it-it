---
title: Risoluzione dei problemi e domande frequenti per machine learning in SQL Server | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2018
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.workload: Inactive
ms.openlocfilehash: 5b9a5c6497781ef67d9d2ef9b9032a4d9ee250e5
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2018
---
# <a name="troubleshoot-machine-learning"></a>Risolvere i problemi di apprendimento automatico
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo fornisce collegamenti alla risoluzione dei problemi sulle guide all'installazione, i problemi noti e note sulla versione. Altri articoli collegata in questo articolo fornisce consigli sull'ottimizzazione delle prestazioni per le soluzioni di machine learning in SQL Server.

Utilizzare questa pagina come punto di partenza per la ricerca di problemi noti, domande frequenti di programma di installazione e le procedure per la risoluzione dei problemi.

**Si applica a:** R Services SQL Server 2016, SQL Server 2017 di Machine Learning Services (R e Python)

## <a name="known-issues"></a>Problemi noti

Gli articoli seguenti per elencare i problemi noti con la versione corrente oppure vengono descritti i problemi con le versioni precedenti:

+ [Problemi noti per R Services](../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)
+ [Note sulla versione di SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)
+ [Note sulla versione di SQL Server 2017](../sql-server/sql-server-2017-release-notes.md)

## <a name="troubleshooting-prerequisites"></a>Risoluzione dei problemi dei prerequisiti

Se si è verificato un errore o necessario comprendere un problema nell'ambiente in uso, è importante raccogliere le informazioni correlate in modo sistematico. Queste informazioni includono la versione, edizione, contesto di sicurezza e contesto di esecuzione.

L'articolo seguente fornisce un elenco di informazioni che facilita la risoluzione dei problemi di risolvere autonomamente il problema o una richiesta per il supporto tecnico.

+ [Raccolta dei dati per la risoluzione dei problemi di apprendimento automatico](data-collection-ml-troubleshooting-process.md)

## <a name="setup-and-configuration-guides"></a>Guide di installazione e configurazione

Iniziare da qui se non è stato configurato apprendimento con SQL Server o se si desidera aggiungere la funzionalità:

+ [Installare SQL Server 2017 Machine Learning Services (In-Database)](install/sql-machine-learning-services-windows-install.md)
+ [Installazione di SQL Server 2017 Machine Learning Server (Standalone)](install/sql-machine-learning-standalone-windows-install.md)
+ [Installare SQL Server 2016 R Services (In-Database)](install/sql-r-services-windows-install.md)
+ [Installazione di SQL Server 2016R Server (Standalone)](install/sql-r-standalone-windows-install.md)
+ [Programma di installazione di prompt dei comandi](install/sql-ml-component-commandline-install.md)
+ [Programma di installazione offline (nessuna internet)](install/sql-ml-component-install-without-internet-access.md)

### <a name="configuration"></a>Configurazione

Gli articoli seguenti contengono informazioni sui valori predefiniti e su come personalizzare la configurazione per machine learning in un'istanza:

+ [Modificare il pool di account utente per SQL Server R Services](r/modify-the-user-account-pool-for-sql-server-r-services.md)  
+ [Configurare e gestire le estensioni analitica avanzate](r/configure-and-manage-advanced-analytics-extensions.md)  
+ [Come creare un pool di risorse](r/how-to-create-a-resource-pool-for-r.md)
+ [Ottimizzazione per carichi di lavoro R](r/operationalizing-your-r-code.md)
