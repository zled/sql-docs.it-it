---
title: Gestione di connessione di SQL Server Compact Edition | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Compact, connection manager
- connections [Integration Services], SQL Server Compact
- connection managers [Integration Services], SQL Server Compact
ms.assetid: ba627d4d-41f4-49fc-a921-f534cde67770
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: dad3c3c379b62863de834386783b595c984c49ed
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="sql-server-compact-edition-connection-manager"></a>Gestione connessione SQL Server Compact Edition
  Una gestione connessione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact consente la connessione tra un pacchetto e un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact. La destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact inclusa in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] usa questa gestione connessione per caricare dati in una tabella di un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
> [!NOTE]  
>  In un computer a 64 bit è necessario eseguire pacchetti che si connettono a origini dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact in modalità a 32 bit. Il provider [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact usato in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] per la connessione a origini dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact è disponibile solo nella versione a 32 bit.  
  
## <a name="configuration-the-sql-server-compact-edition-connection-manager"></a>Configurazione della gestione connessione SQL Server Compact Edition  
 Quando si aggiunge una gestione connessione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact a un pacchetto, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crea una gestione connessione che in fase di esecuzione verrà risolta in una connessione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact, imposta le proprietà della gestione connessione e quindi la aggiunge alla raccolta **Connections** del pacchetto.  
  
 La proprietà **ConnectionManagerType** della gestione connessione viene impostata su **SQLMOBILE**.  
  
 Per configurare la gestione connessione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact, procedere nel modo seguente:  
  
-   Immettere una stringa di connessione che specifica il percorso del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
-   Se il database è protetto da password, specificare una password.  
  
-   Specificare il server in cui è archiviato il database.  
  
-   Indicare se la connessione creata dalla gestione connessione deve essere mantenuta in fase di esecuzione.  
  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Per ulteriori informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , fare clic su uno degli argomenti seguenti:  
  
-   [Editor gestione connessione SQL Server Compact Edition &#40;pagina Connessione&#41;](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager-editor-connection-page.md)  
  
-   [Editor gestione connessione SQL Server Compact Edition &#40;pagina Tutte&#41;](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager-editor-all-page.md)  
  
 Per informazioni sulla configurazione di una gestione connessione a livello di programmazione, vedere <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> e [Aggiunta di connessioni a livello di programmazione](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
  
