---
title: Visualizzazione e arresto dell'esecuzione dei pacchetti nell'integrazione del Server Services | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- packages [Integration Services], managing
- managing running packages [Integration Services]
- packages [Integration Services], running
- running package [Integration Services], managing
ms.assetid: 11bf44e6-f6b0-475f-b816-40e914dbac80
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: ce4fd750986269c0e92ae2ea764f02e1bd642cb7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157802"
---
# <a name="viewing-and-stopping-packages-running-on-the-integration-services-server"></a>Visualizzazione e arresto dell'esecuzione dei pacchetti nel server Integration Services
  Il `SSISDB` database archivia la cronologia delle esecuzioni in tabelle interne che non sono visibili agli utenti. Tuttavia, nel database vengono esposte le informazioni necessarie tramite viste pubbliche su cui è possibile eseguire una query. Inoltre, sono disponibili stored procedure che è possibile chiamare per eseguire attività comuni correlate ai pacchetti.  
  
 In genere, gli oggetti di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] vengono gestiti nel server in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Tuttavia, è anche possibile eseguire query sulle viste del database e chiamare direttamente le stored procedure oppure scrivere codice personalizzato con cui chiamare l'API gestita. [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] e l'API gestita consentono di eseguire query sulle viste e chiamano le stored procedure per eseguire molte delle relative attività. È ad esempio possibile visualizzare l'elenco di pacchetti di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] attualmente in esecuzione nel server e, se necessario richiederne l'arresto.  
  
## <a name="viewing-the-list-of-running-packages"></a>Visualizzazione dell'elenco di pacchetti in esecuzione  
 È possibile visualizzare l'elenco di pacchetti attualmente in esecuzione nel server nella finestra di dialogo **Operazioni attive** . Per altre informazioni, vedere [Active Operations Dialog Box](../../2014/integration-services/active-operations-dialog-box.md).  
  
 Per informazioni su altri metodi utilizzabili per visualizzare l'elenco di pacchetti in esecuzione, vedere gli argomenti seguenti.  
  
 Accesso [!INCLUDE[tsql](../includes/tsql-md.md)]  
 Per visualizzare l'elenco di pacchetti in esecuzione nel server, eseguire una query sulla vista [catalog.executions &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-executions-ssisdb-database) per i pacchetti con stato 2.  
  
 Accesso a livello di codice tramite l'API gestita  
 Vedere lo spazio dei nomi <xref:Microsoft.SqlServer.Management.IntegrationServices> e le relative classi.  
  
## <a name="stopping-a-running-package"></a>Arresto di un pacchetto in esecuzione  
 È possibile richiedere l'arresto di un pacchetto in esecuzione nella finestra di dialogo **Operazioni attive** . Per altre informazioni, vedere [Active Operations Dialog Box](../../2014/integration-services/active-operations-dialog-box.md).  
  
 Per informazioni su altri metodi utilizzabili per arrestare un pacchetto in esecuzione, vedere gli argomenti seguenti.  
  
 Accesso [!INCLUDE[tsql](../includes/tsql-md.md)]  
 Per arrestare un pacchetto in esecuzione nel server, chiamare la stored procedure [catalog.stop_operation &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-stop-operation-ssisdb-database).  
  
 Accesso a livello di codice tramite l'API gestita  
 Vedere lo spazio dei nomi <xref:Microsoft.SqlServer.Management.IntegrationServices> e le relative classi.  
  
## <a name="viewing-the-history-of-packages-that-have-run"></a>Visualizzazione della cronologia dei pacchetti eseguiti  
 Per visualizzare la cronologia di pacchetti eseguiti in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], usare il report **Tutte le esecuzioni** . Per altre informazioni sul report **Tutte le esecuzioni** e gli altri report standard, vedere [Visualizzare i report per il server Integration Services](../../2014/integration-services/reports-for-the-integration-services-server.md).  
  
 Per informazioni su altri metodi utilizzabili per visualizzare la cronologia di pacchetti in esecuzione, vedere gli argomenti seguenti.  
  
 Accesso [!INCLUDE[tsql](../includes/tsql-md.md)]  
 Per visualizzare le informazioni sui pacchetti eseguiti, eseguire una query sulla vista [catalog.executions &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-executions-ssisdb-database).  
  
 Accesso a livello di codice tramite l'API gestita  
 Vedere lo spazio dei nomi <xref:Microsoft.SqlServer.Management.IntegrationServices> e le relative classi.  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di progetti e pacchetti](packages/run-integration-services-ssis-packages.md)   
 [Report per la risoluzione dei problemi relativi all'esecuzione dei pacchetti](troubleshooting/troubleshooting-reports-for-package-execution.md)  
  
  
