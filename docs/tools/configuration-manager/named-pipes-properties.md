---
title: "Propriet&#224; Named Pipes | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pipe [SQL Server]"
  - "attesa [SQL Server], pipe"
  - "pipe [SQL Server], attesa su pipe"
  - "named pipe [SQL Server], attesa su pipe"
ms.assetid: a5fd5b8e-f889-485b-89e3-d4010ec4c6ec
caps.latest.revision: 32
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 32
---
# Propriet&#224; Named Pipes
  La pagina **Protocollo** della finestra di dialogo **Proprietà - Named Pipes** consente di visualizzare o modificare la named pipe sulla quale [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resta in attesa quando è in uso il protocollo Named Pipes.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve essere riavviato per abilitare o disabilitare il protocollo oppure modificare la named pipe.  
  
## Opzioni  
 **Abilitata**  
 I valori possibili sono **Sì** e **No**.  
  
 **Nome pipe**  
 Specifica la named pipe sulla quale [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resta in attesa. Per impostazione predefinita, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resta in attesa su `\\.\pipe\sql\query` per l'istanza predefinita e su `\\.\pipe\MSSQL$<instancename>\sql\query` per un'istanza denominata. La lunghezza massima del campo è 2047 caratteri.  
  
## Creazione di una named pipe alternativa  
 Per modificare la named pipe, digitare il nome della nuova pipe nella casella **Nome pipe** e quindi arrestare e riavviare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Poiché è noto che **sql\query** è la named pipe usata da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], modificare la pipe può risultare utile per ridurre il rischio di attacco da parte di programmi dannosi.  
  
### Esempio  
 Digitare **\\\\.\pipe\unit\app** per impostare l'attesa sulla pipe **unit\app**.  
  
 Digitare **\\\\.\pipe\acct** per impostare l'attesa sulla pipe **acct**.  
  
## Vedere anche  
 [Abilitare o disabilitare un protocollo di rete del server](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)   
 [Scelta di un protocollo di rete](../Topic/Choosing%20a%20Network%20Protocol.md)   
 [Creazione di una stringa di connessione valida tramite named pipe](../Topic/Creating%20a%20Valid%20Connection%20String%20Using%20Named%20Pipes.md)  
  
  