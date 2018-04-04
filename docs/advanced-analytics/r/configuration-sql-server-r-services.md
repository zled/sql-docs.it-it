---
title: Gestione e configurazione | Documenti Microsoft
ms.custom: ''
ms.date: 05/31/2016
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: Inactive
ms.openlocfilehash: e1db968dd15463dcfaf7fb4e55b5166b6310d264
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/04/2018
---
# <a name="configuration-and-management"></a>Configurazione e gestione
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo fornisce collegamenti a informazioni più dettagliate su come configurare un server per supportare i servizi di machine learning con SQL Server in questi prodotti:

+ SQL Server 2016 R Services (In-Database)
+ SQL Server 2017 Machine Learning Services (In-Database)

> [!NOTE]
> 
> Questo contenuto è stato scritto originariamente per la versione SQL Server 2016, supportato solo il linguaggio R.
> 
> In SQL Server 2017, il supporto per Python è stato aggiunto, ma il framework sottostante di architettura e i servizi è lo stesso. Pertanto, è possibile configurare sicurezza, memoria, la governance delle risorse e altre opzioni per supportare l'esecuzione di script Python, esattamente come si farebbe con gli script R.
> 
> Tuttavia, poiché il supporto per Python è una nuova funzionalità, le informazioni dettagliate sui potenziali ottimizzazioni per il carico di lavoro di Python non è ancora disponibile. Riprovare più tardi.

## <a name="r-package-management"></a>Gestione dei pacchetti R

Questi articoli viene descritto come installare i nuovi pacchetti di R nell'istanza di SQL Server, gestione delle librerie di pacchetti R e ripristinare librerie del pacchetto dopo un ripristino del database.

+ [Installazione e gestione dei pacchetti R](installing-and-managing-r-packages.md)
+ [Installazione di nuovi pacchetti R](install-additional-r-packages-on-sql-server.md)
+ [Abilitare la gestione dei pacchetti per un'istanza utilizzando i ruoli del Database](r-package-how-to-enable-or-disable.md)
+ [Creare un Repository di pacchetti locali utilizzando miniCRAN](create-a-local-package-repository-using-minicran.md)
+ [Determinare che quali pacchetti R vengono installati in SQl Server](determine-which-packages-are-installed-on-sql-server.md)
+ [La sincronizzazione dei pacchetti R tra SQL Server e il File System](package-install-uninstall-and-sync.md)
+ [Pacchetti R installati nelle librerie utente](packages-installed-in-user-libraries.md)

## <a name="service-configuration"></a>Configurazione del servizio

Questi articoli viene descritto come apportare modifiche per l'architettura del servizio sottostante e come gestire le entità di sicurezza associate al servizio di estendibilità.

+ [Considerazioni sulla sicurezza](security-considerations-for-the-r-runtime-in-sql-server.md)
+ [Modificare il pool di account utente per SQL Server R Services](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md)
+ [Configurare e gestire Advanced Analytics Extensions](../../advanced-analytics/r/configure-and-manage-advanced-analytics-extensions.md)
+ [Abilitare la gestione dei pacchetti per un'istanza utilizzando i ruoli del Database](r-package-how-to-enable-or-disable.md)
+ [Ottimizzazione delle prestazioni per R Services](sql-server-r-services-performance-tuning.md)

## <a name="resource-governance"></a>Governance delle risorse

Questi articoli viene descritto come implementare la gestione delle risorse per i processi R o Python con disponibile la funzionalità Resource Governor in Enterprise Edition.

+ [Governance delle risorse per R Services](../../advanced-analytics/r/resource-governance-for-r-services.md)
+ [Come creare un Pool di risorse per R](../../advanced-analytics/r/how-to-create-a-resource-pool-for-r.md)

Vedere anche:

+ [R di monitoraggio utilizzo dei report personalizzati di SSMS](monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="initial-setup"></a>Configurazione iniziale

Informazioni aggiuntive relative a configurazione e la configurazione iniziale sono reperibile in questi articoli:

+ [Domande frequenti sull'installazione e sull'aggiornamento](../r/upgrade-and-installation-faq-sql-server-r-services.md)
+ [Considerazioni sulla sicurezza](../r/security-considerations-for-the-r-runtime-in-sql-server.md)
+ [Problemi noti per R Services](../../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)

