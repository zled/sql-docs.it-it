---
title: Configurare le proprietà di un agente di raccolta dati | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.dc.datacollectionprop.advanced.f1
- sql12.swb.dc.datacollectionprop.general.f1
ms.assetid: cf98f57d-5a6d-4bc3-bf10-783e460fc63d
caps.latest.revision: 5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3f79a7826c593410f8dc6879f2b245f5a577e45b
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "43816057"
---
# <a name="configure-properties-of-a-data-collector"></a>Configurare le proprietà di un agente di raccolta dati
  In questo argomento viene descritto come configurare le proprietà di un agente di raccolta dati.  
  
## <a name="data-collection-properties-general-tab"></a>Proprietà raccolta dati (scheda Generale)  
 Utilizzare questa pagina per configurare le impostazioni per il data warehouse di gestione e specificare la posizione di archiviazione dei dati raccolti prima del caricamento nel data warehouse.  
  
 **Abilita raccolta dati**  
 Selezionare questa opzione per abilitare la raccolta dei dati. Questa impostazione equivale all'esecuzione della stored procedure sp_syscollector_enable_collector. La deselezione di questa casella di controllo disabilita la raccolta dei dati ed equivale all'esecuzione della stored procedure sp_syscollector_disable_collector.  
  
 **Server**  
 Visualizza il nome del server che ospiterà il data warehouse di gestione.  
  
 **Nome database**  
 Visualizza il nome del database relazionale utilizzato per il data warehouse di gestione.  
  
 **Test connessione**  
 Consente di testare la connessione al **Server** specificato utilizzando le informazioni fornite durante la configurazione della raccolta dati.  
  
 **Directory cache**  
 Specifica la directory in cui vengono archiviati i dati raccolti nel sistema prima di essere caricati nel data warehouse di gestione. Se la **Directory cache** non è specificata, l'agente di raccolta dati tenta di individuare le variabili di ambiente % TEMP% e % TMP% e utilizza una di queste posizioni come percorso predefinito per l'archiviazione temporanea. Se queste variabili di ambiente non sono configurate, si verifica un errore e viene chiesto di creare una directory della cache.  
  
## <a name="data-collection-properties-advanced-tab"></a>Proprietà raccolta dati (scheda Avanzate)  
 Utilizzare questa pagina per configurare le impostazioni relative ai tentativi per la connessione al data warehouse di gestione.  
  
 **Numero di tentativi se il caricamento ha esito negativo**  
 Consente di specificare il numero di volte in cui è possibile ritentare l'esecuzione di un caricamento non riuscito nel data warehouse di gestione. Il valore predefinito è 1.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestire raccolta dati](data-collection.md)   
 [Configurazione del data warehouse di gestione &#40;SQL Server Management Studio&#41;](configure-the-management-data-warehouse-sql-server-management-studio.md)  
  
  
