---
title: Gestione connessione FTP | Microsoft Docs
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
- FTP connection manager
- connections [Integration Services], FTP
- connection managers [Integration Services], FTP
ms.assetid: c4f43455-29ca-44ba-ac7f-ea729b1daf93
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 5e96a1a11651106cd0534ec20a3a35b79a9f1e7e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36168853"
---
# <a name="ftp-connection-manager"></a>gestione connessione FTP
  Una gestione connessione FTP consente la connessione di un pacchetto a un server FTP (File Transfer Protocol). Questa gestione connessione è usata dall'attività FTP inclusa in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Quando si aggiunge una gestione connessione FTP a un pacchetto, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crea una gestione connessione che in fase di esecuzione verrà risolta in una connessione FTP, imposta le proprietà della gestione connessione e quindi la aggiunge alla raccolta `Connections` del pacchetto.  
  
 Il `ConnectionManagerType` proprietà della gestione connessione è impostata su `FTP`.  
  
 Per configurare la gestione connessione FTP, procedere nel modo seguente:  
  
-   Specificare il nome e la porta del server.  
  
-   Specificare l'accesso anonimo oppure un nome utente e una password per l'autenticazione di base.  
  
    > [!IMPORTANT]  
    >  La gestione connessione FTP supporta solo l'autenticazione anonima e l'autenticazione di base. Non supporta l'autenticazione di Windows.  
  
-   Impostare il timeout, il numero di tentativi e la quantità di dati da copiare di volta in volta.  
  
-   Indicare se la gestione connessione FTP utilizza la modalità attiva o passiva.  
  
 A seconda della configurazione del sito FTP a cui si connette, può essere necessario modificare i seguenti valori predefiniti della gestione connessione FTP:  
  
-   La porta del server è impostata su 21. È necessario specificare la porta su cui è in ascolto il sito FTP.  
  
-   Il nome utente è impostato su "anonymous". È necessario specificare le credenziali richieste dal sito FTP.  
  
## <a name="activepassive-modes"></a>Modalità attiva e passiva  
 La gestione connessione FTP può inviare e ricevere file utilizzando la modalità attiva o passiva. Nella modalità attiva la connessione dati viene aperta dal server, mentre nella modalità passiva la connessione dati viene aperta dal client.  
  
## <a name="configuration-of-the-ftp-connection-manager"></a>Configurazione della gestione connessione FTP  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Per altre informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , vedere [Editor gestione connessione FTP](../ftp-connection-manager-editor.md).  
  
 Per informazioni sulla configurazione di una gestione connessione a livello di codice, vedere <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> e [aggiunta di connessioni a livello di programmazione](../building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività FTP](../control-flow/ftp-task.md)   
 [Servizi di integrazione &#40;SSIS&#41; le connessioni](integration-services-ssis-connections.md)  
  
  