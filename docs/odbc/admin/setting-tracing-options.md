---
title: Impostazione opzioni di traccia | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: admin
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio Analyzer tracing [ODBC]
- ODBC data source administrator [ODBC], tracing options
- tracing options [ODBC], ODBC data source administrator
ms.assetid: 44404a79-b716-4bc1-9ffb-70cd8239d237
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b1a62a03d3bb9e9876ed152bb4ac2cb8fb56ce66
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="setting-tracing-options"></a>Impostazione opzioni di traccia
Il **traccia** scheda della finestra di **Amministrazione origine dati ODBC** la finestra di dialogo consente di configurare la modalità di chiamate di funzioni ODBC vengono tracciate.  
  
## <a name="how-tracing-works"></a>Funzionamento di traccia  
 Quando si avvia la traccia di **traccia** scheda, gestione Driver registreranno tutte le chiamate di funzione ODBC per tutti successivamente eseguire le applicazioni. Chiamate di funzione ODBC dalle applicazioni in esecuzione prima dell'avvio della traccia non vengono registrate. Chiamate di funzioni ODBC vengono registrate in un file di log specificato.  
  
 La traccia viene arrestata solo dopo aver fatto clic **Interrompi analisi**. Tenere presente che, durante la traccia è attiva, il file di log continua ad aumentare e che questo influisce sulle prestazioni di tutte le applicazioni ODBC.  
  
 Per ulteriori informazioni sulla traccia, vedere [traccia](../../odbc/reference/develop-app/tracing.md).  
  
### <a name="changes-in-odbc-tracing"></a>Modifiche in una traccia ODBC  
 Prima di MDAC 2.7 SP2, la traccia ODBC è stato possono solo su base, a livello di computer in cui vengono acquisiti i dettagli esposti su tutte le applicazioni ODBC in esecuzione con identità di traccia. Comprende funzionalità di traccia per le attività correlate a ODBC che potrebbero verificarsi per i processi creati o eseguito per conto di altri account utente locale e l'entità di sicurezza predefinite, ad esempio il servizio locale e il servizio di rete.  
  
 Per impostazione predefinita, ODBC traccia ora utilizza la modalità per utente. Se sei un amministratore locale, tuttavia, è ancora possibile abilitare la traccia a livello di computer con l'amministratore dell'origine dati ODBC.  
  
 Per configurare la modalità di analisi ODBC:  
  
1.  Se necessario, accedere utilizzando un account che appartiene al gruppo Administrators locale.  
  
2.  Strumenti di amministrazione aprire Amministrazione origine dati ODBC.  
  
3.  Fare clic su di **traccia** scheda.  
  
4.  Configurare la modalità di analisi tramite il **traccia a livello di computer per tutte le identità utente** casella di controllo:  
  
5.  Per abilitare la traccia a livello di computer, selezionare la casella di controllo.  
  
6.  Per tornare alla finestra di traccia per ogni utente, deselezionare la casella di controllo.  
  
7.  Fare clic su **Applica**.  
  
> [!NOTE]  
>  Se la traccia è già stato avviato in modalità, è necessario arrestare la traccia e passare alla modalità per la modalità di modifica completata.  
  
> [!IMPORTANT]  
>  La traccia a livello di computer deve essere abilitata solo quando necessario; in caso contrario, deve essere lasciato disattivato.  
  
## <a name="visual-studio-analyzer-tracing"></a>Analisi di Visual Studio Analyzer  
  
> [!IMPORTANT]  
>  Supporto per Visual Studio Analyzer è stata rimossa a partire da Windows 8 (solo incluso Visual Studio Analyzer in versioni precedenti di Visual Studio).. Per un'alternativa meccanismo di risoluzione dei problemi, utilizzare la traccia dell'offerta.  
  
 Analisi di Visual Studio® Analyzer fornisce prestazioni e le informazioni di debug sul livello di ODBC. Tutti gli eventi in uscita verranno generati l'interfaccia principale per presentare accurata un'immagine come possibili relative alla durata in componenti ODBC. Visual Studio Analyzer traccia richiede qualsiasi origine evento per registrare quando l'origine è configurato. Per ulteriori informazioni su questo tipo di traccia, vedere la documentazione di Visual Studio.
