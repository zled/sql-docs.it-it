---
title: Il File INI (Driver di File di testo) | Documenti Microsoft
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
- schema.ini file [ODBC]
- text file driver [ODBC], schema.ini file
ms.assetid: 0c4625c4-c730-4984-b430-9051b7bc0451
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 604dccbbb139cd72f8952fdd604a55d1d9af11c6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="schemaini-file-text-file-driver"></a>File INI (Driver di File di testo)
Quando viene utilizzato il driver di testo, il formato del file di testo è determinato mediante un file di informazioni dello schema. Il file di informazioni dello schema è sempre denominato Schema.ini e mantenuto sempre nella stessa directory dell'origine dati di testo. Il file di informazioni dello schema fornisce il IISAM con informazioni sul formato generale del file, il nome della colonna e informazioni sul tipo di dati e diverse altre caratteristiche di dati. Un file Schema.ini è sempre necessario per l'accesso ai dati a lunghezza fissa. Quando la tabella di testo contiene DateTime, Currency, o dati Decimal o ogni volta che si desidera maggiore controllo sulla gestione dei dati nella tabella, è necessario utilizzare un file ini.  
  
> [!NOTE]  
>  Il driver ISAM testo otterrà i valori iniziali dal Registro di sistema, non dal file Schema.ini. Lo stesso formato di file predefinito si applica a tutte le nuove tabelle di dati di testo. Tutti i file creati dall'istruzione CREATE TABLE ereditano tali stessi valori di formato predefinito, che vengono impostati selezionando i valori di formato di file nel **Definisci formato testo** la finestra di dialogo con \<predefinito > scelto per il  **Tabelle** elenco. Se i valori del Registro di sistema sono diversi dai valori nel file Schema.ini, i valori del Registro di sistema verranno sovrascritti dai valori dal file Schema.ini.  
  
## <a name="understanding-schemaini-files"></a>Informazioni sui file ini  
 Il file ini forniscono informazioni sullo schema relative i record in un file di testo. Ogni voce ini specifica uno dei cinque caratteristiche della tabella:  
  
-   Il nome del file di testo  
  
-   Il formato di file  
  
-   I nomi di campo, larghezza delle colonne e tipi  
  
-   Il set di caratteri  
  
-   Conversioni di tipi di dati speciali  
  
 Le sezioni seguenti illustrano queste caratteristiche.  
  
## <a name="specifying-the-file-name"></a>Specifica il nome del File  
 La prima voce ini è sempre il nome del file di origine testo racchiuso tra parentesi quadre. L'esempio seguente illustra la voce per il file Sample.txt:  
  
```  
[Sample.txt]  
```  
  
