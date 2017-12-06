---
title: Impostazione delle opzioni dello strumento e il Layout | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: dta
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-query-tuning
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
helpviewer_keywords: Database Engine [SQL Server], tutorials
ms.assetid: 43e97ce0-97bc-4a27-9485-5bbeb7190b85
caps.latest.revision: "24"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8d497ec1f8b0d7c557c6d802328ddbbb4360a988
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="lesson-1-2---setting-tool-options-and-layout"></a>Lezione 1-2-Layout e impostazione delle opzioni dello strumento
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]È possibile impostare opzioni che consentono di configurare gli oggetti visualizzati l'interfaccia utente grafica di ottimizzazione guidata motore di Database (GUI) all'avvio, il carattere utilizzato e altre funzionalità dello strumento migliore supporta la modalità di utilizzo. Le procedure contenute in questa pagina illustrano le opzioni che è possibile impostare e in che modo impostarle.  
  
### <a name="set-the-tool-options"></a>Impostazione delle opzioni dello strumento  
  
1.  Avviare lo strumento Ottimizzazione guidata motore di database. Scegliere **Programmi** dal menu **Start**di Windows, selezionare [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], poi **Strumenti per le prestazioni**e fare clic su **Ottimizzazione guidata motore di database**.  
  
2.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
3.  Nella finestra di dialogo **Opzioni** visualizzare le opzioni seguenti:  
  
    -   Espandere l'elenco **All'avvio** per mostrare le visualizzazioni possibili all'avvio di Ottimizzazione guidata motore di database. Per impostazione predefinita, è selezionata l'opzione **Mostra una nuova sessione** .  
  
    -   Fare clic su **Modifica carattere** per visualizzare i tipi di carattere disponibili per gli elenchi di database e le tabelle della scheda **Generale** . I caratteri selezionati per questa opzione vengono utilizzati anche nei report e nelle griglie delle indicazioni dello strumento Ottimizzazione guidata motore di database dopo l'esecuzione dell'ottimizzazione. Per impostazione predefinita, Ottimizzazione guidata motore di database utilizza i caratteri di sistema.  
  
    -   È possibile impostare **Numero di elementi negli elenchi degli ultimi elementi utilizzati** tra **1** e **10**. In tal modo viene impostato il numero massimo di elementi visualizzati quando si sceglie **Sessioni recenti** o **File recenti** dal menu **File** . Per impostazione predefinita, questa opzione è impostata su **4**.  
  
    -   Quando l'opzione **Memorizza le ultime opzioni di ottimizzazione specificate** è selezionata, per impostazione predefinita, per la sessione di ottimizzazione successiva, lo strumento Ottimizzazione guidata motore di database usa le opzioni specificate per l'ultima sessione. Deselezionare questa casella di controllo per utilizzare le opzioni di ottimizzazione predefinite di Ottimizzazione guidata motore di database. Per impostazione predefinita, questa opzione è selezionata.  
  
    -   Per impostazione predefinita, l'opzione **Chiedi conferma prima di eliminare definitivamente le sessioni** è selezionata per evitare l'eliminazione accidentale di sessioni di ottimizzazione.  
  
    -   Per impostazione predefinita, l'opzione **Chiedi conferma prima di arrestare l'analisi della sessione** è selezionata, per evitare l'arresto accidentale di una sessione di ottimizzazione prima che Ottimizzazione guidata motore di database abbia concluso l'analisi di un carico di lavoro.  
  
## <a name="next-lesson"></a>Lezione successiva  
[Lezione 2: Utilizzo dello strumento Ottimizzazione guidata motore di database](../../tools/dta/lesson-2-using-database-engine-tuning-advisor.md)  
  
  
  
