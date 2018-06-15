---
title: Definisce il formato di testo (Driver di File di testo) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- text format [ODBC]
- text file driver [ODBC], text format
ms.assetid: 3af46dad-52cc-4d5c-a27e-6315d65a74e6
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4b8d87785ccb63796698e164b36728301d3c35e5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32904876"
---
# <a name="defining-text-format-text-file-driver"></a>Definisce il formato di testo (Driver di File di testo)
Quando viene utilizzato il driver di testo, è possibile utilizzare il **Definisci formato testo** la finestra di dialogo per definire il formato delle colonne in un file selezionato. Questa finestra di dialogo consente di specificare lo schema per ogni tabella di dati. Queste informazioni vengono scritte in un file ini nella directory di origine dati. Per ogni directory di origine dati di testo, viene creato un file di schema. ini separato.  
  
> [!NOTE]  
>  Lo stesso formato di file predefinito si applica a tutte le nuove tabelle di dati di testo. Tutti i file creati dall'istruzione CREATE TABLE ereditano tali stessi valori di formato predefinito, che vengono impostati selezionando i valori di formato di file nel **Definisci formato testo** la finestra di dialogo con \<predefinito > scelto per il **Tabelle** elenco. Il driver di testo non modifica il formato del file di testo in base al formato definito in questa finestra di dialogo, ma restituisce un errore quando utilizza il formato, ad esempio quando si tenta di recuperare dati dal file di testo.  
  
 Le opzioni seguenti sono disponibili nel **Definisci formato testo** la finestra di dialogo:  
  
|Opzione|Informazioni|  
|------------|-----------------|  
|**Aggiungi**|Aggiunge una colonna utilizzando i valori in **tipo di dati**, **nome**, e **larghezza** nella finestra di dialogo, e se applicabile, il separatore della data del valore dal file Schema.ini.|  
|**Caratteri**|**ANSI** oppure **OEM**. OEM specifica un set di caratteri non ANSI. L'impostazione predefinita è OEM se il formato dell'elemento selezionato nel **tabelle** elenco non è stato definito in precedenza da questa finestra di dialogo.|  
|**Nome colonna**|Indica se le colonne della prima riga della tabella selezionata devono essere utilizzati come nomi di colonna. Entrambi **TRUE** o **FALSE**. Per impostazione predefinita FALSE se il formato dell'elemento selezionato nel **tabelle** elenco non è stato definito in precedenza da questa finestra di dialogo.|  
|**Colonne**|Elenca i nomi di colonna per ogni colonna della tabella selezionata. L'ordine delle colonne corrisponde all'ordine delle colonne nella tabella. Questo elenco è abilitato se è selezionato un file di **tabelle** elenco.|  
|**Tipo di dati**|Può essere BIT, BYTE, CHAR, valuta, data, FLOAT, INTEGER, LONGCHAR, SHORT o singolo. Tipi di dati date possono essere nei formati seguenti: "aaaa-mmm-gg", "mm-dd-yy", "mmm-dd-yy", "aaaa-mm-gg" o "gg-mmm-aa". "mm" indica i numeri per i mesi. indica "mmm" lettere per mesi.|  
|**delimitatore**|Specifica il carattere delimitatore personalizzato da utilizzare per separare le colonne. Abilitato quando la **personalizzato delimitato** è selezionato il formato. Il delimitatore può essere solo un carattere di lunghezza e le virgolette doppie (") non può essere utilizzate come il carattere delimitatore. (Non è specificato il delimitatore in formato esadecimale o decimale).|  
|**Formato**|Lunghezza fissa o delimitata. Se delimitati, indica il tipo di delimitatore utilizzato: valori delimitati da virgole (CSV), tabulazione o un carattere speciale (personalizzato). L'impostazione predefinita è **CSV delimitato** se il formato dell'elemento selezionato nel **tabelle** elenco non è stato definito in precedenza da questa finestra di dialogo.<br /><br /> Se **formato** è a lunghezza fissa e **intestazione nome colonna** è TRUE, la prima riga deve essere delimitato da virgole.|  
|**Indovinare**|Genera automaticamente i valori della colonna dati tipo, nome e la larghezza delle colonne della tabella selezionata analizzando il contenuto della tabella in base al **formato** casella di selezione. Abilitato quando il formato della tabella è delimitato. Colonne definiti in precedenza il **colonne** elenco vengono eliminate e sostituite con nuove voci. Se **intestazione nome colonna** non è selezionata, i nomi delle colonne vengono generate automaticamente come "F1", "F2" e così via. Cui non viene visualizzato alcun valore predefinito di **tipo di dati** casella.<br /><br /> Questa funzionalità funziona solo su colonne che sono minori di 64.513 byte.|  
|**Modificare**|Modifica la colonna selezionata utilizzando i valori in **tipo di dati**, **nome**, e **larghezza**.|  
|**Nome**|Visualizza il nome della colonna selezionata. Consente di specificare un nuovo nome di colonna per una colonna esistente o una nuova colonna.<br /><br /> Se **intestazione nome colonna** è TRUE, la colonna nome visualizzato viene ignorato.|  
|**Rimuovi**|Elimina la colonna selezionata.|  
|**Righe da analizzare**|Il numero di righe che il programma di installazione o il driver eseguirà l'analisi quando si impostano le colonne e i tipi di dati basati su dati esistenti.<br /><br /> È possibile immettere un numero compreso tra 1 e 32767 per il numero di righe da analizzare. L'impostazione predefinita 25 se il formato dell'elemento selezionato nel **tabelle** elenco non è stato definito in precedenza da questa finestra di dialogo. (Un numero di fuori del limite verrà restituito un errore).|  
|**Tabelle**|Contiene un elenco di tutti i file nella directory selezionata tramite il **installazione testo** la finestra di dialogo che corrispondono all'elenco delle estensioni specificate.<br /><br /> Quando \<predefinito > è selezionata, e uno dei seguenti è true, i valori degli attributi nella tabella di **tabelle** gruppo vengono scritte nel file Schema.ini (altre voci nel file Schema.ini non interessate):<br /><br /> -Non è ini nella directory specificata.<br />-Il file ini esiste, ma non vi è alcuna sezione nel file Schema.ini per uno dei file di testo (con l'estensione specificata) nella directory.<br />-La sezione file di testo presente in Schema.ini, ma il corpo è vuoto.<br /><br /> Quando \<predefinito > è selezionata, il **colonne** gruppo è disabilitato.|  
|**Larghezza**|La larghezza della colonna può essere modificata per le colonne CHAR o LONGCHAR. La larghezza valore predefinito è 1 se il formato dell'elemento selezionato nel **tabelle** elenco non è stato definito in precedenza da questa finestra di dialogo.<br /><br /> Per altri tipi di dati, la larghezza delle schede è disabilitata e viene visualizzato alcun valore.|