## <a name="specifying-the-file-format"></a>Specifica il formato di File  
 Il **formato** Schema.ini opzione specifica il formato del file di testo. IISAM di testo può leggere il formato automaticamente dal file delimitati da più caratteri. È possibile utilizzare qualsiasi singolo carattere come delimitatore del file eccetto le virgolette doppie ("). Il **formato** impostazione nel file Schema.ini sostituisce l'impostazione del Registro di sistema, da un file. Nella tabella seguente sono elencati i valori validi per il **formato** opzione.  
  
|Identificatore di formato|Formato di tabella|Istruzione formato INI|  
|----------------------|------------------|---------------------------------|  
|**Delimitato da tabulazione**|I campi nel file sono delimitati da tabulazioni.|Formato = TabDelimited|  
|**CSV delimitato**|I campi nel file sono delimitati da virgole (valori delimitati da virgole).|Formato = CSVDelimited|  
|**Custom delimitato**|I campi nel file sono delimitati da qualsiasi carattere che si sceglie di input nella finestra di dialogo. Tutto eccetto le virgolette doppie (") sono consentiti, tra cui vuoto.|Formato = delimitato (*carattere personalizzato*)<br /><br /> oppure<br /><br /> Con alcun delimitatore:<br /><br /> Formato = delimitato da virgole)|  
|**Lunghezza fissa**|I campi nel file sono di lunghezza fissa.|Formato = FixedLength|  
  
## <a name="specifying-the-fields"></a>Specificare i campi  
 È possibile specificare i nomi dei campi in un file di testo delimitata da caratteri in due modi:  
  
-   Includere i nomi dei campi nella prima riga della tabella e impostare **ColNameHeader** a **True.**  
  
-   Specificare ogni colonna in base al numero e definire il tipo di dati e nome di colonna.  
  
 È necessario specificare ogni colonna in base al numero e definire il nome della colonna, tipo di dati e larghezza per i file di lunghezza fissa.  
  
> [!NOTE]  
>  Il **ColNameHeader** impostazione Schema.ini sostituzioni di **FirstRowHasNames** l'impostazione del Registro di sistema, da un file.  
  
 Possono essere determinati anche i tipi di dati dei campi. Utilizzare il **MaxScanRows** opzione per indicare il numero di righe deve essere analizzato per determinare i tipi di colonna. Se si imposta **MaxScanRows** su 0, viene analizzato l'intero file. Il **MaxScanRows** impostazione nel file Schema.ini sostituisce l'impostazione del Registro di sistema, da un file.  
  
 La voce seguente indica che Microsoft Jet deve utilizzare i dati nella prima riga della tabella per determinare i nomi dei campi e deve esaminare l'intero file per determinare i dati di tipi utilizzati:  
  
```  
ColNameHeader=True  
MaxScanRows=0  
```  
  
 La voce successiva definisce i campi in una tabella utilizzando il numero di colonna (**Col * * * n*) opzione, ovvero per i file delimitati da caratteri facoltative e obbligatorie per i file di lunghezza fissa. L'esempio mostra le voci di file Schema.ini per due campi, un campo di testo NumeroCliente 10 caratteri e un campo di testo di 30 caratteri CustomerName:  
  
```  
Col1=CustomerNumber Text Width 10  
Col2=CustomerName Text Width 30  
```  
  
 La sintassi di **Col * * * n* è:  
  
```  
  
n=ColumnNametype [#]  
```  
  
## <a name="remarks"></a>Osservazioni  
 Nella tabella seguente descrive ogni parte del **Col * * * n* voce.  
  
|Parametro|Description|  
|---------------|-----------------|  
|*ColumnName*|Il nome della colonna di testo. Se il nome di colonna contiene spazi, è necessario racchiuderlo tra virgolette doppie.|  
|*type*|Come indicato di seguito sono riportati i tipi di dati:<br /><br /> **Tipi di dati di Microsoft Jet**<br /><br /> bit<br /><br /> Byte<br /><br /> Short<br /><br /> Long<br /><br /> Currency<br /><br /> Single<br /><br /> Double<br /><br /> DateTime<br /><br /> Text<br /><br /> Memo<br /><br /> **Tipi di dati ODBC** Char (come testo)<br /><br /> Float (uguale a Double)<br /><br /> Integer (analogo a breve)<br /><br /> LongChar (analogo a Memo)<br /><br /> Data *formato di data*|  
|**Larghezza**|Il valore letterale stringa `Width`. Indica che il numero seguente indica la larghezza della colonna (facoltativo per i file delimitati da caratteri, richiesto per i file di lunghezza fissa).|  
|*#*|Il valore intero che definisce la larghezza della colonna (obbligatorio se **larghezza** è specificato).|  
  
## <a name="selecting-a-character-set"></a>Selezione di un Set di caratteri  
 È possibile selezionare due set di caratteri: ANSI e OEM. Il **CharacterSet** impostazione nel file Schema.ini sostituisce l'impostazione del Registro di sistema, da un file. L'esempio seguente mostra la voce ini che imposta il set di caratteri da ANSI:  
  
```  
CharacterSet=ANSI  
```  
  
## <a name="specifying-data-type-formats-and-conversions"></a>Specifica i formati di tipo di dati e conversioni  
 Il file ini contiene diverse opzioni che è possibile utilizzare per specificare come i dati vengono convertiti o visualizzati. Nella tabella seguente sono elencati ognuna di queste opzioni.  
  
|Opzione|Description|  
|------------|-----------------|  
|**DateTimeFormat**|Impostare su una stringa di formato che indica le date e ore. Se tutti i campi di data/ora nell'importazione/esportazione vengono gestiti con lo stesso formato, è necessario specificare questa voce. Tutti i formati di Microsoft Jet AM. e. sono supportati. Se viene individuata alcuna stringa di formato, vengono utilizzate le opzioni di immagine e l'ora di data breve il pannello di controllo di Windows.|  
|**DecimalSymbol**|Impostare su qualsiasi singolo carattere utilizzato per separare il valore integer dalla parte frazionaria di un numero.|  
|**NumberDigits**|Indica il numero di cifre decimali nella parte frazionaria di un numero.|  
|**NumberLeadingZeros**|Specifica se un valore decimale minore di 1 e più di – 1 deve contenere zeri iniziali. Questo valore può essere False (senza zeri iniziali) o True.|  
|**CurrencySymbol**|Indica il simbolo di valuta che può essere utilizzato per i valori di valuta nel file di testo. Esempi includono il segno di dollaro ($) e data mining.|  
|**CurrencyPosFormat**|Può essere impostata su uno dei valori seguenti:<br /><br /> -Il simbolo di valuta prefisso senza separazione ($1)<br />-Il simbolo di valuta suffisso senza separazione (1$)<br />-Il simbolo di valuta prefisso con un carattere di separazione ($ 1)<br />-Il simbolo di valuta suffisso con un carattere di separazione (1 $)|  
|**CurrencyDigits**|Specifica il numero di cifre utilizzate per la parte frazionaria di un importo in valuta.|  
|**CurrencyNegFormat**|I possibili valori sono i seguenti:<br /><br /> -   ($1)<br />-   –$1<br />-   $–1<br />-   $1–<br />-   (1$)<br />-   –1$<br />-   1–$<br />-   1$–<br />-   –1 $<br />-   –$ 1<br />-   1 $–<br />-   $ 1–<br />-   $ –1<br />-   1– $<br />-   ($ 1)<br />-   (1 $)<br /><br /> Questo esempio viene illustrato il segno di dollaro, ma è necessario sostituirlo con l'appropriato **CurrencySymbol** valore al programma effettivo.|  
|**CurrencyThousandSymbol**|Indica il simbolo a carattere singolo che può essere utilizzato per separare i valori di valuta nel file di testo da migliaia.|  
|**CurrencyDecimalSymbol**|Impostare su qualsiasi singolo carattere utilizzato per separare l'intero dalla parte frazionaria di un importo in valuta.|  
  
> [!NOTE]  
>  Se si omette una voce, viene utilizzato il valore predefinito nel Pannello di controllo di Windows.
