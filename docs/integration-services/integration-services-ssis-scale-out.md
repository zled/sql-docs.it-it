---
title: "Scalabilit&#224; orizzontale di Integration Services (SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dcfbd1c5-c001-4fb7-b9ae-916e49ab6a96
caps.latest.revision: 6
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 6
---
# Scalabilit&#224; orizzontale di Integration Services (SSIS)
Il servizio di scalabilità orizzontale di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] consente di raggiungere elevate prestazioni nell'esecuzione dei pacchetti mediante la distribuzione dei processi su più computer. È possibile inviare una richiesta per più esecuzioni di pacchetti in SQL Server Management Studio. I pacchetti verranno eseguiti in parallelo, in modalità di scalabilità orizzontale.  


## <a name="ssis-scale-out-master-and-scale-out-worker"></a>Master e ruolo di lavoro di scalabilità orizzontale di SSIS
Il servizio di scalabilità orizzontale di [!INCLUDE[ssIS_md](../includes/ssis-md.md)] è costituito da un master di scalabilità orizzontale di [!INCLUDE[ssIS_md](../includes/ssis-md.md)] e da più ruoli di lavoro di scalabilità orizzontale di [!INCLUDE[ssIS_md](../includes/ssis-md.md)]. Il master di scalabilità orizzontale è responsabile della gestione del servizio di scalabilità orizzontale e riceve le richieste di esecuzione dei pacchetti dagli utenti. I ruoli di lavoro di scalabilità orizzontale effettuano il pull delle attività di esecuzione dal master e svolgono il lavoro di esecuzione dei pacchetti. Per altre informazioni, vedere [Master di scalabilità orizzontale](../integration-services/integration-services-ssis-scale-out-master.md) e [Ruolo di lavoro di scalabilità orizzontale](../integration-services/integration-services-ssis-scale-out-worker.md).


## <a name="how-to-set-up-scale-out"></a>Come installare il servizio di scalabilità orizzontale
Il servizio di scalabilità orizzontale di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] può essere eseguito su un solo computer, in cui sono installati sia un master che un ruolo di lavoro, ma anche su più computer, in ciascuno dei quali è installato un ruolo di lavoro.
- [Procedura dettagliata: Installare il servizio di scalabilità orizzontale di Integration Services](../integration-services/walkthrough-set-up-integration-services-scale-out.md)


## <a name="run-packages-in-scale-out"></a>Eseguire pacchetti in modalità di scalabilità orizzontale
La scalabilità orizzontale supporta l'esecuzione in parallelo di più pacchetti nel catalogo SSISDB. Per informazioni più dettagliate, vedere [Eseguire pacchetti nel servizio di scalabilità orizzontale](../integration-services/run-packages-in-integration-services-ssis-scale-out.md).

