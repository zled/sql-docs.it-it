---
title: Gestione connessione WMI | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], WMI
- connection managers [Integration Services], WMI
- WMI connection manager [Integration Services]
ms.assetid: fbfa4ba7-3d0d-4d6b-94ad-50741a88d03d
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 86ed0766091f62f8666316fd38274bf59b9f9adf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48114321"
---
# <a name="wmi-connection-manager"></a>Gestione connessione WMI
  Una gestione connessione WMI consente a un pacchetto di utilizzare WMI (Windows Management Instrumentation, Strumentazione gestione Windows) per la gestione delle informazioni in un ambiente aziendale. Questa gestione connessione WMI è usata dall'attività Servizio Web inclusa in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Quando si aggiunge una gestione connessione WMI a un pacchetto, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crea una connessione di gestione che verrà risolta in una connessione di WMI in fase di esecuzione, imposta le proprietà di gestione connessione e aggiunge la gestione connessione per il `Connections` raccolta di pacchetto. Il `ConnectionManagerType` della gestione connessione viene impostata su `WMI`.  
  
## <a name="configuration-of-the-wmi-connection-manager"></a>Configurazione della gestione connessione WMI  
 Per configurare una gestione connessione WMI, procedere nel modo seguente:  
  
-   Specificare il nome di un server.  
  
-   Specificare uno spazio dei nomi sul server.  
  
-   Selezionare la modalità di autenticazione per la connessione al server.  
  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Per altre informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , vedere [Editor gestione connessione WMI](../wmi-connection-manager-editor.md).  
  
 Per informazioni sulla configurazione di una gestione connessione a livello di codice, vedere <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> e [aggiunta di connessioni a livello di programmazione](../building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività servizio Web](../control-flow/web-service-task.md)   
 [Integration Services &#40;SSIS&#41; le connessioni](integration-services-ssis-connections.md)  
  
  
