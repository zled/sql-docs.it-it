---
title: Novità di SSMA per Access(AccessToSQL) | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-access
ms.custom: ''
ms.date: 03/01/2018
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: a24d3fc0-6911-4bfa-828a-197abf222e02
caps.latest.revision: 37
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d2e054168ef28b6f6f323fa67f6a5c189d7febc9
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="whats-new-in-ssma-for-access-accesstosql"></a>Novità di SSMA per Access (AccessToSQL)
Questo argomento elenca SSMA per le modifiche di accesso in ogni versione.  

## <a name="ssma-v77"></a>SSMA v7.7
La versione v7.7 di SSMA per l'accesso contiene le seguenti modifiche:
- SSMA per l'accesso è stata migliorata con le correzioni di destinazione che consentono di migliorare le metriche di qualità e la conversione.
- La versione a 32 bit di SSMA per l'accesso in base a grande richiesta, viene nuovamente. Se confrontato con l'implementazione precedente (prima v7.4), sono disponibili due pacchetti di installazione, ma non possono essere installati side-by-side. Di conseguenza, è necessario scegliere la versione più appropriata in base ai componenti di connettività che è. È sempre preferibile usare la versione a 64 bit, se possibile.

> [!IMPORTANT]
> Con SSMA v7.4 e versioni successive, .net 4.5.2 è un prerequisito di installazione.

## <a name="ssma-v76"></a>SSMA v7.6
La versione v7.6 di SSMA per l'accesso è stata migliorata con le correzioni di destinazione che consentono di migliorare le metriche di qualità e la conversione e con il supporto per SQL Server 2017 (anteprima pubblica). Supporto per SQL Server 2017 in Windows e Linux è disponibile in anteprima pubblica e non deve essere utilizzato per le migrazioni di produzione.

> [!IMPORTANT]
> Con SSMA v7.4 e versioni successive, .net 4.5.2 è un prerequisito di installazione e la versione a 32 bit dello strumento è stata interrotta.

## <a name="ssma-v75"></a>SSMA v7.5
La versione v7.5 di SSMA per l'accesso è stata migliorata con numerosi miglioramenti per garantire maggiore accessibilità per persone affette da disabilità.

> [!IMPORTANT]
> .NET 4.5.2 è un prerequisito per l'installazione di SSMA v7.5. Inoltre, a partire da v7.4, la versione a 32 bit di SSMA è stata sospesa.

## <a name="ssma-v74"></a>SSMA v7.4
La versione v7.4 di SSMA per l'accesso contiene le seguenti modifiche:
- Il **timeout Query** l'opzione è disponibile durante l'individuazione di oggetti dello schema all'origine e di destinazione.
![valore di timeout query](../media/query-timeout_red.png)

- La metrica della qualità e la conversione è stata migliorata con le correzioni di destinazione, in base ai suggerimenti dei clienti.

> [!IMPORTANT]
> .NET 4.5.2 è un prerequisito per l'installazione di SSMA v7.4. Inoltre, a partire da v7.4, la versione a 32 bit di SSMA è stata sospesa.

## <a name="ssma-v73"></a>SSMA v7.3
La versione v7.3 di SSMA per l'accesso contiene le seguenti modifiche:
- Metrica qualità e la conversione migliorata con le correzioni di destinazione in base ai suggerimenti dei clienti.
- Framework di estendibilità SSMA esposta tramite gli elementi seguenti:
  - La funzionalità di esportazione per un progetto di SQL Server Data Tools (SSDT).
    -   È ora possibile esportare script dello schema da SSMA a un progetto SSDT. È possibile utilizzare gli script di schema per apportare ulteriori modifiche dello schema e distribuire il database.
