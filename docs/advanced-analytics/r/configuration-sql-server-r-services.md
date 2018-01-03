---
title: Gestione e configurazione | Documenti Microsoft
ms.custom: 
ms.date: 05/31/2016
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e0fd4554-60c6-4181-ac4c-2e366fb434f6
caps.latest.revision: "7"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 075434e13ad8e988041eee360674ffcb59729312
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2017
---
# <a name="configuration-and-management"></a>Configurazione e gestione

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

Questi argomenti viene descritto come installare i nuovi pacchetti di R nell'istanza di SQL Server, gestione delle librerie di pacchetti R e ripristinare librerie del pacchetto dopo un ripristino del database.

+ [Installazione e gestione dei pacchetti R](installing-and-managing-r-packages.md)
+ [L'installazione di nuovi pacchetti R](install-additional-r-packages-on-sql-server.md)
+ [Abilitare la gestione dei pacchetti per un'istanza utilizzando i ruoli del Database](r-package-how-to-enable-or-disable.md)
+ [Creare un Repository di pacchetti locali utilizzando miniCRAN](create-a-local-package-repository-using-minicran.md)
+ [Determinare che i pacchetti R vengono installati in SQl Server](determine-which-packages-are-installed-on-sql-server.md)
+ [La sincronizzazione dei pacchetti R tra SQL Server e il File System](package-install-uninstall-and-sync.md)
+ [Pacchetti R installati nelle librerie utente](packages-installed-in-user-libraries.md)

## <a name="service-configuration"></a>Configurazione del servizio

Questi argomenti viene descritto come apportare modifiche all'architettura del servizio sottostante e come gestire le entità di sicurezza associate al servizio di estendibilità.

+ [Considerazioni sulla sicurezza](security-considerations-for-the-r-runtime-in-sql-server.md)
+ [Modificare il pool di account utente per SQL Server R Services](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md)
+ [Configurare e gestire Advanced Analytics Extensions](../../advanced-analytics/r/configure-and-manage-advanced-analytics-extensions.md)
+ [Abilitare la gestione dei pacchetti per un'istanza utilizzando i ruoli del Database](r-package-how-to-enable-or-disable.md)
+ [Ottimizzazione delle prestazioni per R Services](sql-server-r-services-performance-tuning.md)

## <a name="resource-governance"></a>Governance delle risorse

Questi argomenti viene descritto come implementare la gestione delle risorse per i processi di R o Python con il disponibili funzionalità Resource Governor in Enterprise Edition.

+ [Governance delle risorse per R Services](../../advanced-analytics/r/resource-governance-for-r-services.md)
+ [Come creare un Pool di risorse per R](../../advanced-analytics/r/how-to-create-a-resource-pool-for-r.md)

Vedere anche:

+ [R di monitoraggio utilizzando i report di SQL Server Management Studio personalizzato](monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="initial-setup"></a>Configurazione iniziale

In questi argomenti sono disponibili informazioni aggiuntive relative alla configurazione e la configurazione iniziale:

+ [Domande frequenti sull'installazione e sull'aggiornamento](../r/upgrade-and-installation-faq-sql-server-r-services.md)
+ [Considerazioni sulla sicurezza](../r/security-considerations-for-the-r-runtime-in-sql-server.md)
+ [Problemi noti per R Services](../../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)

