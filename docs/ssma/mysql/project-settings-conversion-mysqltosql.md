---
title: Impostazioni (conversione) (MySQLToSQL) del progetto | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 7ad5fe44-6445-4ba8-a457-5af792631f11
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 64a3bbdfccc278a795c32bc6bf863c1875912601
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47744669"
---
# <a name="project-settings-conversion-mysqltosql"></a>Impostazioni del progetto (conversione) (MySQLToSQL)
La pagina di conversione del **impostazioni del progetto** nella finestra di dialogo contiene impostazioni che consentono di personalizzare come SSMA Converte la sintassi di MySQL in sintassi SQL Server o SQL Azure.  
  
Nel riquadro di conversione è disponibile nel **impostazioni del progetto** e **impostazioni di progetto predefinite** finestre di dialogo.  
  
-   Usare la **impostazioni di progetto predefinite** finestra di dialogo per impostare le opzioni di configurazione per tutti i progetti. Per accedere a impostazioni di conversione, scegliere il **strumenti** dal menu **impostazioni di progetto predefinite**, selezionare tipo di progetto di migrazione per i quali impostazioni sono necessarie per essere visualizzati / modificato da  **Versione di destinazione della migrazione** elenco a discesa, fare clic su **generali** nella parte inferiore del riquadro a sinistra e quindi selezionare **conversione**.  
  
-   Per specificare le impostazioni per il progetto corrente, il **strumenti** menu fare clic su **le impostazioni del progetto**, quindi fare clic su **generale** nella parte inferiore del riquadro di sinistra e quindi fare clic su **Conversione**.  
  
## <a name="options"></a>Opzioni  
  
### <a name="collate-clause"></a>Clausola COLLATE  
  
|||  
|-|-|  
|**Nome**|**Definizione**|  
|**Conversione esplicita di clausola COLLATE**|Opzione di conversione esplicita COLLATE clausola specifica come eseguire la conversione esplicitare clausole COLLATE nel codice di MySQL. Le scelte possibili: Ignorare e contrassegnare con un messaggio di avviso / genera un errore<br /><br />**Modalità predefinita**: ignorare e contrassegnare con un messaggio di avviso<br /><br />**La modalità ottimistico**: ignorare e contrassegnare con un messaggio di avviso<br /><br />**Modalità intero**: ignorare e contrassegnare con un messaggio di avviso|  
  
### <a name="column-constraints"></a>Vincoli di colonna  
  
|||  
|-|-|  
|**Nome**|**Definizione**|  
|**Generare vincoli per le colonne di tipo di dati di Enumerazione**|Genera vincoli per le colonne di tipo di dati di Enumerazione nella tabella di SQL Server o SQL Azure, se non è presente nella tabella di MySQL. In caso affermativo, tutte le colonne convertite del tipo di dati di Enumerazione sono accompagnate dal vincolo CHECK, controllare il valore.<br /><br />**Modalità predefinita**: No<br /><br />**La modalità ottimistico**: No<br /><br />**Modalità intero**: Sì|  
|**Generare vincoli per le colonne di tipo di SET di dati**|Genera i vincoli per le colonne di tipo di SET di dati della tabella di SQL Server o SQL Azure, se non è presente nella tabella di MySQL. In caso affermativo, tutte le colonne convertite della tipo di SET di dati sia associate a vincolo CHECK, controllare il valore.<br /><br />**Modalità predefinita**: No<br /><br />**La modalità ottimistico**: No<br /><br />**Modalità intero**: Sì|  
|**Generare vincoli per le colonne delle colonne di tipo di dati numerico senza segno**|Aggiungi il controllo per un valore non negativo alle colonne dei tipi di dati numerico senza segno.<br /><br />**Modalità predefinita**: No<br /><br />**La modalità ottimistico**: No<br /><br />**Modalità intero**: Sì|  
|**Generazione di vincolo per colonne di tipo anno dei dati**|Genera l'errore di vincolo per colonne di tipo anno dei dati nella tabella SQL Server o SQL Azure, se non è presente nella tabella MySQL. In caso affermativo, tutti convertiti colonne di tipo sia associato a vincolo CHECK, controllare il valore di dati dell'anno.<br /><br />**Modalità predefinita**: No<br /><br />**La modalità ottimistico**: No<br /><br />**Modalità intero**: Sì|  
  
### <a name="data-types"></a>Tipi di dati  
  
|||  
|-|-|  
|**Nome**|**Definizione**|  
|**Conversione del tipo di dati di Enumerazione**|Specifica come tipo di dati MySQL ENUM deve essere convertito come Convert a NVARCHAR o convertito in numerico<br /><br />**Modalità predefinita**: Converti in NVARCHAR<br /><br />**La modalità ottimistico**: Converti in NVARCHAR<br /><br />**Modalità intero**: Converti in NVARCHAR|  
|**Conversione di tipi SET di dati**|Specifica come tipo di dati di MySQL impostata è deve essere convertito, convertire i per NVARCHAR (L) / convertire BINARY(L)<br /><br />**Modalità predefinita**: convertire NVARCHAR(L)<br /><br />**La modalità ottimistico**: convertire NVARCHAR(L)<br /><br />**Modalità intero**: convertire NVARCHAR(L)|  
  
