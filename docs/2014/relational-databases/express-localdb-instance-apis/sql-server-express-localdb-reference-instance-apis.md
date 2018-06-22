---
title: Riferimento all'API dell'istanza di SQL Server Express LocalDB | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: faec46da-0536-4de3-96f3-83e607c8a8b6
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ebafb4bf20d84d2a570af7225e26c09e9089825e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063159"
---
# <a name="sql-server-express-localdb-instance-api-reference"></a>Riferimento all'API dell'istanza del database locale di SQL Server ExpressSQL Server
  In SQL Server basato su servizi, tradizionale, le singole istanze di SQL Server installate in un solo computer sono separate fisicamente; ovvero, ogni istanza deve essere installata e rimossa separatamente. Inoltre, ciascuna istanza dispone di un set separato di file binari e si esegue in un processo del servizio separato. Il nome dell'istanza di SQL Server viene utilizzato per specificare l'istanza di SQL Server a cui l'utente desidera effettuare la connessione.  
  
 Nell'API dell'istanza del database locale di SQL Server Express viene utilizzato un modello di istanza semplificato e leggero. Anche se le istanze del database locale singole sono separate sul disco e nel Registro di sistema, in esse viene utilizzato lo stesso set di file binari condivisi del database locale. Inoltre, nel database locale non vengono utilizzati servizi. Le istanze del database locale vengono avviate su richiesta tramite le chiamate API dell'istanza del database locale. Nel database locale il nome dell'istanza viene utilizzato per specificare quali delle istanze del database locale l'utente desideri utilizzare.  
  
 Un'istanza del database locale è sempre di proprietà di un solo utente ed è visibile e accessibile solo dal contesto di questo utente, a meno che non sia abilitata la condivisione dell'istanza.  
  
 Anche se tecnicamente le istanze del database locale non corrispondono a istanze di SQL Server tradizionali, l'utilizzo previsto è simile. Vengono chiamati *istanze* per enfatizzare questa somiglianza e per renderle più intuitive agli utenti di SQL Server.  
  
 Il database locale supporta due tipi di istanze, ovvero automatiche e denominate. L'identificatore per un'istanza del database locale è il nome dell'istanza.  
  
## <a name="automatic-localdb-instances"></a>Istanze automatiche del database locale  
 Le istanze automatiche del database locale sono "pubbliche". Vengono create e gestite automaticamente per l'utente e possono essere utilizzate da qualsiasi applicazione. Un'istanza automatica del database locale esiste per ogni versione del database locale installato nel computer dell'utente.  
  
 Le istanze automatiche del database locale forniscono una gestione continua dell'istanza. L'utente non deve creare l'istanza; in questo modo egli può facilmente installare applicazioni ed eseguire la migrazione a computer diversi. Se nel computer di destinazione è installata la versione specificata del database locale, l'istanza automatica di tale database per quella versione è disponibile anche su quel computer.  
  
### <a name="automatic-instance-management"></a>Gestione dell'istanza automatica  
 Un utente non deve creare un'istanza automatica del database locale. L'istanza viene creata al momento dell'utilizzo, purché la versione specificata del database locale sia disponibile nel computer dell'utente. Dal punto di vista dell'utente, l'istanza automatica è sempre presente se sono disponibili file binari del database locale.  
  
 Per le istanze automatiche sono valide anche altre operazioni di gestione dell'istanza, quali eliminazione, condivisione e non condivisione. In particolare, l'eliminazione di un'istanza automatica consente di reimpostare in modo efficiente l'istanza, che verrà ricreata alla successiva operazione di avvio. L'eliminazione di un'istanza automatica può essere necessaria nel caso in cui i database di sistema siano danneggiati.  
  
### <a name="automatic-instance-naming-rules"></a>Regole di denominazione dell'istanza automatica  
 Le istanze automatiche del database locale dispongono di un modello speciale per il nome dell'istanza che appartiene a uno spazio dei nomi riservato. È necessario evitare conflitti di nomi con le istanze denominate del database locale.  
  
 Il nome dell'istanza automatica è il numero di versione di rilascio di base del database locale preceduto da un solo carattere "v", simile a "v" più due numeri con un punto tra loro; ad esempio, v11.0 o V12.00.  
  
 Esempi di nomi di istanze automatiche non consentiti sono:  
  
