---
title: Modificare l'indirizzo IP di un'istanza del cluster di failover | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: ''
ms.component: failover-clusters
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- modifying IP addresses
- failover clustering [SQL Server], IP addresses
- IP addresses [SQL Server]
- clusters [SQL Server], IP addresses
ms.assetid: b685f400-cbfe-4c5d-a070-227a1123dae4
caps.latest.revision: 33
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 692598e4fa27e18c40767d14e46aa48d4d03d265
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="change-the-ip-address-of-a-failover-cluster-instance"></a>Modifica dell'indirizzo IP di un'istanza del cluster di failover
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In questo argomento viene descritto come modificare la risorsa indirizzo IP nell'istanza del cluster di failover (FCI) di Always On tramite lo snap-in Gestione cluster di failover. Lo snap-in Gestione cluster di failover è l'applicazione di gestione cluster per il servizio Windows Server Failover Clustering (WSFC).  
  
-   **Before you begin:**  [Security](#Security)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
 Prima di iniziare, esaminare il seguente argomento della documentazione online di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] : [Operazioni preliminari all'installazione del clustering di failover](../../../sql-server/failover-clusters/install/before-installing-failover-clustering.md).  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 Per eseguire la manutenzione o l'aggiornamento di un'istanza FCI, è necessario essere un amministratore locale che dispone dell'account per accedere come servizio su tutti i nodi dell'istanza FCI.  
  
##  <a name="WSFC"></a> Utilizzo dello snap-in Gestione cluster di failover  
 **Per modificare la risorsa indirizzo IP per un'istanza FCI**  
  
1.  Aprire lo snap-in Gestione cluster di failover.  
  
2.  Espandere il nodo **Servizi e applicazioni** nel riquadro sinistro e fare clic sull'istanza FCI.  
  
3.  Nel riquadro a destra, nella categoria **Nome server** , fare clic con il pulsante destro del mouse sul'istanza di SQL Server e scegliere **Proprietà** per aprire la finestra di dialogo **Proprietà** .  
  
4.  Nella scheda **Generale** , modificare la risorsa indirizzo IP.  
  
5.  Scegliere **OK** per chiudere la finestra di dialogo.  
  
6.  Nel riquadro destro fare clic con il pulsante destro del mouse su SQL IP Address1(nome dell'istanza del cluster di failover) e scegliere **Offline**. Lo stato di SQL IP Address1(nome dell'istanza del cluster di failover), di SQL Network Name(nome dell'istanza del cluster di failover) e di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] passerà da Online a Sospensione offline e quindi a Offline.  
  
7.  Nel riquadro destro fare clic con il pulsante destro del mouse su [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]e scegliere **Online**. Lo stato di SQL IP Address1(nome dell'istanza del cluster di failover), di SQL Network Name(nome dell'istanza del cluster di failover) e di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] passerà da Offline a Sospensione online e quindi a Online.  
  
8.  Chiudere lo snap-in Gestione cluster di failover.  
  
  
