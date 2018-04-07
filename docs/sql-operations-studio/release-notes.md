---
title: Note sulla versione di Microsoft SQL Operations Studio (anteprima) | Microsoft Docs
description: Note sulla versione di Microsoft SQL Operations Studio (anteprima)
ms.custom: tools|sos
ms.date: 03/28/2018
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: article
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ba86403e791af25de4f7bcd8b1cbd7b5f188897b
ms.sourcegitcommit: d6881107b51e1afe09c2d8b88b98d075589377de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2018
---
# <a name="sql-operations-studio-preview-release-notes"></a>Note sulla versione di SQL Operations Studio (anteprima)

**[Scaricare l'anteprima pubblica di marzo](download.md)**

## <a name="march-2018-march-public-preview"></a>Marzo 2018 (anteprima pubblica di marzo)

Data di rilascio: 28 marzo 2018  
versione: 0.27.3

L'*anteprima pubblica di marzo* continua a rivolgersi ai principali issue su GitHub e si concentra sul miglioramento dell'estendibilità. In particolare, è stato aggiunto il pannello di gestione delle estensioni, è stata migliorata la gestione delle dashboard e sono stati introdotti il supporto a SQL Agent e le estensioni di insight. Questa versione include i miglioramenti seguenti:

- Migliorato il modello di estendibilità delle dashboard tramite l'aggiunta del supporto di schede per gli insight e riquadri di configurazione.
   - Aggiunto il pannello **ESTENSIONI**, che consente la semplice acquisizione delle estensioni.
   - Aggiunta un'estensione per *sp_whoisactive* da [whoisactive.com](http://www.whoisactive.com).
   - Per informazioni dettagliate, vedere [estendere le funzionalità di SQL Operations Studio](extensions.md).
- Aggiunte ulteriori [API di estendibilità per le connessioni ed Esplora Oggetti](https://github.com/Microsoft/sqlopsstudio/wiki/Extensibility-API).
- Correzioni degli [issue di GitHub](https://github.com/Microsoft/sqlopsstudio/issues) ad alto impatto sui clienti.

Per ulteriori informazioni, vedere il [log delle modifiche](https://github.com/Microsoft/sqlopsstudio/blob/master/CHANGELOG.md).


## <a name="february-2018-february-public-preview"></a>Febbraio 2018 (anteprima pubblica di febbraio)

Data di rilascio: 15 febbraio 2018  
version: 0.26.7

L'*anteprima pubblica di febbraio* include alcuni suggerimenti sulle funzionalità e correzioni di bug con priorità alta. Questa versione include i miglioramenti seguenti:

- Introdotta la funzionalità di aggiornamento automatico, che mostra una notifica quando una nuova versione è disponibile per il download. 
- Il campo 'Database' della finestra di dialogo di connessione è ora un elenco a discesa popolato in modo dinamico dall'elenco dei database presenti nel server specificato.
- Corretto l'[issue 6](https://github.com/Microsoft/sqlopsstudio/issues/6): Mantieni la connessione e il database selezionato quando si aprono nuove schede di query.
- Corretto l'[issue 22](https://github.com/Microsoft/sqlopsstudio/issues/22): 'Server' e 'Database' - è possibile trasformarli in elenchi a discesa anziché caselle di testo?
- Corretto l'[issue 549](https://github.com/Microsoft/sqlopsstudio/issues/549): Le installazioni con il parametro Silent/VerySilent fanno aprire l'applicazione subito dopo la fine del setup.
- Corretto l'[issue 481](https://github.com/Microsoft/sqlopsstudio/issues/481): Aggiungere l'opzione "Controlla aggiornamenti".
- Correzioni riguardanti l'editor SQL e il completamento automatico:
   - Corretto l'[issue 584](https://github.com/Microsoft/sqlopsstudio/issues/584): La parola chiave 'FULL' non è evidenziata da IntelliSense.
   - Corretto l'[issue 345](https://github.com/Microsoft/sqlopsstudio/issues/345): Colorare le funzioni SQL all'interno dell'editor.
   - Corretto l'[issue 300](https://github.com/Microsoft/sqlopsstudio/issues/300): In una stringa [#tempData] il carattere finale "]" verrà visualizzato di colore verde.
   - Corretto l'[issue 225](https://github.com/Microsoft/sqlopsstudio/issues/225): Mancata corrispondenza di colore su parola chiave.
   - Corretto l'[issue 60](https://github.com/Microsoft/sqlopsstudio/issues/60): Colore non valido quando si utilizza una tabella temporanea nella clausola from.
- Introdotta l'API di estensibilità di connessione.
- Aggiunta l'integrazione dell'editor di codice di Visual Studio 1.19.
- Aggiornato il componente JustinPealing/query-plan per ottenere diversi miglioramenti sul visualizzatore dei piani di query.


## <a name="january-2018-january-public-preview"></a>Gennaio 2018 (anteprima pubblica di gennaio)

Data di rilascio: 17 gennaio 2018  
versione: 0.25.4

L'*anteprima pubblica di gennaio* include alcuni suggerimenti sulle funzionalità e correzioni di bug con priorità alta. Questa versione include i miglioramenti seguenti:

- Le connessioni server salvate sono disponibili nella finestra di dialogo di connessione.
- Aggiunta l'uscita a caldo, disattivata per impostazione predefinita. Per abilitarla vedere [impostazione uscita a caldo](settings.md#hot-exit).
- Ogni scheda è ora contraddistinta dal colore del relativo gruppo di server. La colorazione della scheda è disattivata per impostazione predefinita, per abilitare vedere [impostazione del colore di una scheda](settings.md#tab-color).
- Modificata l'etichetta *Nome Server* in *Server* nella finestra di dialogo di connessione.
- Corretto il comando non funzionante *Esegui Query corrente*.
- Corretto il drag-and-drop dei bug di scripting.
- Corretta l'icona per il pin sul Menu Start.
- Aggiunta l'icona mancante dell'Account di Azure.


## <a name="december-2017-december-public-preview"></a>Dicembre 2017 (anteprima pubblica di dicembre)

Data di rilascio: 19 dicembre 2017  
version: 0.24.1

L'*anteprima pubblica di dicembre* include diverse correzioni di bug in tutte le aree di funzionalità, nonché i miglioramenti seguenti:

- La finestra di dialogo per l'aggiunta automatica della regola del firewall è ora disponibile per consentire la connessione a Database SQL di Azure e Azure SQL Data Warehouse.
- Aggiunta l'installazione di Windows e Linux DEB e i pacchetti di installazione RPM.
- Aggiunto l'editor di layout della dashboard.
- Aggiunti i comandi *Script come ALTER* e *Script come EXECUTE*.
- Aggiunto il comando *Esegui la query corrente con il piano effettivo*.
- Integrato l'editor di codice di Visual Studio 1.18.1.
- Abilitato il caricamento dei file di estensione VSIX.
- Aggiunto il supporto per la sintassi batch `GO N`.


## <a name="november-2017"></a>Novembre 2017

Data di rilascio: 15 novembre 2017  
versione: 0.23.6

- Versione iniziale di [!INCLUDE[name-sos](../includes/name-sos-short.md)].


## <a name="next-steps"></a>Passaggi successivi

Seguire una delle guide rapide qui sotto per iniziare:
- [Connettersi ed eseguire query in SQL Server](quickstart-sql-server.md)
- [Connettersi ed eseguire query in Database SQL di Azure](quickstart-sql-database.md)
- [Connettersi ed eseguire query in Azure Data Warehouse](quickstart-sql-dw.md)

Contribuire a [!INCLUDE[name-sos](../includes/name-sos-short.md)]:
- [https://github.com/Microsoft/sqlopsstudio](https://github.com/Microsoft/sqlopsstudio)
