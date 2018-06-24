---
title: Gestione connessione SQL Server Compact Edition | Microsoft Docs
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
- SQL Server Compact, connection manager
- connections [Integration Services], SQL Server Compact
- connection managers [Integration Services], SQL Server Compact
ms.assetid: ba627d4d-41f4-49fc-a921-f534cde67770
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 5bbc62a0511bd77c1a4ab1f11c536f9480435b49
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065633"
---
# <a name="sql-server-compact-edition-connection-manager"></a>Gestione connessione SQL Server Compact Edition
  Una gestione connessione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact consente la connessione tra un pacchetto e un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact. La destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact inclusa in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] usa questa gestione connessione per caricare dati in una tabella di un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
> [!NOTE]  
>  In un computer a 64 bit è necessario eseguire pacchetti che si connettono a origini dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact in modalità a 32 bit. Il provider [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact usato in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] per la connessione a origini dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact è disponibile solo nella versione a 32 bit.  
  
## <a name="configuration-the-sql-server-compact-edition-connection-manager"></a>Configurazione della gestione connessione SQL Server Compact Edition  
 Quando si aggiunge un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gestione connessione Compact a un pacchetto [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crea una connessione di gestione che verrà risolto in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact connessione in fase di esecuzione, imposta le proprietà di gestione connessione e aggiunge la gestione connessione per il `Connections` raccolta nel pacchetto.  
  
 Il `ConnectionManagerType` proprietà della gestione connessione è impostata su `SQLMOBILE`.  
  
 Per configurare la gestione connessione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact, procedere nel modo seguente:  
  
-   Immettere una stringa di connessione che specifica il percorso del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
-   Se il database è protetto da password, specificare una password.  
  
-   Specificare il server in cui è archiviato il database.  
  
-   Indicare se la connessione creata dalla gestione connessione deve essere mantenuta in fase di esecuzione.  
  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Per ulteriori informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , fare clic su uno degli argomenti seguenti:  
  
-   [SQL Server Compact Edition Connection Manager Editor &#40;pagina di connessione&#41;](../sql-server-compact-edition-connection-manager-editor-connection-page.md)  
  
-   [SQL Server Compact Edition Connection Manager Editor &#40;pagina tutte&#41;](../sql-server-compact-edition-connection-manager-editor-all-page.md)  
  
 Per informazioni sulla configurazione di una gestione connessione a livello di codice, vedere <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> e [aggiunta di connessioni a livello di programmazione](../building-packages-programmatically/adding-connections-programmatically.md).  
  
  