### <a name="generic"></a>Generico  
  
|||  
|-|-|  
|**Nome**|**Definizione**|  
|**Colonne senza un valore predefinito di inserimento e sostituzione**|In caso affermativo, tutte le istruzioni che fanno riferimento a tabelle utilizzando stored motori diversi da MyISAM e InnoDb devono essere contrassegnate con messaggi di avviso di conversione.<br /><br />**Modalità predefinita**: aggiungere all'elenco di colonne<br /><br />**La modalità ottimistico**: aggiungere all'elenco di colonne<br /><br />**Modalità intero**: aggiungere all'elenco di colonne|  
|**Divisione per Zero genera la conversione**|Specifica se emulare MySQL senza comportamento ERROR_FOR_DIVISION_BY_ZERO o meno.<br /><br />**Modalità predefinita**: errore<br /><br />**La modalità ottimistico**: errore<br /><br />**Modalità intero**: NULL|  
|**Operatore IN**|Specifica come convertire operatore IN MySQL.<br /><br />**Modalità predefinita**: converte sempre in India<br /><br />**La modalità ottimistico**: converte sempre in India<br /><br />**Modalità intero**: espandere se necessario|  
|**Conversione di MySQL (funzione)**|Specifica come convertire le funzioni standard di MySQL.<br /><br />**Modalità predefinita**: ottimistica<br /><br />**La modalità ottimistico**: ottimistica<br /><br />**Modalità intero**: preciso|  
|**Non supportati motori di archiviazione**|In caso affermativo, tutte le istruzioni che fanno riferimento a tabelle utilizzando stored motori diversi da MyISAM e InnoDb devono essere contrassegnate con messaggi di avviso di conversione.<br /><br />**Modalità predefinita**: No<br /><br />**La modalità ottimistico**: No<br /><br />**Modalità intero**: Sì|  
|**Eliminare la generazione di colonna ausiliario ROWID**|In caso affermativo, impedisce la creazione della creazione di colonne ausiliario ROWD nelle tabelle di destinazione. Potrebbero influire sulla migrazione di alcune strutture.<br /><br />**Modalità predefinita**: No<br /><br />**La modalità ottimistico**: No<br /><br />**Modalità intero**: No|  
|**Conversione di istruzioni TRUNCATE**|Specifica come eseguire la conversione di istruzioni TRONCATE.<br /><br />**Modalità predefinita**: TRUNCATE<br /><br />**La modalità ottimistico**: TRUNCATE<br /><br />**Modalità intero**: TRUNCATE|  
  
### <a name="misc"></a>Varie  
  
|||  
|-|-|  
|**Nome**|**Definizione**|  
|**Mapping dello Schema predefinito**|Specifica come eseguire il mapping di database MySQL in schemi di SQL Server.<br /><br />**Modalità predefinita**: Database in<br /><br />**La modalità ottimistico**: Database in<br /><br />**Modalità intero**: Database in|  
  
### <a name="procedures-and-functions"></a>Procedure e funzioni  
  
|||  
|-|-|  
|**Nome**|**Definizione**|  
|**Conversione di funzione predefinita**|Specifica se le funzioni devono essere per impostazione predefinita essere convertiti in funzioni T-SQL o alle stored procedure.<br /><br />**Modalità predefinita**: convertire (funzione)<br /><br />**La modalità ottimistico**: convertire (funzione)<br /><br />**Modalità intero**: convertire (funzione)|  
|**Generare SET XACT_ABORT su**|Specifica se SET XACT_ABORT su ON deve essere aggiunto all'inizio della procedura convertito o del trigger.<br /><br />**Modalità predefinita**: Sì<br /><br />**La modalità ottimistico**: Sì<br /><br />**Modalità intero**: Sì|  
|**Generare SET NOCOUNT su**|Specifica se SET NOCOUNT ON deve essere aggiunto all'inizio della procedura convertito o del trigger.<br /><br />**Modalità predefinita**: Sì<br /><br />**La modalità ottimistico**: Sì<br /><br />**Modalità intero**: Sì|  
  
### <a name="spatial-data-types"></a>Tipi di dati spaziali  
  
