---
title: "Seleziona pacchetto | Microsoft Docs"
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
  - "sql13.dts.designer.selectapackage.f1"
helpviewer_keywords: 
  - "Seleziona pacchetto - finestra di dialogo"
ms.assetid: 92b47a2b-21b5-460a-885d-6cc4bb567249
caps.latest.revision: 16
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 16
---
# Seleziona pacchetto
  Utilizzare la finestra di dialogo **Seleziona pacchetto** per specificare il pacchetto da cui l'attività Message Queue può ricevere messaggi.  
  
## Opzioni statiche  
 **Percorso**  
 Consente di specificare il percorso del pacchetto. Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|Impostare il percorso su un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se si seleziona questo valore vengono visualizzate le opzioni dinamiche **Server**, **Usa autenticazione di Windows**, **Usa autenticazione di SQL Server**, **Nome utente**e **Password**.|  
|File DTSX|Consente di impostare il percorso su un file DTSX. Se si seleziona questo valore viene visualizzata l'opzione dinamica **Nome file**.|  
  
## Opzioni dinamiche relative al percorso  
  
### Percorso = SQL Server  
 **Nome pacchetto**  
 Consente di selezionare un pacchetto archiviato nel server specificato.  
  
 **Server**  
 Consente di specificare il nome del server o di selezionarlo nell'elenco.  
  
 **Usa autenticazione di Windows**  
 Fare clic su questa opzione per utilizzare l'autenticazione di Windows.  
  
 **Usa autenticazione di SQL Server**  
 Fare clic su questa opzione per usare l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Nome utente**  
 Se si usa l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], specificare il nome utente da usare per l'accesso al server.  
  
 **Password**  
 Se si usa l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], specificare una password.  
  
### Percorso = File DTSX  
 **Nome file**  
 Specificare il percorso di un pacchetto oppure fare clic sul pulsante Sfoglia **(…)** per individuare il pacchetto.  
  
## Vedere anche  
 [Attività Message Queue](../../integration-services/control-flow/message-queue-task.md)  
  
  