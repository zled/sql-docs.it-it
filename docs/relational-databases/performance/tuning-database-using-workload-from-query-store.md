---
title: Ottimizzazione del database tramite un carico di lavoro dell'archivio query | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Database Engine Tuning Advisor, Query Store
ms.assetid: 17107549-5073-4fa2-8ee7-5ed33b38821e
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 7f89ed5e87b8fd51e8618a8559679225d91b32de
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="tuning-database-using-workload-from-query-store"></a>Ottimizzazione del database tramite un carico di lavoro dell'archivio query
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]


La funzionalità [Archivio query](../../relational-databases/performance/how-query-store-collects-data.md) di SQL Server acquisisce automaticamente una cronologia delle query, dei piani e delle statistiche di runtime e conserva queste informazioni nel database. [Ottimizzazione guidata motore di database (DTA)](../../relational-databases/performance/database-engine-tuning-advisor.md) supporta una nuova opzione che consente di usare l'archivio query per selezionare automaticamente un carico di lavoro appropriato per l'ottimizzazione. Per molti utenti, questo può eliminare la necessità di raccogliere esplicitamente un carico di lavoro per l'ottimizzazione. Questa funzionalità è disponibile solo se nel database è attivata la funzionalità Archivio query. 
  
  Questa funzionalità è disponibile con SQL Server Management Studio **16.4** o versione successiva. 
  
<a name="how-to-tune-a-workload-from-query-store-in-database-engine-tuning-advisor-gui"></a>Come ottimizzare un carico di lavoro dall'archivio query nella GUI di Ottimizzazione guidata motore di Database
---
Nella GUI di DTA selezionare il pulsante di opzione **Archivio query** nel riquadro **Generale** per abilitare la funzionalità (vedere la figura seguente).
![Carico di lavoro DTA dall'archivio query](../../relational-databases/performance/media/dta-workload-from-query-store.gif)
 
<a name="how-to-tune-a-workload-from-query-store-in-dtaexe-command-line-utility"></a>Come ottimizzare un carico di lavoro dall'archivio query nell'utilità della riga di comando dta.exe
---
Dalla riga di comando (dta.exe) scegliere l'opzione **-iq** per selezionare il carico di lavoro dall'archivio query. 

Tramite la riga di comando sono disponibili altre due opzioni che consentono di regolare il comportamento di DTA quando si seleziona il carico di lavoro dall'archivio query. Queste opzioni non disponibili tramite la GUI:
  1. Numero di eventi del carico di lavoro da ottimizzare: questa opzione, specificata usando l'argomento della riga di comando **-n**, consente all'utente di controllare il numero di eventi da Archivio query ottimizzati. Per impostazione predefinita, DTA usa il valore 1000 per questa opzione. Si noti che DTA sceglie sempre gli eventi con costo più elevato in termini di durata totale. 
  
  2. Intervalli di tempo degli eventi da ottimizzare: poiché l'archivio query può contenere query eseguite molto tempo fa, questa opzione consente all'utente di specificare un intervallo di tempo precedente (in ore) in cui una query deve essere stata eseguita per essere considerata da DTA per l'ottimizzazione. Questa opzione si specifica usando l'argomento della riga di comando **-I**. 

Per altre informazioni, vedere l'argomento sull'[utilità dta](../../tools/dta/dta-utility.md).

<a name="difference-between-using-workload-from-query-store-and-plan-cache"></a>Differenza tra l'uso del carico di lavoro dall'archivio query e dalla cache dei piani 
--- 
La differenza tra le opzioni Archivio query e Cache dei piani è che il primo contiene una cronologia più lunga delle query eseguite sul database, conservate tra i riavvii del server. D'altra parte, la cache dei piani contiene solo un subset di query eseguite di recente i cui piani sono memorizzati nella cache. Quando il server viene riavviato, le voci nella cache dei piani vengono eliminate.

<a name="see-also"></a>Vedere anche 
--- 
[Ottimizzazione guidata motore di database](../../relational-databases/performance/database-engine-tuning-advisor.md)     
[Esercitazione: Strumento Ottimizzazione guidata motore di database](Tutorial:%20Database%20Engine%20Tuning%20Advisor.md)     
[Come Archivio query raccoglie i dati](../../relational-databases/performance/how-query-store-collects-data.md)     
[Archivio query, procedure consigliate](../../relational-databases/performance/best-practice-with-the-query-store.md)

