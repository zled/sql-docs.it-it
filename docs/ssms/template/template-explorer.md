---
title: Esplora modelli | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-templates
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.templates.explorer.f1
- sql13.wb.templates.f1
helpviewer_keywords:
- templates [SQL Server]
- SQL Server Management Studio [SQL Server], Template Explorer
- Template Explorer
- templates [Transact-SQL]
- templates [SQL Server], Template Explorer
ms.assetid: b9ee55c5-bb44-4f76-90ac-792d8d83b4c8
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: cd3d984df93312d1eb58bbef7e4eea92dc758a1e
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="template-explorer"></a>Esplora modelli
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] offre un'ampia gamma di modelli. I modelli sono file preimpostati contenenti script SQL che agevolano la creazione degli oggetti di database. Alla prima apertura di Esplora modelli, una copia dei modelli viene inserita nella cartella dell'utente in C:\Users in AppData\Roaming\Microsoft\SQL Server Management Studio\130\Templates.  
  
È possibile esplorare i modelli disponibili in Esplora modelli, quindi aprire un modello per incorporare il codice in una finestra dell'editor di codice. È inoltre possibile creare modelli personalizzati.  
  
## <a name="benefits-of-templates"></a>Vantaggi dei modelli  
Sono disponibili modelli per soluzioni, progetti e diversi tipi di editor del codice. I modelli inclusi nell'applicazione consentono di creare oggetti, ad esempio database, tabelle, viste, indici, stored procedure, trigger, statistiche e funzioni. Sono inoltre disponibili modelli che facilitano la gestione del server mediante la creazione di proprietà estese, server collegati, account di accesso, ruoli, utenti e modelli per [!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)].  
  
Gli script modello disponibili in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] includono parametri che consentono di personalizzare il codice. Dopo avere aperto il modello, usare la finestra di dialogo **Sostituisci parametri modello** per sostituire i parametri del modello con i valori desiderati.  
  
Creare modelli personalizzati per le attività eseguite di frequente. Organizzare gli script personalizzati in cartelle esistenti oppure creare una nuova struttura di cartelle.  
  
L'editor di query del [!INCLUDE[ssDE](../../includes/ssde_md.md)] supporta anche frammenti di codice che possono essere inseriti in percorsi specifici in uno script facendo clic con il pulsante destro del mouse sul percorso.  
  
## <a name="related-tasks"></a>Related Tasks  
Utilizzare i seguenti argomenti per ottenere un'introduzione ai modelli.  
  
|**Description**|**Argomento**|  
|-------------------|-------------|  
|Viene descritto come incorporare il codice da un modello in una finestra dell'editor di codice.|[Aprire un modello](../../ssms/template/open-a-template.md)|  
|Si descrive come sostituire valori del parametro di modello dopo aver aperto un modello in un editor di codice.|[Sostituisci parametri modello](../../ssms/template/replace-template-parameters.md)|  
  
