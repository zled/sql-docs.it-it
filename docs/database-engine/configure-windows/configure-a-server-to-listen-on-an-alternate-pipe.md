---
title: Configurare un server per l'attesa su una pipe alternativa | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Named Pipes [SQL Server], configuring
- listening [SQL Server], pipes
- pipes [SQL Server], alternate
- alternate pipes [SQL Server]
ms.assetid: 914f7491-e2be-4b0d-b3aa-fe5409cdbafa
caps.latest.revision: "29"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 56ec0c83b27cc830a1614ad6232c28d2cac3c44f
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="configure-a-server-to-listen-on-an-alternate-pipe"></a>Configurare un server per l'attesa su una pipe alternativa
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Questo argomento illustra come configurare un server per l'ascolto su una pipe alternativa in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usando Gestione configurazione SQL Server. Per impostazione predefinita, l'istanza predefinita di [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] è in attesa sulla named pipe \\\\.\pipe\sql\query. Le istanze denominate del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] e [!INCLUDE[ssEW](../../includes/ssew-md.md)] sono in attesa su altre pipe.  
  
 È possibile connettersi a una named pipe specifica mediante un'applicazione client in tre modi differenti:  
  
-   Avviare il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser sul server.  
  
-   Creare un alias nel client, specificando la named pipe.  
  
-   Programmare il client affinché si connetta utilizzando una stringa di connessione personalizzata.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di Gestione configurazione SQL Server  
  
#### <a name="to-configure-the-named-pipe-used-by-the-sql-server-database-engine"></a>Per configurare l'utilizzo della named pipe mediante il Motore di database di SQL Server  
  
1.  Nel riquadro della console di Gestione configurazione SQL Server, espandere **Configurazione di rete SQL Server** e **Protocolli per** *\<nome istanza>*.  
  
2.  Nel riquadro dei dettagli fare clic con il pulsante destro del mouse su **Named pipe**, quindi scegliere **Proprietà**.  
  
3.  Nel riquadro **Nome pipe** della scheda **Protocollo** , specificare la pipe su cui si desidera che il [!INCLUDE[ssDE](../../includes/ssde-md.md)] sia in attesa e quindi fare clic su **OK**.  
  
4.  Nel riquadro della console fare clic su **Servizi di SQL Server**.  
  
5.  Nel riquadro dei dettagli fare clic con il pulsante destro del mouse su **SQL Server (**\<<nome istanza>**)** e scegliere **Riavvia**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verrà arrestato e riavviato.  
  
 Quando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in attesa su una pipe alternativa, è possibile connettersi a una named pipe specifica mediante un'applicazione client in tre modi differenti:  
  
-   Avviare il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser sul server.  
  
-   Creare un alias nel client, specificando la named pipe.  
  
-   Programmare il client affinché si connetta utilizzando una stringa di connessione personalizzata.  
  
## <a name="see-also"></a>Vedere anche  
 [Creare o eliminare un alias server per l'uso da parte di un client &#40;Gestione configurazione SQL Server Manager&#41;](../../database-engine/configure-windows/create-or-delete-a-server-alias-for-use-by-a-client.md)   
 [Configurazione di rete del server](../../database-engine/configure-windows/server-network-configuration.md)  
  
  
