---
title: Gestione connessione SMTP | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], SMTP
- SMTP connection manager [Integration Services]
- connection managers [Integration Services], SMTP
ms.assetid: 3795d442-714b-4bbb-9acd-75bf277a468a
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b05612ac34e4c2e7eb412d59eb9dcf5f28e99c78
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37213481"
---
# <a name="smtp-connection-manager"></a>Gestione connessione SMTP
  Una gestione connessione SMTP consente a un pacchetto di connettersi a un server SMTP (Simple Mail Transfer Protocol). Questa gestione connessione è usata dall'attività Invia messaggi inclusa in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Quando si utilizza Microsoft Exchange come server SMTP, potrebbe essere necessario configurare la gestione connessione SMTP per utilizzare l'autenticazione di Windows. È possibile configurare i server Exchange in modo da non consentire connessioni SMTP non autenticate.  
  
## <a name="configuration-the-smtp-connection-manager"></a>Configurazione della gestione connessione SMTP  
 Quando si aggiunge una gestione connessione SMTP a un pacchetto, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crea una connessione di gestione che verrà risolta in una connessione di SMTP in fase di esecuzione, imposta le proprietà di gestione connessione e aggiunge la gestione connessione per il `Connections` raccolta di pacchetto. Il `ConnectionManagerType` della gestione connessione viene impostata su `SMTP`.  
  
 Per configurare la gestione connessione SMTP, procedere nel modo seguente:  
  
-   Specificare una stringa di connessione.  
  
-   Specificare il nome di un server SMTP.  
  
-   Specificare il metodo di autenticazione da utilizzare.  
  
    > [!IMPORTANT]  
    >  La gestione connessione SMTP supporta solo l'autenticazione anonima e l'autenticazione di Windows. Non supporta l'autenticazione di base.  
  
-   Specificare se crittografare la comunicazione mediante SSL (Secure Sockets Layer) quando si inviano messaggi di posta elettronica.  
  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Per altre informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , vedere [Editor gestione connessione SMTP](../smtp-connection-manager-editor.md).  
  
 Per informazioni sulla configurazione di una gestione connessione a livello di codice, vedere <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> e [aggiunta di connessioni a livello di programmazione](../building-packages-programmatically/adding-connections-programmatically.md).  
  
  
