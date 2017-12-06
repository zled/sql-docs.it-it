---
title: Impostazioni (conversione) (MySQLToSQL) del progetto | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-mysql
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 7ad5fe44-6445-4ba8-a457-5af792631f11
caps.latest.revision: "19"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5c40fe3bcc95b062b188c041477011358d60fba2
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="project-settings-conversion-mysqltosql"></a>Impostazioni del progetto (conversione) (MySQLToSQL)
La pagina di conversione del **impostazioni progetto** la finestra di dialogo contiene le impostazioni che consentono di personalizzare la modalità SSMA converte sintassi MySQL alla sintassi SQL Server o SQL Azure.  
  
Il riquadro di conversione è disponibile nel **impostazioni progetto** e **impostazioni di progetto predefinite** finestre di dialogo.  
  
-   Utilizzare il **impostazioni di progetto predefinite** la finestra di dialogo per impostare le opzioni di configurazione per tutti i progetti. Per accedere alle impostazioni di conversione, nel **strumenti** dal menu **impostazioni di progetto predefinite**, selezionare il tipo di progetto di migrazione per i quali impostazioni sono necessarie per essere visualizzati o modificati da **versione di destinazione della migrazione** elenco a discesa, fare clic su **generale** nella parte inferiore del riquadro sinistro, quindi scegliere **conversione**.  
  
-   Per specificare le impostazioni per il progetto corrente, il **strumenti** dal menu **impostazioni progetto**, quindi fare clic su **generale** nella parte inferiore del riquadro sinistro e quindi fare clic su **conversione**.  
  
## <a name="options"></a>Opzioni  
  
### <a name="collate-clause"></a>Clausola COLLATE  
  
|||  
|-|-|  
|**Nome**|**Definizione**|  
|**Conversione esplicita di clausola COLLATE**|Opzione di conversione esplicita COLLATE clausola specifica la modalità di conversione esplicite clausole COLLATE nel codice di MySQL. Le scelte possibili: Ignorare e contrassegnare con un messaggio di avviso / genera un errore<br /><br />**Modalità predefinita**: ignorare e contrassegnare con un messaggio di avviso<br /><br />**Modalità ottimistica**: ignorare e contrassegnare con un messaggio di avviso<br /><br />**Modalità**: ignorare e contrassegnare con un messaggio di avviso|  
  
### <a name="column-constraints"></a>Vincoli di colonna  
  
|||  
|-|-|  
|**Nome**|**Definizione**|  
|**Generare i vincoli per le colonne di tipo di dati di Enumerazione**|Genera l'errore di vincolo per le colonne di tipo di dati di Enumerazione nella tabella SQL Server o SQL Azure, se non è presente nella tabella di MySQL. In caso affermativo, tutte le colonne convertite del tipo di dati di Enumerazione sono accompagnate dal vincolo CHECK, controllare il valore.<br /><br />**Modalità predefinita**: No<br /><br />**Modalità ottimistica**: No<br /><br />**Modalità**: Sì|  
|**Generare i vincoli per le colonne di tipo di SET di dati**|Genera l'errore vincoli per le colonne di tipo di SET di dati nella tabella SQL Server o SQL Azure, se non è presente nella tabella di MySQL. In caso affermativo, tutte le colonne convertite del tipo SET di dati saranno associate con il vincolo CHECK controllare il valore.<br /><br />**Modalità predefinita**: No<br /><br />**Modalità ottimistica**: No<br /><br />**Modalità**: Sì|  
|**Generare i vincoli per le colonne delle colonne di tipo di dati numerico senza segno**|Alle colonne di tipi di dati numerico senza segno, aggiungere il controllo per un valore non negativo.<br /><br />**Modalità predefinita**: No<br /><br />**Modalità ottimistica**: No<br /><br />**Modalità**: Sì|  
|**Generare i vincoli per le colonne di tipo data anno**|Genera l'errore di vincolo per le colonne di tipo data anno nella tabella SQL Server o SQL Azure, se non è presente nella tabella di MySQL. In caso affermativo, tutte convertire colonne di dati di anno sarà associato a tipo con il vincolo CHECK controllare il valore.<br /><br />**Modalità predefinita**: No<br /><br />**Modalità ottimistica**: No<br /><br />**Modalità**: Sì|  
  
### <a name="data-types"></a>Tipi di dati  
  
|||  
|-|-|  
|**Nome**|**Definizione**|  
|**Conversione di tipi di dati di Enumerazione**|Specifica come tipo di dati MySQL ENUM deve essere convertito come convertire in NVARCHAR o Convert in numerico<br /><br />**Modalità predefinita**: convertire in NVARCHAR<br /><br />**Modalità ottimistica**: convertire in NVARCHAR<br /><br />**Modalità**: convertire in NVARCHAR|  
|**Conversione di tipi SET di dati**|Specifica il modo in cui deve essere MySQL Imposta tipo di dati convertito, convertire a NVARCHAR (L) / convertire BINARY(L)<br /><br />**Modalità predefinita**: convertire NVARCHAR(L)<br /><br />**Modalità ottimistica**: convertire NVARCHAR(L)<br /><br />**Modalità**: convertire NVARCHAR(L)|  
  
