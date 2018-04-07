---
title: Tabella remota copia (SQL Server PDW)
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/13/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e00d948f-fede-4d41-a45d-67134770ce37
caps.latest.revision: 23
ms.openlocfilehash: fe6e808b8db8534f38db250d838d6a2cf132a30d
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="remote-table-copy"></a>Copia della tabella remota
Viene descritto come utilizzare la funzionalità di copia della tabella remota per copiare le tabelle dal database di SQL Server PDW ai database remoti di SMP SQL Server (non accessorio). Utilizzare tabella remota copy rende possibili scenari di hub e spoke per SQL Server PDW.  
  
## <a name="BasicsPDE"></a>Comprendere copia della tabella remota di SQL Server PDW  
Copia della tabella remota è una funzionalità di SQL Server PDW che consente scenari di Hub e Spoke, copiando i risultati di un'istruzione SQL SELECT in una tabella in un database SMP. La copia della tabella remota è stata avviata con il [CREATE REMOTE TABLE AS SELECT](../t-sql/statements/create-remote-table-as-select-parallel-data-warehouse.md) istruzione.  
  
## <a name="BasicsPrerequisites"></a>Requisiti per l'utilizzo di copia della tabella remota  
È possibile utilizzare le tabelle di copia per copiare la tabella remota da SQL Server PDW a un database di SQL Server quando vengono soddisfatte queste condizioni:  
  
-   Il database di destinazione deve essere un'istanza di Microsoft® SQL Server® che è in esecuzione in un sistema Microsoft Windows® che è possibile connettersi al dispositivo di SQL Server PDW ma non risiede su un server all'interno del dispositivo. Il Server SQL remoto può essere connesso a SQL Server PDW, utilizzare la rete InfiniBand o tramite rete Ethernet.  
  
-   I dati da copiare devono essere selezionabili utilizzando un singolo SQL Server PDW valido [selezionare](../t-sql/queries/select-transact-sql.md) istruzione.  
  
-   Il server di destinazione deve essere un server non appliance. Impossibile copiare i dati direttamente da un dispositivo a un altro utilizzando le istruzioni riportate in questo argomento.  
  
-   Il server di destinazione deve essere accessibile a tutti i nodi nella rete Infiniband del dispositivo.  
  
## <a name="ConfigureRemote"></a>Configurare una copia della tabella remota  
Per utilizzare una copia della tabella remota, è necessario acquistare e configurare un server Windows, configurare SQL Server in Windows server e configurare SQL Server PDW. Utilizzare i collegamenti seguenti per eseguire questi passaggi di configurazione di tre.  
  
1.  [Configurare un sistema di Windows esterno per la ricezione di copie di tabella remota utilizzando InfiniBand](configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband.md)  
  
2.  [Configurare un Server SQL SMP esterni per ricevono una copia di tabella remota](configure-an-external-smp-sql-server-to-receive-remote-table-copies.md)  
  
3.  [Configurare SQL Server PDW per copie tabella remota](configure-sql-server-pdw-for-remote-table-copies.md)  
  
## <a name="PerformRemote"></a>Eseguire una copia della tabella remota  
Per eseguire una copia della tabella remota, utilizzare il [CREATE REMOTE TABLE AS SELECT](../t-sql/statements/create-remote-table-as-select-parallel-data-warehouse.md) istruzione SQL. Esempi sono inclusi con l'argomento di CREATE REMOTE TABLE.  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
