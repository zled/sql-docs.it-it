---
title: Gestione connessione ODBC | Microsoft Docs
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
- connections [Integration Services], ODBC
- ODBC connection manager
- data sources [Integration Services], connections
- connection managers [Integration Services], ODBC
ms.assetid: e8c77aa7-6772-485e-918e-cef9eeb18c58
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 9453dc6e402fce60e1f4f440d84f882e513abea7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36068979"
---
# <a name="odbc-connection-manager"></a>gestione connessione ODBC
  Una gestione connessione ODBC consente la connessione di un pacchetto a un'ampia gamma di sistemi di gestione di database in base alla specifica ODBC (Open Database Connectivity).  
  
 Quando si aggiunge una connessione ODBC a un pacchetto e impostare le proprietà di gestione connessione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crea una gestione connessione e aggiunge la gestione connessione per il `Connections` raccolta del pacchetto. In fase di esecuzione la gestione connessione viene risolta in una connessione ODBC fisica.  
  
 Il `ConnectionManagerType` proprietà della gestione connessione è impostata su `ODBC`.  
  
 Per configurare la gestione connessione ODBC, procedere nel modo seguente:  
  
-   Specificare una stringa di connessione che fa riferimento al nome di un'origine dei dati utente o di sistema.  
  
-   Specificare il server a cui connettersi.  
  
-   Indicare se la connessione viene mantenuta in fase di esecuzione.  
  
## <a name="configuration-of-the-odbc-connection-manager"></a>Configurazione della gestione connessione ODBC  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Per altre informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , fare clic su uno degli argomenti seguenti:  
  
-   [Riferimento all'interfaccia utente di gestione connessione ODBC](../odbc-connection-manager-ui-reference.md)  
  
 Per informazioni sulla configurazione di una gestione connessione a livello di codice, vedere <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> e [aggiunta di connessioni a livello di programmazione](../building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Servizi di integrazione &#40;SSIS&#41; le connessioni](integration-services-ssis-connections.md)  
  
  