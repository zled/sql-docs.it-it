---
title: MSSQLSERVER_30053 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
ms.assetid: 8ad23889-e243-4bd7-bc3e-150403399d89
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5a54ed2eb35a6a7f0b5d1255e5f2841b7ace6f3a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47614789"
---
# <a name="mssqlserver30053"></a>MSSQLSERVER_30053
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|30053|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|FTXT_QUERY_E_WORDBREAKINGTIMEOUT|  
|Testo del messaggio|Timeout del word breaking per la stringa di query full-text. Questo problema può verificarsi se il word breaker impiega molto tempo per elaborare la stringa di query full-text o se è in esecuzione un numero elevato di query nel server. Provare a eseguire nuovamente la query in un carico ridotto.|  
  
## <a name="explanation"></a>Spiegazione  
Un errore di timeout del word breaking può verificarsi nelle situazioni seguenti:  
  
-   Il word breaker per il linguaggio di query non è configurato correttamente. Le impostazioni del Registro di sistema, ad esempio, non sono corrette.  
  
-   Il malfunzionamento del word breaker è dovuto a una stringa di query specifica.  
  
-   Il word breaker restituisce troppi dati per una stringa di query specifica. I dati in eccesso sono considerati un potenziale attacco con sovraccarico del buffer e di conseguenza viene arrestato il processo del daemon di filtri (fdhost.exe) che ospita i servizi di word breaking.  
  
-   La configurazione del processo del daemon di filtri non è corretta.  
  
    I problemi di configurazione più comuni sono rappresentati dalla scadenza della password o da criteri del dominio che impediscono l'accesso dell'account del daemon di filtri.  
  
-   Un carico di lavoro di query molto elevato è in esecuzione nell'istanza server. Ad esempio, il word breaker impiega molto tempo per elaborare la stringa della query full-text o un numero elevato di query sono in esecuzione nel server. Si tratta tuttavia della causa meno probabile.  
  
## <a name="user-action"></a>Azione dell'utente  
Selezionare l'azione dell'utente adatta alla probabile causa del timeout, come segue:  
  
|Causa probabile|Azione utente|  
|------------------|---------------|  
|Il word breaker per il linguaggio di query non è configurato correttamente.|Se si utilizza un word breaker di terze parti, è possibile che non sia stato registrato correttamente nel sistema operativo. In questo caso, registrare nuovamente il word breaker. Per altre informazioni, vedere [Ripristinare i word breaker usati dalla ricerca alla versione precedente](~/relational-databases/search/revert-the-word-breakers-used-by-search-to-the-previous-version.md).|  
|Il malfunzionamento del word breaker è dovuto a una stringa di query specifica.|Se il word breaker è supportato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], contattare il Servizio Supporto Tecnico Clienti Microsoft.|  
|Il word breaker restituisce troppi dati per una stringa di query specifica.|Se il word breaker è supportato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], contattare il Servizio Supporto Tecnico Clienti Microsoft.|  
|La configurazione del processo del daemon di filtri non è corretta.|Assicurarsi che venga utilizzata la password corrente e che i criteri di dominio non stiano impedendo l'accesso dell'account del daemon di filtri.|  
|Nell'istanza del server è in esecuzione un carico di lavoro molto elevato di query.|Provare a eseguire nuovamente la query in un carico ridotto.|  
  
## <a name="see-also"></a>Vedere anche  
[Impostare l'account del servizio dell'Utilità di avvio del daemon di filtri full-text](~/relational-databases/search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md)  
[Ricerca full-text](~/relational-databases/search/full-text-search.md)  
[sp_help_fulltext_system_components &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql.md)  
[Configurare e gestire word breaker e stemmer per la ricerca](~/relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)  
[Configurare e gestire filtri per la ricerca](~/relational-databases/search/configure-and-manage-filters-for-search.md)  
  
