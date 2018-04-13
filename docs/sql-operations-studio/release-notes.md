---
title: Note sulla versione di Microsoft SQL Operations Studio (preview) | Documenti Microsoft
description: Note sulla versione di Microsoft SQL Operations Studio (preview)
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
# <a name="sql-operations-studio-preview-release-notes"></a>Note sulla versione SQL Operations Studio (preview)

**[Scaricare l'anteprima pubblica di marzo](download.md)**

## <a name="march-2018-march-public-preview"></a>2018 marzo (marzo in anteprima pubblica)

Data di rilascio: il 28 marzo 2018  
version: 0.27.3

Il *anteprima pubblica di marzo* continua a risolvere i problemi principali GitHub e si concentra sul miglioramento della nostra storia di estendibilità. In particolare l'abilitazione estensione Manager, il miglioramento della gestione di dashboard e fornire SQL Agent e le estensioni di insights. Questa versione include i miglioramenti seguenti:

- Migliorare il modello di estendibilità del dashboard per supportare insights a schede e riquadri di configurazione.
   - Gestore estensioni del attiva semplice acquisizione delle estensioni.
   - Le estensioni del dashboard per sp_whoisactive dal [whoisactive.com](http://www.whoisactive.com).
   - Per informazioni dettagliate, vedere [estendere le funzionalità di SQL Operations Studio](extensions.md).
- Aggiungere ulteriori [API di estendibilità per la connessione e oggetto explorer](https://github.com/Microsoft/sqlopsstudio/wiki/Extensibility-API) management.
- Continuare a correggere i clienti che hanno un impatto [problemi GitHub](https://github.com/Microsoft/sqlopsstudio/issues).

Per ulteriori informazioni, vedere il [registro delle modifiche](https://github.com/Microsoft/sqlopsstudio/blob/master/CHANGELOG.md).


## <a name="february-2018-february-public-preview"></a>2018 febbraio (febbraio in anteprima pubblica)

Data di rilascio: 15 febbraio 2018  
version: 0.26.7

Il *anteprima pubblica di febbraio* include alcuni suggerimenti sulle funzionalità e correzioni di bug con priorità alta. Questa versione include i miglioramenti seguenti:

- Che l'introduzione di installazione di aggiornamento automatico, fornisce una notifica quando una nuova versione è disponibile per il download 
- Il campo di finestra di dialogo di connessione 'Database' è un elenco di riepilogo a discesa popolato in modo dinamico contenenti un elenco di database popolato dal server specificato.
- Correggere [emettere 6](https://github.com/Microsoft/sqlopsstudio/issues/6): Mantieni connessione e il database selezionato quando si apre nuove schede di query.
- Correggere [emettere 22](https://github.com/Microsoft/sqlopsstudio/issues/22): "Nome Server" e 'Nome di Database -' possono questi essere elenchi a discesa anziché le caselle di testo?
- Correggere [emettere 549](https://github.com/Microsoft/sqlopsstudio/issues/549): installazione invisibile all'utente invisibile all'utente/molto comporterà l'applicazione che apre dopo l'installazione.
- Correggere [emettere 481](https://github.com/Microsoft/sqlopsstudio/issues/481): aggiungere l'opzione "Controlla aggiornamenti".
- Editor SQL colorazione e correzioni di completamento automatico:
   - Correggere [emettere 584](https://github.com/Microsoft/sqlopsstudio/issues/584): parola chiave "Completa" non è evidenziata da IntelliSense.
   - Correggere [emettere 345](https://github.com/Microsoft/sqlopsstudio/issues/345): funzioni colorare SQL all'interno dell'editor.
   - Correggere [emettere 300](https://github.com/Microsoft/sqlopsstudio/issues/300): [#tempData] più recente "]" verrà visualizzato di colore verde.
   - Correggere [emettere 225](https://github.com/Microsoft/sqlopsstudio/issues/225): mancata corrispondenza di colore (parola chiave).
   - Correggere [emettere 60](https://github.com/Microsoft/sqlopsstudio/issues/60): sql non valido Colore evidenziazione della sintassi quando si utilizza la tabella temporanea nella clausola from.
- Introdurre API di estensibilità di connessione.
- Integrazione di Visual Studio 1.19 Editor di codice.
- Aggiornare il componente JustinPealing/html-piano di query al ritiro diversi miglioramenti di Visualizzatore di piano di Query.


## <a name="january-2018-january-public-preview"></a>2018 gennaio (anteprima pubblica di gennaio)

Data di rilascio: 17 gennaio 2018  
versione: 0.25.4

Il *anteprima pubblica di gennaio* include alcuni suggerimenti sulle funzionalità e correzioni di bug con priorità alta. Questa versione include i miglioramenti seguenti:

- Connessioni Server salvate sono disponibili nella finestra di dialogo di connessione.
- Abilitare l'uscita a caldo. Uscita frequente è disattivata per impostazione predefinita, per abilitare vedere [impostazione uscita Hot](settings.md#hot-exit).
- Scheda contraddistinta dal colore in base a gruppo di Server. La colorazione della scheda è disattivata per impostazione predefinita, per abilitare vedere [scheda impostazione del colore](settings.md#tab-color).
- Modifica *nome Server* a *Server* nella finestra di dialogo di connessione.
- Correzione suddiviso *Esegui Query corrente* comando.
- Correggere l'interruzione di trascinamento e rilascio bug di scripting.
- Correggere icona Menu Start aggiunto non corretta.
- Correggere l'icona di branding mancante Account di Azure.


## <a name="december-2017-december-public-preview"></a>Dicembre 2017 (anteprima pubblica di dicembre)

Data di rilascio: 19 dicembre 2017  
version: 0.24.1

Il *anteprima pubblica di dicembre* include diverse correzioni di bug in tutte le aree di funzionalità, nonché i miglioramenti seguenti:

- Creare finestra di dialogo regola Firewall è ora disponibile per consentire la connessione a Database SQL di Azure e Azure SQL Data Warehouse.
- Aggiunto l'installazione di Windows e Linux DEB e RPM pacchetti di installazione.
- Gestire l'editor di layout visivo del Dashboard.
- *Script di modifica come* e *Script come eseguire* comandi.
- *Eseguire la Query corrente con il piano effettivo* comando.
- Integrare il codice di Visual Studio 1.18.1 editor platform.
- Abilitare i file di trasferimento locale di estensione VSIX.
- Supporta la sintassi di iterazione batch "Vai N".


## <a name="november-2017"></a>2017 novembre

Data di rilascio: 15 novembre 2017  
versione: 0.23.6

- Versione di iniziale [!INCLUDE[name-sos](../includes/name-sos-short.md)].


## <a name="next-steps"></a>Passaggi successivi

Vedere una delle Guide rapide seguenti per iniziare:
- [Connetti & Query in SQL Server](quickstart-sql-server.md)
- [Connettersi & Query di Database SQL di Azure](quickstart-sql-database.md)
- [Connettersi & Query Azure Data Warehouse](quickstart-sql-dw.md)

Contribuire a [!INCLUDE[name-sos](../includes/name-sos-short.md)]:
- [https://github.com/Microsoft/sqlopsstudio](https://github.com/Microsoft/sqlopsstudio)