-   11.0 (carattere "v" mancante all'inizio)  
  
-   v11 (punto e secondo numero della versione mancanti)  
  
-   v11. (secondo numero di versione mancante)  
  
-   v11.0.1.2 (numero di versione con più di due parti)  
  
## <a name="named-localdb-instances"></a>Istanze denominate del database locale  
 Le istanze denominate del database locale sono "private", ovvero un'istanza è di proprietà di una sola applicazione, responsabile della creazione e della gestione dell'istanza. Le istanze denominate del database locale forniscono isolamento e migliorano le prestazioni.  
  
### <a name="named-instance-creation"></a>Creazione di istanze denominate  
 L'utente deve creare istanze denominate in modo esplicito tramite l'API di gestione del database locale o in modo implicito tramite il file app.config per un'applicazione gestita. È possibile che in un'applicazione gestita venga utilizzata anche l'API.  
  
 Ogni istanza denominata dispone di una versione associata del database locale, ovvero che punta a un set specificato di file binari del database locale. La versione per l'istanza denominata viene impostata durante il processo di creazione dell'istanza.  
  
### <a name="named-instance-naming-rules"></a>Regole di denominazione dell'istanza denominata  
 Il nome di un'istanza del database locale può essere composto da un massimo di 128 caratteri (il limite viene imposto dal tipo di dati `sysname`). Si tratta di una differenza significativa rispetto ai nomi di istanze di SQL Server tradizionali, che sono limitati a nomi NetBIOS di 16 caratteri ASCII. Il motivo di questa differenza è che i database vengono trattati dal database locale come file, pertanto viene applicata una semantica basata su file, in modo che sia intuitiva per gli utenti affinché abbiano più libertà nella scelta di nomi dell'istanza.  
  
 Nel nome di un'istanza del database locale può essere incluso qualsiasi carattere Unicode che sia valido all'interno del componente del nome del file. Caratteri non validi in un componente del nome del file in genere includono i seguenti caratteri: caratteri ASCII/Unicode 1 a 31, nonché virgolette ("), minore di (\<), maggiore di (>), barra verticale (|), backspace (\b), tabulazione (\t), due punti (:), asterisco (*) punto interrogativo (?), barra rovesciata (\\) e barra (/). Si noti che il carattere Null (\0) è consentito perché utilizzato per la chiusura della stringa. Tutti i caratteri successivi al primo carattere Null verranno ignorati.  
  
> [!NOTE]  
>  L'elenco di caratteri non consentiti può dipendere dal sistema operativo e può essere modificato nelle versioni successive.  
  
 Gli spazi vuoti iniziali e finali nei nomi dell'istanza vengono ignorati e saranno tagliati.  
  
 Per evitare conflitti di denominazione, denominati LocalDB istanze non possono avere un nome che segue il modello di denominazione per le istanze automatiche, come descritto in precedenza in "Regole di automatica dei nomi di istanza". Un tentativo di creare un'istanza denominata con un nome che segue il modello di denominazione istanza automatica in modo efficace crea un'istanza predefinita.  
  
## <a name="sql-server-express-localdb-reference-topics"></a>Argomenti di riferimento al database locale di SQL Server Express  
 [Informazioni sulla versione e intestazione di SQL Server Express LocalDB](sql-server-express-localdb-header-and-version-information.md)  
 Vengono fornite informazioni sul file di intestazione e le chiavi del Registro di sistema per l'individuazione dell'API dell'istanza del database locale.  
  
 [Strumento di gestione della riga di comando: SqlLocalDB.exe](command-line-management-tool-sqllocaldb-exe.md)  
 Viene descritto SqlLocalDB.exe, uno strumento per la gestione delle istanze del database locale dalla riga di comando.  
  
 [Funzione LocalDBCreateInstance](localdbcreateinstance-function.md)  
 Viene descritta la funzione per creare una nuova istanza del database locale.  
  
 [Funzione LocalDBDeleteInstance](localdbdeleteinstance-function.md)  
 Viene descritta la funzione per rimuovere un'istanza del database locale.  
  
 [Funzione LocalDBFormatMessage](localdbformatmessage-function.md)  
 Viene descritta la funzione per restituire la descrizione localizzata di un errore del database locale.  
  
 [Funzione LocalDBGetInstanceInfo](localdbgetinstanceinfo-function.md)  
 Viene descritta la funzione per ottenere informazioni per un'istanza del database locale, ad esempio se è disponibile, le informazioni sulla versione, se l'istanza è in esecuzione e così via.  
  
 [Funzione LocalDBGetInstances](localdbgetinstances-function.md)  
 Viene descritta la funzione per restituire tutte le istanze del database locale con una versione specificata.  
  
 [Funzione LocalDBGetVersionInfo](localdbgetversioninfo-function.md)  
 Viene descritta la funzione per restituire le informazioni per una versione specificata del database locale.  
  
 [Funzione LocalDBGetVersions](localdbgetversions-function.md)  
 Viene descritta la funzione per restituire tutte le versioni del database locale disponibili in un computer.  
  
 [Funzione LocalDBShareInstance](localdbshareinstance-function.md)  
 Viene descritta la funzione per condividere un'istanza specificata del database locale.  
  
 [Funzione LocalDBStartInstance](localdbstartinstance-function.md)  
 Viene descritta la funzione per avviare un'istanza specificata del database locale.  
  
 [Funzione LocalDBStartTracing](localdbstarttracing-function.md)  
 Viene descritta la funzione per abilitare la traccia API per un utente.  
  
 [Funzione LocalDBStopInstance](localdbstopinstance-function.md)  
 Viene descritta la funzione per arrestare l'esecuzione di un'istanza specificata del database locale.  
  
 [Funzione LocalDBStopTracing](localdbstoptracing-function.md)  
 Viene descritta la funzione per disabilitare la traccia API per un utente.  
  
 [Funzione LocalDBUnshareInstance](localdbunshareinstance-function.md)  
 Viene descritta la funzione per arrestare la condivisione di un'istanza specificata del database locale.  
  
  