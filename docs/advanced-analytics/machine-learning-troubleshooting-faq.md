---
title: Risoluzione dei problemi e domande frequenti per machine learning in SQL Server | Documenti Microsoft
ms.custom: 
ms.date: 06/16/2017
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9f1e93fafc4a6dcbbebb33577f5d6bfcef86adaa
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="troubleshoot-machine-learning"></a>Risoluzione dei problemi di apprendimento

Questo articolo fornisce informazioni sulla risoluzione dei problemi relativi a installazione e configurazione delle funzionalità di machine learning in SQL Server. Le informazioni includono i collegamenti alle guide di installazione, problemi noti e note sulla versione. Altri articoli collegata in questo articolo fornisce consigli sull'ottimizzazione delle prestazioni per le soluzioni di machine learning in SQL Server.

Utilizzare questa pagina come punto di partenza per la ricerca di problemi noti, domande di configurazione comuni e procedure per la risoluzione dei problemi.

**Si applica a:** R Services SQL Server 2016, SQL Server 2017 di Machine Learning Services (R e Python)

## <a name="known-issues"></a>Problemi noti

Gli articoli seguenti Elenca i problemi noti con la versione corrente o vengono descritti i problemi con le versioni precedenti:

+ [Problemi noti per R Services](../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)
+ [Note sulla versione di SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)
+ [Note sulla versione di SQL Server 2017](../sql-server/sql-server-2017-release-notes.md)

## <a name="troubleshooting-prerequisites"></a>Risoluzione dei problemi dei prerequisiti

Se si è verificato un errore o necessario comprendere un problema nell'ambiente in uso, è importante raccogliere le informazioni correlate in modo sistematico. Queste informazioni includono la versione, edizione, il contesto di sicurezza e contesto di esecuzione.

Il seguente articolo fornisce un elenco di informazioni che facilita la risoluzione dei problemi di risolvere autonomamente il problema o una richiesta per il supporto tecnico.

+ [Raccolta dei dati per la risoluzione dei problemi di apprendimento](data-collection-ml-troubleshooting-process.md)

## <a name="setup-and-configuration-guides"></a>Guide di installazione e configurazione

Iniziare da qui se non è stato configurato l'apprendimento con SQL Server o se si desidera aggiungere la funzionalità:

+ [Impostare i servizi R o Machine Learning con R](../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)
+ [Impostare i servizi di Machine Learning con Python](../advanced-analytics/python/setup-python-machine-learning-services.md)
+ [Domande frequenti del programma di installazione](../advanced-analytics/r/upgrade-and-installation-faq-sql-server-r-services.md)
+ [Utilizzare SqlBindR per aggiornare un'istanza di R services](../advanced-analytics/r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)

Gli articoli seguenti descrivono i passaggi aggiuntivi necessari per l'installazione offline di apprendimento di funzionalità del computer in SQL Server:

+ [Installazione automatica di R Services](../advanced-analytics/r/unattended-installs-of-sql-server-r-services.md) 
+ [Installazione automatica di servizi di Machine Learning con Python](../advanced-analytics/python/unattended-installs-of-sql-server-python-services.md)

Se è necessario installare di machine learning funzionalità in un computer senza stabilire una connessione Internet, utilizzare i collegamenti in questo articolo per scaricare i componenti di R e Python prima di iniziare l'installazione:

+ [Installazione di componenti di apprendimento automatico senza accesso a Internet](../advanced-analytics/r/installing-ml-components-without-internet-access.md)

### <a name="configuration"></a>Configurazione

Gli articoli seguenti contengono informazioni sulle impostazioni predefinite e come personalizzare la configurazione per machine learning in un'istanza di:

+ [Modificare il pool di account utente per SQL Server R Services](../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md)  
+ [Configurare e gestire le estensioni analitica avanzate](../advanced-analytics/r/configure-and-manage-advanced-analytics-extensions.md)  
+ [Come creare un pool di risorse](r/how-to-create-a-resource-pool-for-r.md)
+ [Ottimizzazione per carichi di lavoro R](r/operationalizing-your-r-code.md)

## <a name="related-tools-and-services"></a>Servizi e strumenti correlati

+ [Configurare Microsoft Machine Learning Server autonomo](../advanced-analytics/r/create-a-standalone-r-server.md)
+ [Configurare il Server di R in una macchina virtuale di Azure](../advanced-analytics/r/provision-the-r-server-only-sql-server-2016-enterprise-vm-on-azure.md)
+ [Installare R Server per Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows)
+ [Ottenere strumenti R per Visual Studio](https://www.visualstudio.com/vs/rtvs/)
