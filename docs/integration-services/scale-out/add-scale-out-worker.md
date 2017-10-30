---
title: "Aggiungere una lavoro di scalabilità SSIS con scalabilità orizzontale Manager | Documenti Microsoft"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b769236330941a107865a0b133961bce5bf6b85b
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="add-a-scale-out-worker-with-scale-out-manager"></a>Aggiungere una scalabilità lavoro con scalabilità orizzontale Manager

Scala Out Gestione servizi di integrazione Elimina notevolmente la complessità per aggiungere lavoro Out di scalabilità orizzontale ambiente esistente. 

I passaggi seguenti consentono di aggiungere una scala il lavoro per la topologia orizzontale:

## <a name="1-install-scale-out-worker"></a>1. Installare la scalabilità orizzontale di lavoro
Nell'installazione guidata di SQL Server, selezionare Integration Services e scala il lavoro sul **Selezione funzionalità** pagina. 
![Selezione della funzionalità Ruolo di lavoro](media/feature-select-worker.PNG)

Nel **scala Out configurazione di Integration Services - nodo di lavoro** pagina, è possibile semplicemente fare clic su "Avanti" per ignorare la configurazione qui e usare **scala Out Manager** alla configurazione dopo l'installazione.

Completare l'installazione guidata.

## <a name="2-open-firewall-on-scale-out-master-computer"></a>2. Apre il firewall nel computer di scala Out Master
Aprire la porta specificata durante l'installazione di scala Out Master (8391, per impostazione predefinita) e la porta di SQL Server (1433 per impostazione predefinita), utilizza Windows Firewall nel computer Master Out di scala.

## <a name="3-add-scale-out-worker-with-scale-out-manager"></a>3. Aggiungere scalabilità lavoro con scalabilità orizzontale Manager
Eseguire SQL Server Management Studio come amministratore e connettersi all'istanza di SQL Server di scalabilità Out Master.

Fare doppio clic su **SSISDB** in Esplora oggetti e selezionare **gestire Scale Out...** . 

![Gestire la scalabilità orizzontale](media/manage-scale-out.PNG)

Nell'estratto di **scala Out Manager**, passare a **responsabile**. Fare clic su "+" pulsante e seguire le istruzioni nella finestra di dialogo connessione lavoro. Per informazioni dettagliate, vedere [scala Out Manager](integration-services-ssis-scale-out-manager.md).

