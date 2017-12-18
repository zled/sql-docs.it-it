---
title: SQL Server Integration Services (SSIS) Scale Out | Microsoft Docs
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dcfbd1c5-c001-4fb7-b9ae-916e49ab6a96
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 0277d312ce4dab14e7ba64529e3eb2251a0d2d02
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="integration-services-ssis-scale-out"></a>Scalabilità orizzontale di Integration Services (SSIS)
Il servizio di scalabilità orizzontale di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] consente di raggiungere elevate prestazioni nell'esecuzione dei pacchetti mediante la distribuzione dei processi su più computer. È possibile inviare una richiesta per più esecuzioni di pacchetti in SQL Server Management Studio. I pacchetti verranno eseguiti in parallelo, in modalità di scalabilità orizzontale.  

[!INCLUDE[ssIS_md](../../includes/ssis-md.md)] Scale Out è costituito da un servizio [!INCLUDE[ssIS_md](../../includes/ssis-md.md)] Scale Out Master e da uno o più servizi [!INCLUDE[ssIS_md](../../includes/ssis-md.md)] Scale Out Worker. Il master di scalabilità orizzontale è responsabile della gestione del servizio di scalabilità orizzontale e riceve le richieste di esecuzione dei pacchetti dagli utenti. I ruoli di lavoro di scalabilità orizzontale effettuano il pull delle attività di esecuzione dal master e svolgono il lavoro di esecuzione dei pacchetti. Per altre informazioni, vedere [Master di scalabilità orizzontale](integration-services-ssis-scale-out-master.md) e [Ruolo di lavoro di scalabilità orizzontale](integration-services-ssis-scale-out-worker.md).

[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out può essere configurato su un solo computer in cui sono installati sia uno Scale Out Master che uno Scale Out Worker, ma anche su più computer, in ciascuno dei quali è installato un ruolo di lavoro.
- [Procedura dettagliata: Installare il servizio di scalabilità orizzontale di Integration Services](walkthrough-set-up-integration-services-scale-out.md)

La scalabilità orizzontale supporta l'esecuzione in parallelo di più pacchetti nel catalogo SSISDB. Per informazioni più dettagliate, vedere [Eseguire pacchetti nel servizio di scalabilità orizzontale](run-packages-in-integration-services-ssis-scale-out.md).