### <a name="generic"></a>Generico  
  
|||  
|-|-|  
|**Nome**|**Definizione**|  
|**Colonne senza un valore predefinito in istruzioni INSERT e Sostituisci**|In caso affermativo, tutte le istruzioni che fanno riferimento a tabelle utilizzando stored motori diversi da MyISAM e InnoDb devono essere contrassegnate con messaggi di avviso conversione.<br /><br />**Modalità predefinita**: aggiungere all'elenco di colonne<br /><br />**Modalità ottimistica**: aggiungere all'elenco di colonne<br /><br />**Modalità**: aggiungere all'elenco di colonne|  
|**Divisione per Zero genera di conversione**|Specifica se emulare MySQL senza comportamento ERROR_FOR_DIVISION_BY_ZERO o meno.<br /><br />**Modalità predefinita**: errore<br /><br />**Modalità ottimistica**: errore<br /><br />**Modalità**: NULL|  
|**Operatore IN**|Specifica come convertire l'operatore IN MySQL.<br /><br />**Modalità predefinita**: convertire sempre IN<br /><br />**Modalità ottimistica**: convertire sempre IN<br /><br />**Modalità**: espandere se necessario|  
|**Conversione di MySQL (funzione)**|Specifica come convertire le funzioni standard di MySQL.<br /><br />**Modalità predefinita**: ottimistica<br /><br />**Modalità ottimistica**: ottimistica<br /><br />**Modalità**: preciso|  
|**Motori di archiviazione non è supportato**|In caso affermativo, tutte le istruzioni che fanno riferimento a tabelle utilizzando stored motori diversi da MyISAM e InnoDb devono essere contrassegnate con messaggi di avviso conversione.<br /><br />**Modalità predefinita**: No<br /><br />**Modalità ottimistica**: No<br /><br />**Modalità**: Sì|  
|**Eliminare la generazione di colonna ausiliario ROWID**|In caso affermativo, impedisce la creazione della creazione di colonna ausiliario ROWD nelle tabelle di destinazione. Può influire sulla migrazione di alcune strutture.<br /><br />**Modalità predefinita**: No<br /><br />**Modalità ottimistica**: No<br /><br />**Modalità**: No|  
|**Conversione di istruzioni TRUNCATE**|Specifica la modalità di conversione di istruzioni.<br /><br />**Modalità predefinita**: TRUNCATE<br /><br />**Modalità ottimistica**: TRUNCATE<br /><br />**Modalità**: TRUNCATE|  
  
### <a name="misc"></a>Varie  
  
|||  
|-|-|  
|**Nome**|**Definizione**|  
|**Mapping dello Schema predefinito**|Specifica come eseguire il mapping di database MySQL in schemi di SQL Server.<br /><br />**Modalità predefinita**: Database in<br /><br />**Modalità ottimistica**: Database in<br /><br />**Modalità**: Database in|  
  
### <a name="procedures-and-functions"></a>Procedure e funzioni  
  
|||  
|-|-|  
|**Nome**|**Definizione**|  
|**Conversione di funzione predefinita**|Specifica se le funzioni essere per impostazione predefinita verrà convertito alle funzioni di T-SQL o stored procedure.<br /><br />**Modalità predefinita**: convertire (funzione)<br /><br />**Modalità ottimistica**: convertire (funzione)<br /><br />**Modalità**: convertire (funzione)|  
|**Generare SET XACT_ABORT su**|Specifica se SET XACT_ABORT ON deve essere aggiunto all'inizio della procedura convertito o del trigger.<br /><br />**Modalità predefinita**: Sì<br /><br />**Modalità ottimistica**: Sì<br /><br />**Modalità**: Sì|  
|**Generare SET NOCOUNT su**|Specifica se consentire o meno SET NOCOUNT ON deve essere aggiunto all'inizio della procedura convertito o del trigger.<br /><br />**Modalità predefinita**: Sì<br /><br />**Modalità ottimistica**: Sì<br /><br />**Modalità**: Sì|  
  
### <a name="spatial-data-types"></a>Tipi di dati spaziali  
  
