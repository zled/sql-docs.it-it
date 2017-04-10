---
title: "Password complesse | Microsoft Docs"
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
  - "account di accesso [SQL Server], password"
  - "password [SQL Server], complesse"
  - "simboli [SQL Server]"
  - "sicurezza [SQL Server], password"
  - "password [SQL Server], simboli"
  - "caratteri [SQL Server], criteri password"
  - "password complesse [SQL Server]"
ms.assetid: 338548f4-c4d8-47ca-b597-5c9c0f2fa205
caps.latest.revision: 30
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 30
---
# Password complesse
  Le password possono costituire il punto debole nell'ambito distribuzione della sicurezza in un server. È dunque necessario prestare grande attenzione alla scelta delle password. Una password complessa ha le caratteristiche seguenti:  
  
-   È composta da almeno 8 caratteri.  
  
-   È costituita da una combinazione di lettere, numeri e simboli.  
  
-   Non è una parola presente nei dizionari.  
  
-   Non è il nome di un comando.  
  
-   Non è il nome di una persona.  
  
-   Non è il nome di un utente.  
  
-   Non è il nome di un computer.  
  
-   Viene modificata regolarmente.  
  
-   Presenta differenze sostanziali rispetto alle password precedenti.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le password possono contenere fino a 128 caratteri, compresi lettere, simboli e cifre. Poiché gli account di accesso, i nomi utente, i ruoli e le password vengono spesso utilizzati in istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)], è necessario racchiudere alcuni simboli tra virgolette doppie (") o parentesi quadre ([ ]). Utilizzare questi delimitatori nelle istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] quando l'account di accesso, l'utente, il ruolo o la password di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] presenta le caratteristiche seguenti:  
  
-   Include o inizia con uno spazio.  
  
-   Inizia con il carattere $ o @.  
  
 Gli account di accesso e le password utilizzati in una stringa di connessione OLE DB o ODBC non devono includere i caratteri [] {}() , ; ? * ! @. Questi caratteri vengono utilizzati per inizializzare una connessione o per separare i relativi valori.  
  
## Contenuto correlato  
 [Criteri password](../../relational-databases/security/password-policy.md)  
  
  