---
title: "Finestra di dialogo Operazioni attive | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.ssms.isoperations.executions.f1"
  - "sql13.ssis.ssms.isoperations.general.f1"
ms.assetid: 5bb0fcd6-0ce9-488a-85b8-25dddaa03cda
caps.latest.revision: 8
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# Finestra di dialogo Operazioni attive
  Utilizzare la finestra di dialogo **Operazioni attive** per visualizzare lo stato delle operazioni di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] attualmente in esecuzione nel server di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , ad esempio distribuzione, convalida ed esecuzione dei pacchetti. Questi dati vengono archiviati nel catalogo SSISDB.  
  
 Per altre informazioni sulle viste [!INCLUDE[tsql](../../includes/tsql-md.md)] correlate, vedere[catalog.operations &#40;SSISDB Database&#41;](../../integration-services/system-views/catalog-operations-ssisdb-database.md), [catalog.validations &#40;SSISDB Database&#41;](../../integration-services/system-views/catalog-validations-ssisdb-database.md) e [catalog.executions &#40;SSISDB Database&#41;](../../integration-services/system-views/catalog-executions-ssisdb-database.md)  
  
 **Per saperne di più**  
  
-   [Apertura della finestra di dialogo Operazioni attive](../../integration-services/performance/active-operations-dialog-box.md#open_dialog)  
  
-   [Opzioni](#options)  
  
##  <a name="open_dialog"></a> Apertura della finestra di dialogo Operazioni attive  
  
1.  Aprire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
2.  Connettersi al motore di database di Microsoft SQL Server.  
  
3.  In Esplora oggetti espandere il nodo **Integration Services**, fare clic con il pulsante destro del mouse su **SSISDB**, quindi fare clic su **Operazioni attive**.  
  
## Configurare le opzioni  
  
###  <a name="options"></a> Opzioni  
 **Tipo**  
 Consente di specificare il tipo di operazione. Di seguito sono riportati i valori possibili per il campo **Tipo** e i valori corrispondenti nella colonna operations_type della vista **catalog.operations** Transact-SQL.  
  
|||  
|-|-|  
|Inizializzazione di Integration Services|1|  
|Pulizia di operazioni (processo di SQL Agent)|2|  
|Pulizia delle versioni del progetto (processo di SQL Agent)|3|  
|Distribuzione del progetto|101|  
|Ripristino del progetto|106|  
|Creazione e avvio dell'esecuzione del pacchetto|200|  
|Arresto dell'operazione (arresto di una convalida o di un'esecuzione)|202|  
|Convalida del progetto|300|  
|Convalida del pacchetto|301|  
|Configurazione del catalogo|1000|  
  
 **Arresta**  
 Fare clic per arrestare un'operazione in esecuzione.  
  
  