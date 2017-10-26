---
title: "Aprire Monitoraggio attività (SQL Server Management Studio) | Microsoft Docs"
ms.custom: 
ms.date: 08/05/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Activity Monitor [SQL Server], setting the refresh interval
- refresh interval for Activity Monitor
- Activity Monitor [SQL Server], opening
- opening Activity Monitor
ms.assetid: 0a6eeb16-f02b-479d-9a60-543e40ebf46b
caps.latest.revision: 38
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 45e63d53b65730136bbc0a4f20ad5d4215020c58
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="open-activity-monitor-sql-server-management-studio"></a>Aprire Monitoraggio attività (SQL Server Management Studio)

   
 Monitoraggio attività esegue query sull'istanza monitorata per ottenere informazioni per i riquadri di visualizzazione di Monitoraggio attività. Quando l'intervallo di aggiornamento viene impostato su un valore inferiore a 10 secondi, il tempo utilizzato per eseguire queste query può ridurre le prestazioni del server  
  
  
##  <a name="Permissions"></a> Verificare le autorizzazioni.  
 Per visualizzare l'attività effettiva, è necessaria l'autorizzazione VIEW SERVER STATE. Per visualizzare la sezione I/O dati di file di Monitoraggio attività, è necessario disporre delle autorizzazioni CREATE DATABASE, ALTER ANY DATABASE, o VIEW ANY DEFINITION oltre a VIEW SERVER STATE.  
  
 Per eseguire il comando KILL in un processo, è necessario che l'utente sia un membro del ruolo predefinito del server sysadmin o processadmin.  
  
  
## <a name="open-activity-monitor"></a>Aprire Monitoraggio attività  

### <a name="keyboard-shortcut"></a>Scelta rapida da tastiera  
 - Digitare **CTRL+ALT+A** per aprire Monitoraggio attività in qualsiasi momento.

 >**Hint.** Passare il mouse su un'icona di SQL Server Management Studio per ottenere informazioni su che cos'è e sulla scelta rapida da tastiera che la attiva.

### <a name="toolbar"></a>Barra degli strumenti

Nella barra degli strumenti Standard fare clic sull'icona **Monitoraggio attività** . L'icona di trova al centro, subito a destra dei pulsanti di annullamento/ripristino.
![Activity_Monitor_icon](../../relational-databases/performance-monitor/media/activity-monitor-icon.png)  
  
Completare la finestra di dialogo **Connetti al server** se non si è già connessi a un'istanza di SQL Server da monitorare.
  
## <a name="launch-activity-monitor-and-object-explorer-on-startup"></a>Aprire Esplora oggetti e Monitoraggio attività all'avvio
  
1.  Dal menu **Strumenti** scegliere **Opzioni**.  
  
2.  Nella finestra di dialogo **Opzioni** espandere **Ambiente**, quindi selezionare **Avvio**.  
  
3.  Nell'elenco a discesa **All'avvio** selezionare **Apri Esplora oggetti e Monitoraggio attività**.  

4.  Scegliere **OK**.
  
![open_object_explorer](../../relational-databases/performance-monitor/media/open-object-explorer.png)
  
  
## <a name="set-the-activity-monitor-refresh-interval"></a>Impostare l'intervallo di aggiornamento di Monitoraggio attività  
  
1.   Aprire il Monitoraggio attività.  
  
2.   Fare clic con il pulsante destro del mouse su **Panoramica**, selezionare **Intervallo di aggiornamento**, quindi selezionare l'intervallo con cui Monitoraggio attività deve ottenere nuove informazioni sull'istanza.  
  
  

