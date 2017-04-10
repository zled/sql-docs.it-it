---
title: "Opzione cancel (strumento di amministrazione Distributed Replay) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fea376de-307a-4b45-b7e2-37df88f3681a
caps.latest.revision: 15
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 15
---
# Opzione cancel (strumento di amministrazione Distributed Replay)
  Lo strumento di amministrazione Riesecuzione distribuita di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], **DReplay.exe**, è uno strumento da riga di comando che consente di comunicare con il controller di Riesecuzione distribuita. Questo argomento descrive l'opzione della riga di comando **cancel** e la sintassi corrispondente.  
  
 L'opzione **cancel** annulla l'operazione corrente in esecuzione nel controller.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.png "Icona di collegamento a un argomento") Per altre informazioni sulle convenzioni relative alla sintassi dello strumento di amministrazione, vedere [Convenzioni della sintassi Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## Sintassi  
  
```  
  
dreplay cancel [-m controller] [-q]   
```  
  
#### Parametri  
 *Controller* **-m**  
 Nome computer del controller. È possibile utilizzare "`localhost`" o "`.`" per fare riferimento al computer locale.  
  
 Se il parametro **-m** non è specificato, viene usato il computer locale.  
  
 **-q**  
 Modalità non interattiva. Non viene richiesta alcuna conferma da parte dell'utente.  
  
 Il parametro **-q** è facoltativo.  
  
## Esempi  
 Nell'esempio seguente viene inviata una richiesta di annullamento in modalità non interattiva. Il valore `localhost` indica che il servizio controller viene eseguito nello stesso computer dello strumento di amministrazione.  
  
```  
dreplay cancel –m localhost -q  
```  
  
## Autorizzazioni  
 È necessario eseguire lo strumento di amministrazione come utente interattivo, scegliendo tra utente locale e account utente di dominio. Per utilizzare un account utente locale, lo strumento di amministrazione e il controller devono essere eseguiti nello stesso computer.  
  
 Per altre informazioni, vedere [Sicurezza di Distributed Replay](../../tools/distributed-replay/distributed-replay-security.md).  
  
## Vedere anche  
 [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md)  
  
  