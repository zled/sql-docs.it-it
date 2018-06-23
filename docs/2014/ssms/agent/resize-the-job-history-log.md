---
title: Modificare le dimensioni del log di cronologia processi | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- jobs [SQL Server Agent], history
- resizing job history log
- size [SQL Server], job history log
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: ddee1ce8-9d1b-4017-9894-bf7256aed95d
caps.latest.revision: 26
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4ca02340ed14e94bc479f825a2e69702f31fb4d9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36158801"
---
# <a name="resize-the-job-history-log"></a>Modificare le dimensioni del log di cronologia processi
  In questo argomento viene illustrato come impostare le dimensioni massime per i log di cronologia dei processi di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
-   **Prima di iniziare:**  
  
     [Security](#Security)  
  
-   **Per impostare le dimensioni massime dei log della cronologia dei processi utilizzando:**  
  
     [SQL Server Management Studio](#SSMS)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
 Per informazioni dettagliate, vedere [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-resize-the-job-history-log-based-on-raw-size"></a>Per ridimensionare il log cronologia processi in base alle dimensioni dei dati non elaborati  
  
1.  In **Esplora oggetti** connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]ed espandere tale istanza.  
  
2.  Fare clic con il pulsante destro del mouse su **SQL Server Agent**, quindi scegliere **Proprietà**.  
  
3.  Nella pagina **Cronologia** verificare che la casella di controllo **Limita dimensioni log cronologia processi**sia selezionata.  
  
4.  Nella casella **Dimensioni massime log cronologia processi** immettere il numero massimo di righe consentito per il log cronologia processi.  
  
5.  Nella casella **Numero massimo di righe di cronologia per processo** immettere il numero massimo di righe di cronologia consentito per un processo.  
  
#### <a name="to-resize-the-job-history-log-based-on-time"></a>Per ridimensionare il log cronologia processi in base al tempo  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], quindi espandere questa istanza.  
  
2.  Fare clic con il pulsante destro del mouse su **SQL Server Agent**, quindi scegliere **Proprietà**.  
  
3.  Nella scheda **Cronologia** fare clic su **Rimuovi automaticamente cronologia dell'agente**.  
  
4.  Selezionare il numero appropriato di **giorno/i**, **settimana/e**o **mese/i**.  
  
  