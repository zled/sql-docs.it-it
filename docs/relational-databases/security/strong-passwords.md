---
title: Password complesse | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- logins [SQL Server], passwords
- passwords [SQL Server], strong
- symbols [SQL Server]
- security [SQL Server], passwords
- passwords [SQL Server], symbols
- characters [SQL Server], password policies
- strong passwords [SQL Server]
ms.assetid: 338548f4-c4d8-47ca-b597-5c9c0f2fa205
caps.latest.revision: "30"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.openlocfilehash: 32a3c3b28c7db5155bf75cac5aed8229694c1486
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="strong-passwords"></a>Password complesse
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
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le password possono contenere fino a 128 caratteri, compresi lettere, simboli e cifre. Poiché gli account di accesso, i nomi utente, i ruoli e le password vengono spesso utilizzati in istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] , è necessario racchiudere alcuni simboli tra virgolette doppie (") o parentesi quadre ([ ]). Utilizzare questi delimitatori nelle istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] quando l'account di accesso, l'utente, il ruolo o la password di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] presenta le caratteristiche seguenti:  
  
-   Include o inizia con uno spazio.  
  
-   Inizia con il carattere $ o @.  
  
 Gli account di accesso e le password utilizzati in una stringa di connessione OLE DB o ODBC non devono includere i caratteri [] {}() , ; ? * ! @. Questi caratteri vengono utilizzati per inizializzare una connessione o per separare i relativi valori.  
  
## <a name="related-content"></a>Contenuto correlato  
 [Criteri password](../../relational-databases/security/password-policy.md)  
  
  