![Comando progetto SSDT Salva con nome](../media/export-schema-scripts_red.png)

  - Librerie che possono essere utilizzate da SSMA per l'esecuzione di conversioni personalizzate.
    - È ora possibile creare codice in grado di gestire le conversioni di sintassi personalizzata e che non sono stati precedentemente gestite dal SSMA.
      - Le istruzioni su come costruire un convertitore personalizzato sono disponibili in questo post di blog [funzionalità di conversione della estensione SQL Server Migration Assistant](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/).
      - Progetto di esempio per la conversione possibile scaricare questo [post di blog](https://blogs.msdn.microsoft.com/datamigration/ssmafororacleconversionsample/).

## <a name="ssma-v72"></a>Versione 7.2 SSMA
La versione a versione 7.2 di SSMA per l'accesso contiene le seguenti modifiche:
- Metrica qualità e la conversione migliorata con le correzioni di destinazione in base ai suggerimenti dei clienti.
- Miglioramenti di telemetria per fornire una migliore punti dati per risolvere i problemi dei clienti e migliorare il tasso di conversione di SSMA.

## <a name="ssma-v71"></a>V 7.1 SSMA
La versione v 7.1 di SSMA per l'accesso contiene le seguenti modifiche:
- 2017 di SQL Server in Windows e Linux CTP1 è una piattaforma di destinazione supportate per la migrazione. Questa funzionalità è disponibile in anteprima tecnica e supporta lo spostamento di dati e lo schema a server SQL di destinazione.
- SSMA supporta ora gli aggiornamenti automatici per scaricare la versione più recente di SSMA è disponibile.
- I file binari installabili SSMA ora vengono recapitati tramite file di pacchetto di Windows installer (MSI).

**Risorse**

[Estensione delle funzionalità di SQL Server Migration Assistant conversione](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/)
  
## <a name="may-2016"></a>Maggio 2016  
La versione di maggio 2016 di SSMA per l'accesso contiene le seguenti modifiche:  
  
-  Aggiunta del supporto ufficiale per SQL Server 2016
-  Rimuovere il controllo di programma di installazione per .net 2.0.
-  Fisso "Salva"progetto "progetto aperto" comandi e per la Console di SSMA.
-  Comando predefinito "securepassword" per la Console di SSMA.
-  Fissa il conteggio di oggetti per il caricamento iniziale.
-  Caricamento dati tabelle predefinito per le schede di interfaccia utente per l'accesso.
-  Correzione del bug nelle impostazioni globali. 
   
## <a name="march-2016"></a>Marzo 2016  
La versione di anteprima di marzo 2016 di SSMA per Access è le seguenti modifiche:  
  
-  Aggiunta del supporto per la migrazione a SQL Server 2016.  
   
## <a name="january-2016"></a>Gennaio 2016  
La versione di manutenzione di gennaio 2016 di SSMA per l'accesso contiene le seguenti modifiche:  
  
-  Funzione fixed non valido per impostazione predefinita di un campo GUID (RFC 3894811).  
-  Blocco predefinito sull'importazione di record per Database SQL (Azure) (RFC 4919573).  
-  Aggiunta Log menu Visualizza per SSMA (RFC 5706203).  
-  Aggiunta di telemetria.  
  
## <a name="july-2014"></a>Luglio 2014  
La versione di luglio 2014 di SSMA per l'accesso contiene le seguenti modifiche:  
  
-   Conversione del codice di database SQL di Azure migliorata.  
-   Spostare la funzionalità di estensione pack allo schema per supportare i database SQL di Azure.  
-   Miglioramenti delle prestazioni testata per i database con oggetti di 10 k.  
-   Aggiunti miglioramenti dell'interfaccia utente per la gestione con un numero elevato di oggetti.  
-   Aggiunta del supporto per l'evidenziazione degli schemi LOB "noti" (in modo che può essere ignorati nella conversione).  
-   Aggiunti miglioramenti di velocità di conversione.
-   Aggiunta del supporto per la visualizzazione oggetto conta nell'interfaccia utente.
-   Dimensioni del report ridotta da più di 25%.
-   Messaggi di errore migliorati per i costrutti non analizzati.  
  
## <a name="april-2014"></a>Aprile 2014  
La versione di aprile 2014 di SSMA per l'accesso contiene le seguenti modifiche:  
  
-   Aggiunta del supporto per Microsoft SQL Server 2014.  
-   Bug risolti sulla conversione in Azure.  
-   Bug risolti per le pagine del report invisibile in Internet Explorer 10.  
  
## <a name="january-2012"></a>Gennaio 2012  
La versione di gennaio 2012 di SSMA per l'accesso contiene le seguenti modifiche:  
  
-   È disponibile l'opzione per non mantenere nome utente e password per l'accesso MS tabelle collegate dopo la migrazione.  
-   Impostare le azioni cascade per riferimenti circolari No Action.  
-   Condizione messaggi corretti, che indica le azioni cascade per i riferimenti circolari sono stati impostati su No Action.  
  
## <a name="july-2011"></a>Luglio 2011  
La versione di luglio 2011 di SSMA per l'accesso contiene le seguenti modifiche:  
  
-   Una migliore segnalazione errori durante la migrazione dei dati.  
  
## <a name="april-2011"></a>Aprile 2011  
La versione di aprile 2011 di SSMA per l'accesso contiene le seguenti modifiche:  
  
-   Aggiunta di un singolo installabile di "SSMA per l'accesso", che supporta [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] "Denali" e SQL Azure.  
-   Aggiunta la possibilità di connettersi [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] "Denali".  
-   SSMA aggiunto per la versione della Console di accesso il supporto per la compatibilità con le versioni precedenti. È possibile aprire i progetti creati con versioni precedenti a v 5.0 SSMA.
-   Aggiunta la possibilità di installare il prodotto v 5.0 SSMA affiancata (SxS) con le versioni precedenti del prodotto SSMA.  
  
## <a name="july-2010"></a>Luglio 2010  
La versione di luglio 2010 di SSMA per l'accesso contiene le seguenti modifiche:  
  
-   Aggiunta del supporto per la migrazione a SQL Server 2008 R2 e SQL Azure.
-   Aggiunta di una connessione protetta a SQL Server e SQL Azure.  
-   Aggiunta del supporto per i database di Access 2010.
-   Aggiungere una nuova applicazione Console di SSMA per l'esecuzione della riga di comando.
-   Aggiunta del supporto per il tipo di dati DateTime2 di SQL Server.
  
## <a name="june-2008"></a>Giugno 2008  
La versione di giugno 2008 di SSMA per l'accesso contiene le seguenti modifiche:  
  
-   Aggiunta del supporto per i database di Access 2007.  
  
## <a name="may-2007"></a>Maggio 2007  
La versione di maggio 2007 di SSMA per l'accesso contiene le seguenti modifiche:  
  
-   Aggiunta del supporto per i database di Access che utilizzano criteri di gruppo di lavoro.  
-   Fornita la possibilità di eliminare gli oggetti convertiti da Visualizzatore metadati SQL Server.  
-   Aggiunta del supporto per i commenti immessi dall'utente in SQL Server in formato modalità SQL.  
-   Aggiunti miglioramenti per la conversione di oggetti.  
  
## <a name="november-2006"></a>Novembre 2006  
La versione di SSMA per Access novembre 2006 contiene le seguenti modifiche:  
  
-   Aggiungere una nuova migrazione guidata di Database che agevola la migrazione di un singolo database da Access a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
-   Aggiungere una nuova conversione, caricamento, e il comando Esegui migrazione che converte i database di Access, carica oggetti convertiti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], e viene eseguita la migrazione di dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] un'unica operazione.  
-   Migrazione di query superiori. Eseguire una query migrazione ora converte selezionare più query di viste. Per ulteriori informazioni, vedere [la conversione di oggetti di Database di Access](http://msdn.microsoft.com/en-us/e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c).  
-   Aggiunta la possibilità di modificare le proprietà di tabelle e indici sul [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **tabella** scheda.  
-   Aggiunte nuove impostazioni globali:  
    -   È possibile scegliere di visualizzare i numeri di riga nelle finestre dell'editor.  
    -   È possibile configurare SSMA per la richiesta di sostituire gli oggetti duplicati o sempre o mai sostituire oggetti duplicati durante la conversione dello schema.  
-   Aggiunta una nuova opzione di conversione che consente di specificare se SSMA viene visualizzato un avviso quando una query complessa contiene un carattere jolly.  
  
## <a name="july-2006"></a>Luglio 2006  
La versione di SSMA per Access luglio 2006 costituisce la versione iniziale.
