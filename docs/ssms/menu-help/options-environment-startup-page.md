---
title: " Pagina Opzioni di SQL Server - Ambiente - Avvio | Microsoft Docs"
ms.date: 11/05/2018
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 87de35c23a89e49f376b41676462dd275f676871
ms.sourcegitcommit: a2be75158491535c9a59583c51890e3457dc75d6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2018
ms.locfileid: "51269465"
---
# <a name="options-environment---startup-page"></a>Opzioni (Ambiente - Pagina Avvio)

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Usare la finestra di dialogo **Opzioni** per configurare le azioni di avvio di [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], le opzioni generali di gestione della finestra e altre impostazioni generali. Scegliere **Opzioni** dal menu **Strumenti**, espandere la cartella **Ambiente** e quindi fare clic su **Avvio**.

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia

**All'avvio**

Consente di selezionare l'azione che deve essere eseguita da [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] all'avvio. Le opzioni disponibili sono le seguenti:

- **Apri Esplora oggetti** richiede di stabilire una connessione e quindi apre Esplora oggetti.

- **Apri nuova finestra Query** richiede di stabilire una connessione e quindi apre Editor di query SQL.

- **Apri finestra Query e Esplora oggetti** richiede di stabilire una connessione e quindi la usa per aprire sia Esplora oggetti sia Editor di query SQL.

- **Apri Esplora oggetti e Monitoraggio attività**

- **Apri ambiente vuoto** apre [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] senza visualizzare una finestra dell'editor di query SQL né connettere Esplora oggetti a un server.

**Nascondi oggetti di sistema in Esplora oggetti**

Selezionare questa casella di controllo per rimuovere database, tabelle, viste e stored procedure di sistema dalla visualizzazione dell'albero in Esplora oggetti. Le funzioni e i tipi di dati di sistema non vengono nascosti. Questa opzione si applica solo alle istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e non ha alcun effetto sui server già connessi in Esplora oggetti.

## <a name="see-also"></a>Vedere anche

- [Guida sensibile al contesto delle finestre di dialogo Opzioni](options-dialog-boxes-f1-help.md)
- [Opzioni (Ambiente - pagina Generale)](options-environment-general-page.md)
