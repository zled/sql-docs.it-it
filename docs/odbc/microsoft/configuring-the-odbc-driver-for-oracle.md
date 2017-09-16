---
title: Configurazione del Driver ODBC per Oracle | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring ODBC driver for Oracle [ODBC]
- ODBC driver for Oracle [ODBC], configuring
ms.assetid: 0a5f827c-0b80-4627-85cb-f10292b9fb33
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 64e6dfe9f31eb983170f08e9fcd3e0705ba9ae62
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="configuring-the-odbc-driver-for-oracle"></a>Configurazione del Driver ODBC per Oracle
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. In alternativa, utilizzare il driver ODBC fornito da Oracle.  
  
 È possibile controllare le prestazioni del Driver ODBC per Oracle per conoscere l'ambiente di dati e impostare correttamente i parametri di connessione all'origine dati tramite il [Amministrazione origine dati ODBC](../../odbc/admin/odbc-data-source-administrator.md) finestra dialogo o la connessione parametri di stringa. Nella finestra di dialogo disponibili i seguenti controlli per la connessione a un'origine dati tramite la finestra di dialogo o utilizzo di stringhe di connessione:  
  
-   **Scheda DSN utente** Elenca i nomi di origine dati che sono locali nel computer.  
  
-   **Scheda DSN di sistema** consente di aggiungere o rimuovere un'origine dati di sistema. Origini dati di sistema sono accessibili da tutti gli utenti del computer locale.  
  
-   **Scheda DSN file** consente di aggiungere o rimuovere un'origine dati file dal computer locale. Origini dati dei file possono essere condiviso da tutti gli utenti che hanno installato il driver stesso.  
  
-   **Scheda driver** sono elencati i driver ODBC installati.  
  
-   **Scheda analisi** consente di specificare la modalità di gestione Driver ODBC tracce chiamate alle funzioni ODBC. È possibile configurare la traccia separatamente per ogni applicazione ODBC installato.  
  
-   **Scheda pool di connessioni** consente di selezionare le opzioni di connessione per ogni driver installato.  
  
-   **Sulla scheda** sono elencati i file di componente ODBC installati.  
  
 Dopo avere aggiunto un'origine dati, è possibile utilizzare il **Amministrazione origine dati ODBC** la finestra di dialogo per configurare l'accesso all'origine dati. Selezionare un'origine dati e quindi fare clic su una delle schede per modificare o esaminare le informazioni.
