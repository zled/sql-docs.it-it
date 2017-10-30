---
title: Viste (catalogo di Integration Services) | Documenti Microsoft
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- views [Integration Services]
ms.assetid: d0294d43-4852-46dc-9afa-d0c19ea9aa03
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b7293a70046df19eef816d3e7830518959ecbc98
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="views-integration-services-catalog"></a>Viste (catalogo di Integration Services)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  In questa sezione vengono descritte le viste [!INCLUDE[tsql](../../includes/tsql-md.md)] disponibili per l'amministrazione di progetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] distribuiti in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Query di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] viste per controllare oggetti, impostazioni e dati operativi archiviati nel **SSISDB** catalogo.  
  
 Il nome predefinito del catalogo è SSISDB. Tra gli oggetti archiviati nel catalogo sono inclusi progetti, pacchetti, parametri, ambienti e cronologia operativa.  
  
 È possibile utilizzare le viste del database e le stored procedure direttamente oppure scrivere codice personalizzato con cui chiamare l'API gestita. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] e l'API gestita eseguono query sulle viste e chiamano le stored procedure descritte in questa sezione per eseguire molte delle rispettive attività.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Catalog. catalog_properties &#40; Database SSISDB &#41;](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md)  
 Vengono visualizzate le proprietà del catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [Catalog. effective_object_permissions &#40; Database SSISDB &#41;](../../integration-services/system-views/catalog-effective-object-permissions-ssisdb-database.md)  
 Vengono visualizzate le autorizzazioni valide per l'entità corrente per tutti gli oggetti nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.environment_variables &#40;SSISDB Database&#41;](../../integration-services/system-views/catalog-environment-variables-ssisdb-database.md)  
 Vengono visualizzati i dettagli delle variabili di ambiente di tutti gli ambienti nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.environments &#40;SSISDB Database&#41;](../../integration-services/system-views/catalog-environments-ssisdb-database.md)  
 Vengono visualizzati i dettagli relativi all'ambiente di tutti gli ambienti nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Negli ambienti sono contenute variabili che possono fare riferimento ai progetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.execution_parameter_values &#40;SSISDB Database&#41;](../../integration-services/system-views/catalog-execution-parameter-values-ssisdb-database.md)  
 Vengono visualizzati i valori effettivi del parametro utilizzati dai pacchetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] durante un'istanza di esecuzione.  
  
 [catalog.executions &#40;SSISDB Database&#41;](../../integration-services/system-views/catalog-executions-ssisdb-database.md)  
 Vengono visualizzate le istanze di esecuzione del pacchetto nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. I pacchetti eseguiti con l'attività Esegui pacchetto vengono eseguiti nella stessa istanza di esecuzione del pacchetto padre.  
  
 [Catalog. explicit_object_permissions &#40; Database SSISDB &#41;](../../integration-services/system-views/catalog-explicit-object-permissions-ssisdb-database.md)  
 Vengono visualizzate solo le autorizzazioni assegnate in modo esplicito all'utente.  
  
 [catalog.extended_operation_info &#40;SSISDB Database&#41;](../../integration-services/system-views/catalog-extended-operation-info-ssisdb-database.md)  
 Vengono visualizzate le informazioni estese per tutte le operazioni nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [Catalog. Folders &#40; Database SSISDB &#41;](../../integration-services/system-views/catalog-folders-ssisdb-database.md)  
 Vengono visualizzate le cartelle nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.object_parameters &#40;SSISDB Database&#41;](../../integration-services/system-views/catalog-object-parameters-ssisdb-database.md)  
 Vengono visualizzati i parametri per tutti i pacchetti e progetti nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.object_versions &#40;SSISDB Database&#41;](../../integration-services/system-views/catalog-object-versions-ssisdb-database.md)  
 Vengono visualizzate le versioni di oggetti nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. In questa versione sono supportate solo le versioni di progetto in questa vista.  
  
 [catalog.operation_messages &#40;SSISDB Database&#41;](../../integration-services/system-views/catalog-operation-messages-ssisdb-database.md)  
 Vengono visualizzati i messaggi registrati durante le operazioni nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.operations &#40;SSISDB Database&#41;](../../integration-services/system-views/catalog-operations-ssisdb-database.md)  
 Vengono visualizzati i dettagli di tutte le operazioni nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.packages &#40;SSISDB Database&#41;](../../integration-services/system-views/catalog-packages-ssisdb-database.md)  
 Vengono visualizzati i dettagli di tutti i pacchetti visualizzati nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.environment_references &#40;SSISDB Database&#41;](../../integration-services/system-views/catalog-environment-references-ssisdb-database.md)  
 Vengono visualizzati i riferimenti all'ambiente per tutti i progetti nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.projects &#40;SSISDB Database&#41;](../../integration-services/system-views/catalog-projects-ssisdb-database.md)  
 Vengono visualizzati i dettagli per tutti i progetti visualizzati nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [Catalog. validations &#40; Database SSISDB &#41;](../../integration-services/system-views/catalog-validations-ssisdb-database.md)  
 Vengono visualizzati i dettagli di tutte le convalide del progetto e del pacchetto nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
[Catalog.master_properties &#40; Database SSISDB &#41;](../../integration-services/system-views/catalog-master-properties-ssisdb-database.md)  
Visualizza le proprietà del [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] scala Out Master.

[Catalog.worker_agents &#40; Database SSISDB &#41;](../../integration-services/system-views/catalog-worker-agents-ssisdb-database.md)  
Visualizza le informazioni di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] scala il lavoro.  

