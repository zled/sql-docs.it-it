---
title: Gestione connessione Analysis Services | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: connection-manager
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connections [Integration Services], Analysis Services
- connection managers [Integration Services], Analysis Services
- Analysis Services connection manager
ms.assetid: 9f9cadad-a1d0-4db5-98f5-df5dbbec1be4
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a140037121a7c33d23d6485c11684c0ba6a69505
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="analysis-services-connection-manager"></a>Analysis Services - gestione connessione
  Una gestione connessione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] consente la connessione di un pacchetto a un server che esegue un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] oppure a un progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] che permette di accedere ai dati di cubi e dimensioni. È possibile connettersi a un progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] solo durante lo sviluppo di pacchetti in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. In fase di esecuzione i pacchetti si connettono al server e al database in cui è stato distribuito il progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Sia le attività, ad esempio Esegui DDL [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ed Elaborazione [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], sia le destinazioni, ad esempio Training modello di data mining, usano la gestione connessione [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Per altre informazioni sui database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vedere [Database modelli multidimensionali &#40;SSAS&#41;](../../analysis-services/multidimensional-models/multidimensional-model-databases-ssas.md).  
  
## <a name="configuration-of-the-analysis-services-connection-manager"></a>Configurazione della Gestione connessione Analysis Services  
 Quando si aggiunge una gestione connessione [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] a un pacchetto, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crea una gestione connessione che in fase di esecuzione verrà risolta in una connessione [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , imposta le proprietà della gestione connessione e quindi aggiunge quest'ultima alla raccolta **Connections** del pacchetto. La proprietà **ConnectionManagerType** della gestione connessione viene impostata su **MSOLAP100**.  
  
 Per configurare la gestione connessione [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , procedere nel modo seguente:  
  
-   Specificare una stringa di connessione configurata in modo da soddisfare i requisiti del provider Microsoft OLE DB per Analysis Services.  
  
-   Specificare l'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] o il progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] al quale connettersi.  
  
-   Se ci si connette a un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], specificare la modalità di autenticazione.  
  
-   Indicare se la connessione creata dalla gestione connessione deve essere mantenuta in fase di esecuzione.  
  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Per altre informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , fare clic su uno degli argomenti seguenti:  
  
-   [Riferimento all'interfaccia utente della finestra di dialogo Aggiungi gestione connessione Analysis Services](../../integration-services/connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)  
  
 Per informazioni sulla configurazione di una gestione connessione a livello di programmazione, vedere l'articolo relativo a <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> e [Aggiunta di connessioni a livello di programmazione](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
  
