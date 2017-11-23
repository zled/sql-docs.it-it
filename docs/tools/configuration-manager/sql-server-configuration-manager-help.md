---
title: Guida SQL Server Configuration Manager | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQL Server Configuration Manager, help
ms.assetid: 6e909911-39a6-469b-b22a-3afdfd08a30b
caps.latest.revision: "28"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 46fae234aa78b30fcb3f16bc4d7cf0db40228f8e
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="sql-server-configuration-manager-help"></a>Guida di Gestione configurazione SQL Server
  Usare Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per configurare i servizi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e la connettività di rete. Per creare o gestire oggetti di database, configurare la sicurezza e scrivere query [!INCLUDE[tsql](../../includes/tsql-md.md)] , usare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Per altre informazioni su [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], vedere la documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 In questa sezione sono disponibili gli argomenti della Guida per le finestre di dialogo di Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Configuration Manager non è possibile configurare versioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anteriore [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
## <a name="services"></a>Servizi  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Gestione configurazione SQL Server gestisce i servizi relativi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Sebbene molte delle funzioni di questo strumento equivalgano alle opzioni della finestra di dialogo Servizi di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, è importante sottolineare che Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] esegue operazioni aggiuntive sui servizi che gestisce, ad esempio applicando le autorizzazioni corrette quando si cambia l'account del servizio. L'utilizzo della finestra di dialogo Servizi Windows standard per configurare i servizi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] potrebbe provocare malfunzionamenti.  
  
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
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] I client SQL Server si connettono a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite la libreria di rete [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Utilizzare Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per le operazioni seguenti relative alle applicazioni client nel computer corrente:  
  
-   Per le applicazioni client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nel computer, specificare l'ordine dei protocolli quando si stabiliscono connessioni alle istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Configurare i protocolli di connessione client.  
  
-   Per le applicazioni client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , creare alias per le istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], in modo che i client possano connettersi usando una stringa di connessione personalizzata.  
  
 Per ulteriori informazioni su tali attività, vedere la Guida sensibile al contesto.  
  
#### <a name="to-open-sql-server-configuration-manager"></a>Per aprire Gestione configurazione SQL Server  
  
-   Dal menu **Start** scegliere **Tutti i programmi**, **Microsoft SQL Server** (versione), **Strumenti di configurazione**, quindi fare clic su **Gestione configurazione SQL Server**.  
  
  
 **Per accedere a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Using Configuration Manager[!INCLUDE[win8](../../includes/win8-md.md)]**  
  
 Poiché Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è uno snap-in per il programma [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console e non un programma autonomo, Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non viene visualizzato come applicazione durante l'esecuzione di [!INCLUDE[win8](../../includes/win8-md.md)]. Per aprire Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , nell'icona promemoria **Cerca** in **App**digitare **SQLServerManager12.msc** (per [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]) o **SQLServerManager11.msc** per ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) e quindi premere **INVIO**.  
  

## <a name="see-also"></a>Vedere anche  
 [Servizi di SQL Server](../../tools/configuration-manager/sql-server-services.md)   
 [Configurazione di rete SQL Server](../../tools/configuration-manager/sql-server-network-configuration.md)   
 [Configurazione SQL Native Client 11.0](../../tools/configuration-manager/sql-native-client-11-0-configuration.md)   
 [Scelta di un protocollo di rete](http://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)  
  
  