|||  
|-|-|  
|**Nome**|**Definizione**|  
|**Rettangolo delimitatore predefinito {XMAX&#124;XMIN&#124;YMAX&#124;YMIN} per gli indici spaziali**|Definisce il valore predefinito per {XMAX&#124;XMIN&#124;YMAX&#124;YMIN} parametro del rettangolo utilizzate negli indici spaziali.<br /><br />**Modalità predefinita**<br /><br />XMAX: 100<br /><br />XMIN: 0<br /><br />YMAX: 100<br /><br />YMIN: 0<br /><br />**Modalità ottimistico**<br /><br />XMAX: 100<br /><br />XMIN: 0<br /><br />YMAX:  100<br /><br />YMIN: 0<br /><br />**Modalità completa**<br /><br />XMAX: 100<br /><br />XMIN: 0<br /><br />YMAX: 100<br /><br />YMIN: 0|  
|**Densità della griglia predefinita per gli indici spaziali**|Definisce il valore predefinito per LEVEL_1, LEVEL_2, LEVEL_3 e LEVEL_4 di densità della griglia utilizzate negli indici spaziali.<br /><br />**Modalità predefinita**<br /><br />LEVEL_1: predefinito<br /><br />LEVEL_2: predefinito<br /><br />LEVEL_3: predefinito<br /><br />LEVEL_4: predefinito<br /><br />**Modalità ottimistico**<br /><br />LEVEL_1: predefinito<br /><br />LEVEL_2: predefinito<br /><br />LEVEL_3: predefinito<br /><br />LEVEL_4: predefinito<br /><br />**Modalità completa**<br /><br />LEVEL_1: predefinito<br /><br />LEVEL_2: predefinito<br /><br />LEVEL_3: predefinito<br /><br />LEVEL_4: predefinito|  
  
### <a name="transactions"></a>Transazioni  
  
|||  
|-|-|  
|**Nome**|**Definizione**|  
|**Tabelle non transazionale**|Specifica se tutti i riferimenti alla tabella che non supportano le transazioni devono essere contrassegnati con messaggi di avviso di conversione.<br /><br />**Modalità predefinita**: No<br /><br />**La modalità ottimistico**: No<br /><br />**Modalità intero**: Sì|  
|**Livello di isolamento delle transazioni**|Specifica il livello di isolamento delle transazioni deve essere utilizzato per le nuove transazioni.<br /><br />**Modalità predefinita**: predefinito<br /><br />**La modalità ottimistico**: predefinito<br /><br />**Modalità intero**: lettura ripetibile|  
  
### <a name="value-control"></a>Controllo valore  
  
|||  
|-|-|  
|**Nome**|**Definizione**|  
|**Carattere per la conversione numerica**|Specifica come gestire la conversione implicita ed esplicita dal tipo di dati Character a tipi di dati numerici.<br /><br />**Modalità predefinita**: ottimistica<br /><br />**La modalità ottimistico**: ottimistica<br /><br />**Modalità intero**: preciso|  
|**Controllare i valori numerici senza segno**|Controllo assegnazione di valori per parametri e variabili numeriche senza segno.<br /><br />**Modalità predefinita**: No<br /><br />**La modalità ottimistico**: No<br /><br />**Modalità intero**: Sì|  
|**Controllare la sottrazione non FIRMATA**|Modificare i valori negativi inseriti nelle colonne di tabella del tipo di dati senza segno.<br /><br />**Modalità predefinita**: convertire ' come-è '<br /><br />**La modalità ottimistico**: convertire ' come-è '<br /><br />**Modalità intero**: contrassegno con un messaggio di avviso|  
|**Conversione da e verso il tipo di dati binari**|Specifica come gestire le conversioni implicite ed esplicite dal tipo di dati binari.<br /><br />**Modalità predefinita**: ottimistica<br /><br />**La modalità ottimistico**: ottimistica<br /><br />**Modalità intero**: preciso|  
|**Tipo di conversione in dati di data/ora**|Specifica la modalità di conversione impliciti ed espliciti a data/ora di gestire tipi di dati.<br /><br />**Modalità predefinita**: formato emulare MySQL<br /><br />**La modalità ottimistico**: formato di uso di SQL Server<br /><br />**Modalità intero**: formato emulare MySQL|  
|**Valori letterali numerici con precisione superiore a 38**|Specifica come convertire i valori letterali numerici con precisione superiore a 38.<br /><br />**Modalità predefinita**: arrotondare se possibile<br /><br />**La modalità ottimistico**: arrotondare se possibile<br /><br />**Modalità intero**: arrotondare se possibile|  
|**Zero-date nelle colonne NOT NULL**|Specifica come gestire l'assegnazione per le colonne NOT NULL di Zero-date, Zero-in-date o valori data/ora non valido.<br /><br />**Modalità predefinita**: GETDATE)<br /><br />**La modalità ottimistico**: GETDATE)<br /><br />**Modalità intero**: GETDATE)|  
  
## <a name="see-also"></a>Vedere anche  
[Riferimento all'interfaccia utente &#40;MySQLToSQL&#41;](../../ssma/mysql/user-interface-reference-mysqltosql.md)  
  
