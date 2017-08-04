---
title: Guida SQL Server Configuration Manager | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Configuration Manager, help
ms.assetid: 6e909911-39a6-469b-b22a-3afdfd08a30b
caps.latest.revision: 28
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e7c3445dee2fe753506a02e9c828f1835664592a
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="sql-server-configuration-manager-help"></a>Guida di Gestione configurazione SQL Server
  Usare Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per configurare i servizi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e la connettività di rete. Per creare o gestire oggetti di database, configurare la sicurezza e scrivere query [!INCLUDE[tsql](../../includes/tsql-md.md)] , usare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Per altre informazioni su [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], vedere la documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 In questa sezione sono disponibili gli argomenti della Guida per le finestre di dialogo di Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Configuration Manager non è possibile configurare versioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anteriore [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
## <a name="services"></a>Servizi  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Configuration Manager consente di gestire i servizi correlati a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Sebbene molte delle funzioni di questo strumento equivalgano alle opzioni della finestra di dialogo Servizi di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, è importante sottolineare che Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] esegue operazioni aggiuntive sui servizi che gestisce, ad esempio applicando le autorizzazioni corrette quando si cambia l'account del servizio. L'utilizzo della finestra di dialogo Servizi Windows standard per configurare i servizi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] potrebbe provocare malfunzionamenti.  
  
 Usare Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per le operazioni seguenti:  
  
-   Avviare, arrestare e sospendere i servizi  
  
-   Configurare i servizi in modo che vengano avviati automaticamente o manualmente, disabilitare i servizi o modificare altre impostazioni  
  
-   Modificare le password degli account usati dai servizi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Avviare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mediante i flag di traccia (parametri della riga di comando)  
  
-   Visualizzare le proprietà dei servizi  
  
## <a name="sql-server-network-configuration"></a>Configurazione di rete SQL Server  
 Usare Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per le operazioni seguenti relative ai servizi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nel computer corrente:  
  
-   Abilitare o disabilitare un protocollo di rete di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Configurare un protocollo di rete di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
> [!NOTE]  
>  Per una breve esercitazione sulla configurazione di protocolli e sulla connessione di [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], vedere [Esercitazione: Introduzione al Motore di database](../../relational-databases/tutorial-getting-started-with-the-database-engine.md).  
  
## <a name="sql-server-native-client-configuration"></a>Configurazione SQL Server Native Client  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]i client si connettono a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzando il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] libreria di rete Client nativo. Utilizzare Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per le operazioni seguenti relative alle applicazioni client nel computer corrente:  
  
-   Per le applicazioni client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nel computer, specificare l'ordine dei protocolli quando si stabiliscono connessioni alle istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Configurare i protocolli di connessione client.  
  
-   Per le applicazioni client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , creare alias per le istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], in modo che i client possano connettersi usando una stringa di connessione personalizzata.  
  
 Per ulteriori informazioni su tali attività, vedere la Guida sensibile al contesto.  
  
#### <a name="to-open-sql-server-configuration-manager"></a>Per aprire Gestione configurazione SQL Server  
  
-   Dal menu **Start** scegliere **Tutti i programmi**, **Microsoft SQL Server** (versione), **Strumenti di configurazione**, quindi fare clic su **Gestione configurazione SQL Server**.  
  
## <a name="see-also"></a>Vedere anche  
 [Servizi SQL Server](../../tools/configuration-manager/sql-server-services.md)   
 [Configurazione di rete SQL Server](../../tools/configuration-manager/sql-server-network-configuration.md)   
 [Configurazione SQL Native Client 11.0](../../tools/configuration-manager/sql-native-client-11-0-configuration.md)   
 [Scelta di un protocollo di rete](http://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)  
  
  
