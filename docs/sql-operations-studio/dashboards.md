---
title: Accedere rapidamente alle informazioni e le attività comuni in Studio operazioni SQL (anteprima) | Documenti Microsoft
description: Informazioni sulla visualizzazione dei widget dettagliati in Studio operazioni SQL (anteprima).
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: article
author: yualan
ms.author: alayu
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ad7fcbab5a01828cccd855da2d65ba3199e0b41b
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="dashboards-in-includename-sosincludesname-sos-shortmd"></a>Dashboard in [!INCLUDE[name-sos](../includes/name-sos-short.md)]

Per visualizzare un dashboard, scelta di un server o database e selezionare **Gestisci**.

![Dashboard di esempio](media/dashboards/sample-dashboard.png)

**Proprietà server** contiene le proprietà del server, tra cui versione, versione, nome del Computer e versione del sistema operativo.

**Attività** contiene attività commons come nuova Query e di ripristino.

**I database di ricerca** cercare facilmente i database esistenti archiviati nel server, incluse le tabelle.

**Stato backup** cercare facilmente lo stato del backup per i database esistenti.

## <a name="configuring-insight-widgets"></a>Configurazione widget Insight
Si consiglia di seguire l'esercitazione per la configurazione di dashboard, che può essere trovato [qui](tutorial-build-custom-insight-sql-server.md).

Inoltre, assicurarsi di estrarre il [procedure sulla configurazione widget insight]().

Dopo questa esercitazione, leggere per ulteriori informazioni sui widget specifici che non sono trattati in questa esercitazione.

## <a name="insight-detail"></a>Dettagli informazioni dettagliate
Il riquadro a comparsa Dettagli informazioni fornisce informazioni più dettagliate per un widget di informazioni correlate. 
- Un widget Insight esegue il rendering di una vista di riepilogo in immediate con numero di riga, grafico e così via. 
- Il riquadro a comparsa Dettagli informazioni dettagliate vengono fornite informazioni dettagliate "drill in", elenco approfondite dei dati per ogni elemento elencato nel widget di informazioni di alto livello. 
  - Il contenuto del riquadro a comparsa dettagli è definito con una query SQL separata per query principale del widget. 

Non è necessario impostare per una query di dettagli informazioni dettagliate, ma il layout è standard.
- La metà superiore della visualizzazione è sempre una visualizzazione "riepilogo" 2-colonna. Le colonne da utilizzare sono definite dalle proprietà della configurazione JSON "label" e "value"
- Su facendo clic su una riga nella tabella di riepilogo, nella parte inferiore del riquadro a comparsa la metà elencherà il set completo di informazioni di colonna per la riga.

### <a name="insight-detail-configuration-in-packagejson"></a>Configurazione di dettaglio informazioni dettagliate nel file package. JSON

Configurazione di esempio Insight dettagli riquadro a comparsa
```json
"details": {
    "queryFile": "./relative_path_to_sqlfile_from_package_json_file.sql",
    "label": {
        "icon": "database",
        "column": "first_column_name_for_summary_list_view",
        "state": [
            {
                "condition": {
                    "if": "equals",
                    "equals": "0"
                },
                "color": "red"
            },
            {
                "condition": {
                    "if": "equals",
                    "equals": "1"
                },
                "color": "orange"
            },
            {
                "condition": {
                    "if": "equals",
                    "equals": "2"
                },
                "color": "green"
            }
        ]
    },
    "value": "second_column_and_condition_check_value_column_for_summary_list_view",
```
|proprietà|Tipo|Valore|Valore predefinito|description|comment|
|:---|:---|:---|:---|:---|:---|
|dettagli|oggetto JSON|||proprietà obbligatoria per specificare le definizioni di dettaglio informazioni all'interno della struttura||
|queryFile|string|||il percorso del file query sql detail insight e il nome relativo alla posizione del file package. JSON||
|Etichetta|oggetto JSON|||proprietà obbligatoria per definire ogni elemento di riga nella visualizzazione elenco riepilogo|in futuro il nome di questa proprietà per modificare ad esempio 'summaryList'|
|Icona|string|||indicare il nome dell'icona per ogni elemento della visualizzazione elenco di riepilogo per riprodurre.|verrà documentato elenco (da definire) delle icone supportate|
|column|string|||indicare il nome della prima colonna nella visualizzazione elenco di riepilogo dal set di risultati della query|in futuro verrà modificato il nome di questa proprietà per un nome più intuitivo|
|Valore|string|||indicare il nome della seconda colonna nella visualizzazione elenco di riepilogo dal set di risultati della query. Il valore di questa colonna viene utilizzato per controllare le condizioni e impostare i colori per punto di colore di ogni elenco di riepilogo Visualizza elementi|in futuro si modificherà il nome di questa proprietà su un valore più intuitiva|
|condizione|oggetto JSON|||definisce il controllo di condizione per il valore di colonna e determinare colore per ogni elemento della visualizzazione elenco riepilogo||
|if|string|è sempre uguale a, diverso da, greaterThan, lessThan, greaterThanOrEqauls, lessThanOrEquals||operatore di controllo di condizione|in futuro si modificherà il nome della proprietà a operatore|
|equals|string|||valore di controllo di condizione|in futuro si modificherà il nome della proprietà 'value'|

## <a name="insight-actions"></a>Azioni dettagliate
Con un widget di informazioni dettagliate e informazioni dettagliate, possono verificarsi facilmente un piano d'azione per ridurre un errore o gestire. Ad esempio, si verrà considerare l'esecuzione di DBCC CHECKDB, leggere i log degli errori o quando un database è in un ripristino in sospeso, ripristinare il database. Oppure può essere una delle azioni che si desiderano eseguire.

Utilizzando [!INCLUDE[name-sos](../includes/name-sos-short.md)]della configurazione di azioni di informazioni dettagliate, è possibile mappare un azioni predefinite come ripristinare o riportare la propria azione definita con uno script sql.

> Configurazione delle azioni personalizzate utilizzando uno script sql è in fase di sviluppo e non è disponibile nella build di anteprima privata ancora.

## <a name="sample-insight-action-definition"></a>Definizione dell'azione di informazioni di esempio

```"actions"{}``` Definisce un'azione di una visione. Azione può essere definita su un ambito specifico, ad esempio ```"server"```, ```"database"``` e così via e [!INCLUDE[name-sos](../includes/name-sos-short.md)] passa le informazioni sul contesto di connessione corrente all'azione. 

Ad esempio, quando l'azione di ripristino viene avviata per il database WideWorldImporters, ```"database": "${Database}"``` definizione indica di passare ```Database``` valore della colonna nel risultato della query per l'azione di ripristino. Azione di ripristino avvia quindi il database. ```"types"``` è una matrice json e più azioni possono essere elencate nella matrice. Fondamentalmente, diventa un menu di scelta rapida nella finestra di dialogo Dettagli informazioni dettagliate che l'utente può scegliere ed eseguire l'azione. 

> [!INCLUDE[name-sos](../includes/name-sos-short.md)] Anteprima 0.17.1 è abilitata "backup", "ripristino", "nuova query" e "nuovo database" come tipi di azione.

```json
"details": {
    "queryFile": "./sql/database_state_detail.sql",
    "label": {...},
    "value": "state",
    "actions": {
        "database": "${Database}",
        "types": ["restore"]
    }
}
```
