---
title: Modificare le dimensioni del log di cronologia processi | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- resizing job history log
- size [SQL Server], job history log
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: ddee1ce8-9d1b-4017-9894-bf7256aed95d
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 64534d4f6dbf033dc4031a36343eaa0e12d21877
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47620799"
---
# <a name="resize-the-job-history-log"></a>Modificare le dimensioni del log di cronologia processi
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In [Istanza gestita di database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) sono attualmente supportate la maggior parte delle funzionalità di SQL Server Agent, ma non tutte. Per informazioni dettagliate, vedere [Differenze T-SQL tra Istanza gestita del database SQL di Azure e SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Questo argomento descrive come impostare le dimensioni massime per i log di cronologia dei processi di [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].
  
-   **Prima di iniziare:**  
  
    [Security](#Security)  
  
-   **Per impostare le dimensioni massime dei log della cronologia dei processi utilizzando:**  
  
    [SQL Server Management Studio](#SSMS)  
  
## <a name="BeforeYouBegin"></a>Prima di iniziare  
  
### <a name="Security"></a>Security  
Per informazioni dettagliate, vedere [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Utilizzo di SQL Server Management Studio  
  
*Per ridimensionare il log cronologia processi in base alle dimensioni dei dati non elaborati*
  
1.  In **Esplora oggetti** connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]ed espandere tale istanza.  
  
2.  Fare clic con il pulsante destro del mouse su **SQL Server Agent**, quindi scegliere **Proprietà**.  
  
3.  Nella pagina **Cronologia** verificare che la casella di controllo **Limita dimensioni log cronologia processi**sia selezionata.  
  
4.  Nella casella **Dimensioni massime log cronologia processi** immettere il numero massimo di righe consentito per il log cronologia processi.  
  
5.  Nella casella **Numero massimo di righe di cronologia per processo** immettere il numero massimo di righe di cronologia consentito per un processo.  
  
**Per ridimensionare il log cronologia processi in base al tempo:**
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)], quindi espandere questa istanza.  
  
2.  Fare clic con il pulsante destro del mouse su **SQL Server Agent**, quindi scegliere **Proprietà**.  
  
3.  Nella scheda **Cronologia** fare clic su **Rimuovi automaticamente cronologia dell'agente**.  
  
4.  Selezionare il numero appropriato di **Giorni**, **Settimane** o **Mesi**.  
  
