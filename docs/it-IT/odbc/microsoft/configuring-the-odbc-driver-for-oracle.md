---
title: Configurazione del Driver ODBC per Oracle | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- configuring ODBC driver for Oracle [ODBC]
- ODBC driver for Oracle [ODBC], configuring
ms.assetid: 0a5f827c-0b80-4627-85cb-f10292b9fb33
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 64c90e68e98e5f2c3a242d9a14bc51e2445a12ef
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="configuring-the-odbc-driver-for-oracle"></a>Configurazione del Driver ODBC per Oracle
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. In alternativa, utilizzare il driver ODBC fornito da Oracle.  
  
 È possibile controllare le prestazioni del Driver ODBC per Oracle per conoscere l'ambiente di dati e impostare correttamente i parametri di connessione all'origine dati tramite il [Amministrazione origine dati ODBC](../../odbc/admin/odbc-data-source-administrator.md) finestra dialogo o la connessione parametri di stringa. Nella finestra di dialogo disponibili i seguenti controlli per la connessione a un'origine dati tramite la finestra di dialogo o utilizzo di stringhe di connessione:  
  
-   **Scheda DSN utente** Elenca i nomi delle origini dati locali nel computer.  
  
-   **Scheda DSN di sistema** consente di aggiungere o rimuovere un'origine dati di sistema. Origini dati di sistema sono accessibili da tutti gli utenti del computer locale.  
  
-   **Scheda DSN file** consente di aggiungere o rimuovere un'origine dati file dal computer locale. Origini dati dei file possono essere condiviso da tutti gli utenti che hanno installato il driver stesso.  
  
-   **Scheda driver** sono elencati i driver ODBC installati.  
  
-   **Scheda Tracing** consente di specificare la modalità gestione Driver ODBC tiene traccia di chiamate alle funzioni ODBC. È possibile configurare la traccia separatamente per ogni applicazione ODBC installato.  
  
-   **Scheda connessione Pooling** consente di selezionare le opzioni di connessione per ogni driver installato.  
  
-   **Sulla scheda** sono elencati i file componente ODBC installati.  
  
 Dopo avere aggiunto un'origine dati, è possibile utilizzare il **Amministrazione origine dati ODBC** la finestra di dialogo per configurare l'accesso all'origine dati. Selezionare un'origine dati e quindi fare clic su una delle schede per modificare o esaminare le informazioni.
