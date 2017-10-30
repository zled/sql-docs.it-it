---
title: "SQL Server Integration Services (SSIS) scalabilità | Documenti Microsoft"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dcfbd1c5-c001-4fb7-b9ae-916e49ab6a96
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ce7fb96901e8af4da74392fe0a0a85c6e2ec05a4
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="integration-services-ssis-scale-out"></a>Scalabilità orizzontale di Integration Services (SSIS)
Il servizio di scalabilità orizzontale di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] consente di raggiungere elevate prestazioni nell'esecuzione dei pacchetti mediante la distribuzione dei processi su più computer. È possibile inviare una richiesta per più esecuzioni del pacchetto in SQL Server Management Studio. I pacchetti verranno eseguiti in parallelo, in modalità di scalabilità orizzontale.  

[!INCLUDE[ssIS_md](../../includes/ssis-md.md)]Orizzontale è costituito da un [!INCLUDE[ssIS_md](../../includes/ssis-md.md)] scala Out Master e uno o più [!INCLUDE[ssIS_md](../../includes/ssis-md.md)] scala i processi di lavoro. Il master di scalabilità orizzontale è responsabile della gestione del servizio di scalabilità orizzontale e riceve le richieste di esecuzione dei pacchetti dagli utenti. I ruoli di lavoro di scalabilità orizzontale effettuano il pull delle attività di esecuzione dal master e svolgono il lavoro di esecuzione dei pacchetti. Per altre informazioni, vedere [Master di scalabilità orizzontale](integration-services-ssis-scale-out-master.md) e [Ruolo di lavoro di scalabilità orizzontale](integration-services-ssis-scale-out-worker.md).

[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]Orizzontale può essere configurato in un computer, in cui una scala Out Master e una scala Out lavoro impostati side-by-side nel computer. ma anche su più computer, in ciascuno dei quali è installato un ruolo di lavoro.
- [Procedura dettagliata: Installare il servizio di scalabilità orizzontale di Integration Services](walkthrough-set-up-integration-services-scale-out.md)

La scalabilità orizzontale supporta l'esecuzione in parallelo di più pacchetti nel catalogo SSISDB. Per informazioni più dettagliate, vedere [Eseguire pacchetti nel servizio di scalabilità orizzontale](run-packages-in-integration-services-ssis-scale-out.md).