|||  
|-|-|  
|**Nome**|**Definizione**|  
|**Predefinito delimitatore {XMAX &#124; XMIN &#124; YMAX &#124; YMIN} per gli indici spaziali**|Definisce il valore predefinito per {XMAX &#124; XMIN &#124; YMAX &#124; Parametro YMIN} del rettangolo utilizzate negli indici spaziali.<br /><br />**Modalità predefinita**<br /><br />XMAX: 100<br /><br />XMIN: 0<br /><br />YMAX: 100<br /><br />YMIN: 0<br /><br />**Modalità ottimistico**<br /><br />XMAX: 100<br /><br />XMIN: 0<br /><br />YMAX: 100<br /><br />YMIN: 0<br /><br />**Modalità completa**<br /><br />XMAX: 100<br /><br />XMIN: 0<br /><br />YMAX: 100<br /><br />YMIN: 0|  
|**Densità della griglia predefinita per gli indici spaziali**|Definisce il valore predefinito per LEVEL_1, LEVEL_2, LEVEL_3 e LEVEL_4 di densità della griglia utilizzate negli indici spaziali.<br /><br />**Modalità predefinita**<br /><br />LEVEL_1: predefinito<br /><br />LEVEL_2: predefinito<br /><br />LEVEL_3: predefinito<br /><br />LEVEL_4: predefinito<br /><br />**Modalità ottimistico**<br /><br />LEVEL_1: predefinito<br /><br />LEVEL_2: predefinito<br /><br />LEVEL_3: predefinito<br /><br />LEVEL_4: predefinito<br /><br />**Modalità completa**<br /><br />LEVEL_1: predefinito<br /><br />LEVEL_2: predefinito<br /><br />LEVEL_3: predefinito<br /><br />LEVEL_4: predefinito|  
  
### <a name="transactions"></a>Transazioni  
  
|||  
|-|-|  
|**Nome**|**Definizione**|  
|**Tabelle non transazionale**|Specifica se tutti i riferimenti alla tabella che non supportano le transazioni devono essere contrassegnati con messaggi di avviso conversione.<br /><br />**Modalità predefinita**: No<br /><br />**Modalità ottimistica**: No<br /><br />**Modalità**: Sì|  
|**Livello di isolamento delle transazioni**|Specifica il livello di isolamento delle transazioni deve essere utilizzato per le nuove transazioni.<br /><br />**Modalità predefinita**: predefinito<br /><br />**Modalità ottimistica**: predefinito<br /><br />**Modalità**: Repeatable read|  
  
### <a name="value-control"></a>Controllo Value  
  
|||  
|-|-|  
|**Nome**|**Definizione**|  
|**Carattere da conversioni numeriche**|Specifica come gestire la conversione implicita ed esplicita dal tipo di dati Character a tipi di dati numerici.<br /><br />**Modalità predefinita**: ottimistica<br /><br />**Modalità ottimistica**: ottimistica<br /><br />**Modalità**: preciso|  
|**Controllare i valori numerici senza segno**|Controllo assegnazione di valori per parametri e variabili numeriche senza segno.<br /><br />**Modalità predefinita**: No<br /><br />**Modalità ottimistica**: No<br /><br />**Modalità**: Sì|  
|**Controllo senza segno di sottrazione**|Modificare i valori negativi inseriti nelle colonne di tabella di tipo di dati senza segno.<br /><br />**Modalità predefinita**: convertire ' come-è '<br /><br />**Modalità ottimistica**: convertire ' come-è '<br /><br />**Modalità**: contrassegnare con un messaggio di avviso|  
|**Conversione da e verso il tipo di dati binari**|Specifica come gestire la conversione implicita ed esplicita dal tipo di dati binari.<br /><br />**Modalità predefinita**: ottimistica<br /><br />**Modalità ottimistica**: ottimistica<br /><br />**Modalità**: preciso|  
|**Tipo di conversione in dati di data/ora**|Specifica come gestire le conversioni implicite ed esplicite per data e ora del tipo di dati.<br /><br />**Modalità predefinita**: formato emulare MySQL<br /><br />**Modalità ottimistica**: formato di utilizzare SQL Server<br /><br />**Modalità**: formato emulare MySQL|  
|**Valori letterali numerici con precisione superiore a 38**|Specifica come convertire i valori letterali numerici con precisione superiore a 38.<br /><br />**Modalità predefinita**: arrotondare se possibile<br /><br />**Modalità ottimistica**: arrotondare se possibile<br /><br />**Modalità**: arrotondare se possibile|  
|**Le colonne NOT NULL zero Data**|Specifica come gestire l'assegnazione per le colonne NOT NULL della data di Zero, Zero-in-date o valori di data/ora non valido.<br /><br />**Modalità predefinita**: GETDATE)<br /><br />**Modalità ottimistica**: GETDATE)<br /><br />**Modalità**: GETDATE)|  
  
## <a name="see-also"></a>Vedere anche  
[Riferimento all'interfaccia utente &#40; MySQLToSQL &#41;](../../ssma/mysql/user-interface-reference-mysqltosql.md)  
  
