---
title: Il Driver ODBC per Oracle | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC driver for Oracle [ODBC]
- ODBC driver for Oracle [ODBC], about ODBC driver for Oracle
- Oracle data access [ODBC]
ms.assetid: 937e0662-8b1d-44f7-b077-4015c6605b2c
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 70ae9b447f0f3bcc6e70060b2f46f994ef3ea773
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-driver-for-oracle"></a>Driver ODBC per Oracle
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. In alternativa, utilizzare il driver ODBC fornito da Oracle.  
  
 Microsoft® ODBC Driver for Oracle consente di connettere l'applicazione ODBC conformi a un database Oracle. Il Driver ODBC per Oracle è conforme alla specifica Open Database Connectivity (ODBC) descritto nel *riferimento per programmatori ODBC*. Consente l'accesso ai pacchetti PL/SQL, l'integrazione XA/DTC e accesso a Oracle da all'interno di Internet Information Services (IIS).  
  
 Oracle RDBMS è un sistema di gestione di database relazionale multiutente che viene eseguito con diversi sistemi operativi workstation e minicomputer. I computer IBM compatibile in esecuzione Microsoft Windows possono comunicare con il server di database Oracle in rete. Reti supportate includono Microsoft LAN Manager, NetWare, VINES, DECnet e qualsiasi rete che supporta TCP/IP.  
  
 Il Driver ODBC per Oracle consente a un'applicazione di accedere ai dati in un database Oracle tramite l'interfaccia ODBC. Il driver può accedere a database Oracle locali o può comunicare con la rete tramite SQL * Net. Nel diagramma seguente illustra in dettaglio l'architettura di applicazioni e driver.  
  
 ![Il Driver ODBC per Oracle app &#47; architettura driver](../../odbc/microsoft/media/orcdrvsdkarch.gif "OrcDrvSDKArch")  
  
 Il Driver ODBC per Oracle è conforme a 1 livello di conformità di API e componenti di base del livello di conformità SQL. Supporta inoltre alcune funzioni in conformità di API di livello 2 e la maggior parte della grammatica nei livelli di conformità di base ed estesi di SQL. Il driver ODBC versione 2.5 conforme e supporta sistemi a 32 bit. Oracle 7.3 x è supportato completamente; Oracle8 offre supporto limitato. Il Driver ODBC per Oracle non supporta i nuovi tipi di dati Oracle8, tipi di dati Unicode, BLOB, CLOB, e così via, né il supporto per nuovo modello Oracle a oggetti relazionali. Per ulteriori informazioni sui tipi di dati supportati, vedere [Supported Data Types](../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md) in questa Guida.  
  
 Per accedere ai dati di Oracle, sono necessari i componenti seguenti:  
  
-   Il Driver ODBC per Oracle  
  
-   Un database Oracle RDBMS  
  
-   Software Client Oracle  
  
 Inoltre, per le connessioni remote:  
  
-   Una rete che connette i computer che eseguono il driver e il database. La rete deve supportare SQL * Net connessioni.  
  
## <a name="component-documentation"></a>Documentazione del componente  
 Questa guida contiene informazioni dettagliate sull'impostazione e configurazione del Driver ODBC Microsoft per Oracle e aggiunta di funzionalità a livello di codice. Contiene inoltre materiale di riferimento tecnico.  
  
 Per informazioni su un comportamento specifico prodotto Oracle, consultare la documentazione che accompagna il prodotto Oracle.  
  
 Per informazioni sull'impostazione o configurazione di Microsoft ODBC Driver for Oracle utilizzando Amministrazione origine dati ODBC, vedere il [Amministrazione origine dati ODBC](../../odbc/admin/odbc-data-source-administrator.md) documentazione.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Guida dell'utente del driver ODBC per Oracle](../../odbc/microsoft/odbc-driver-for-oracle-user-s-guide.md)  
  
-   [Guida di riferimento per i programmatori del driver ODBC per Oracle](../../odbc/microsoft/odbc-driver-for-oracle-programmer-s-reference.md)
