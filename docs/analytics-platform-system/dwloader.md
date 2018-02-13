---
title: dwloader caricatore della riga di comando per Parallel Data Warehouse
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: 
ms.technology: mpp-data-warehouse
description: "**dwloader** è uno strumento da riga di comando Parallel Data Warehouse (PDW) che esegue il caricamento bulk di righe di tabella in una tabella esistente."
ms.date: 11/04/2016
ms.topic: article
ms.assetid: f79b8354-fca5-41f7-81da-031fc2570a7c
caps.latest.revision: 
ms.openlocfilehash: 4050df3fa69a823ebb36076367c2e8d7344ac1a2
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/13/2018
---
# <a name="dwloader-command-line-loader"></a>dwloader caricatore della riga di comando
**dwloader** è uno strumento da riga di comando Parallel Data Warehouse (PDW) che esegue il caricamento bulk di righe di tabella in una tabella esistente. Durante il caricamento di righe, è possibile aggiungere tutte le righe alla fine della tabella (*modalità append* o *modalità fastappend*), aggiungere nuove righe e aggiornare le righe esistenti (*modalità upsert*), o eliminarli tutti righe prima del caricamento esistente e quindi inserire tutte le righe in una tabella vuota (*ricaricare modalità*).  
  
**Processo di caricamento dei dati**  
  
1.  Preparare i dati di origine.  
  
    Usare i propri processi ETL per creare i dati di origine che si desidera caricare. I dati di origine devono essere formattati affinché corrisponda allo schema della tabella di destinazione. Archiviare i dati di origine in uno o più file di testo e copiare i file di testo nella stessa directory del server durante il caricamento. Per informazioni sul server durante il caricamento, vedere [acquisire e configurare un Server durante il caricamento](acquire-and-configure-loading-server.md)  
  
2.  Preparare le opzioni di caricamento.  
  
    Decidere quali opzioni di caricamento verrà utilizzato. Archiviare le opzioni di caricamento in un file di configurazione. Copiare il file di configurazione in un percorso locale sul server durante il caricamento. Il **dwloader** opzioni di configurazione descritte in questo argomento.  
  
3.  Preparare il caricamento di opzioni relative agli errori.  
  
    Decidere come **dwloader** di gestire le righe che non riescono a caricare. Per eseguire il caricamento, **dwloader** carica innanzitutto i dati in una tabella di gestione temporanea e quindi trasferisce i dati nella tabella di destinazione. Come il caricatore carica i dati in una tabella di gestione temporanea, registra il numero di righe che non riescono a caricare. Ad esempio, le righe che non sono formattate correttamente potrà essere caricata. Le righe vengono copiate in un file di rifiuto. Per impostazione predefinita, il carico interrompe dopo il rifiuto prima a meno che non si specifica una soglia di rifiuto diversi.  
  
4.  Installare **dwloader**.  
  
    Se non è già installato, installare dwloader nel server durante il caricamento. 

<!-- MISSING LINK
    See [Install dwloader Command-Line Loader &#40;SQL Server PDW&#41;](install-dwloader-command-line-loader-sql-server-pdw.md). 
--> 
  
5.  Eseguire **dwloader**.  
  
    Accedere al server di caricamento ed eseguire l'eseguibile **dwloader.exe** con le opzioni della riga di comando appropriate.  
  
6.  Verificare i risultati.  
  
    È possibile controllare l'errore righe di file (specificata con -R) da vedere se tutte le righe non è stato possibile caricare. Se questo file è vuoto, tutte le righe caricato correttamente. **dwloader** è transazionale, pertanto se qualsiasi passaggio ha esito negativo (diversa da righe rifiutate), tutti i passaggi verranno ripristinato lo stato iniziale.  
  
<!-- 
![Topic link icon](media/topic-link.gif "Topic_Link")[Syntax Conventions](syntax-conventions-sql-server-pdw.md)  
-->  


## <a name="syntax"></a>Sintassi  
  
```  
dwloader.exe { -h }  
  
dwloader.exe   
    {  
        { -U login_name  -P password  }  
        | -W  
    }  
    [ -f parameter_file ]  
    [ -S target_appliance ]  
    { -T target_database_name . [ schema ] . table_name }   
    { -i source_data_location } [ <source_data_options> ]  
    { -R load_failure_file_name } [ <load_failure_options> ]  
    [ <loading_options> ]  
}  
  
<source_data_options> ::=  
{  
    [ -fh number_header_rows ]  
    [ < variable_length_column_options > | < fixed_width_column_options > ]  
    [ -D { mdy | myd | ymd | ydm | dmy | dym | custom_date_format } ]  
    [ -dt datetime_format_file ]  
}  
  
<variable_length_column_options> ::=  
{  
    [ -e character_encoding ]  
    -r row_delimiter   
    [ -s string_delimiter ]  
    -t field_delimiter   
}  
  
<fixed_width_column_options> ::=  
{  
    -w fixed_width_config_file   
    [ -e character_encoding ]   
    -r row_delimiter   
}  
  
<load_failure_options> ::=  
{  
    [ -rt { value | percentage } ]  
    [ -rv reject_value ]  
    [ -rs reject_sample_value ]  
}  
  
<loading_options> ::=  
{  
    [ -d staging_database_name ]  
    [ -M { append | fastappend | upsert -K merge_column [ ,...n ] | reload } ]  
    [ -b batchsize ]   
    [ -c ]  
    [ -E ]  
    [ -m ]  
    [ -N ]  
    [ -se ]   
}  
```  
  
## <a name="arguments"></a>Argomenti  
**-h**  
Visualizza le informazioni della Guida semplice sull'utilizzo il caricatore. Guida in linea viene visualizzato solo se nessun altro parametro della riga di comando viene specificato.  
  
**-U** *login_name*  
Un accesso di autenticazione di SQL Server valido con le autorizzazioni appropriate per eseguire il caricamento.  
  
**-P** *password*  
La password per l'autenticazione di SQL Server *login_name*.  
  
**-W**  
Utilizza l'autenticazione di Windows. (No *login_name* o *password* obbligatorio.) 

<!-- MISSING LINK
For information about configuring Windows Authentication, see [Security - Configure Domain Trusts](security-configure-domain-trusts.md).  
-->
  
**-f** *parameter_file_name*  
Utilizzare un file di parametro, *parameter_file_name*, al posto di parametri della riga di comando. *parameter_file_name* può contenere tutti i parametri della riga di comando tranne *nome_utente* e *password*. Se viene specificato un parametro della riga di comando e nel file di parametri, la riga di comando sostituisce il parametro file.  
  
Il file dei parametri contiene un parametro, senza il  **-**  prefisso, per ogni riga.  
  
Esempi:  
  
`rt=percentage`  
  
`rv=25`  
  
**-S***target_appliance*  
Specifica il dispositivo di SQL Server PDW che riceverà i dati caricati.  
  
*Per le connessioni Infiniband*, *target_appliance* è specificato come < nome dispositivo >-SQLCTL01. Per configurare questa impostazione è denominata connessione, vedere [configurare schede di rete InfiniBand](configure-infiniband-network-adapters.md).  
  
Per le connessioni Ethernet, *target_appliance* è l'indirizzo IP per il cluster di nodi di controllo.  
  
Se omesso, viene impostata sul valore specificato durante l'installazione di dwloader dwloader. 

<!-- MISSING LINK
For more information about this install option, see [Install dwloader Command-Line Loader](install-dwloader.md).  
-->
  
**-T** *target_database_name.*[*schema*].*table_name*  
Il nome in tre parti per la tabella di destinazione.  
  
**-I***source_data_location*  
Il percorso di uno o più file di origine da caricare. Ogni file di origine deve essere un file di testo o un file di testo compresso con gzip. Solo un file di origine può essere compresse in ogni file gzip.  
  
Per formattare un file di origine:  
  
-   Il file di origine deve essere formattato in base alle opzioni di caricamento.  
  
-   Ogni riga in un file di origine contiene i dati per una riga di tabella. I dati di origine devono corrispondere allo schema della tabella di destinazione. Devono corrispondere anche i tipi di dati e ordine di colonna. Ogni campo nella riga rappresenta una colonna nella tabella di destinazione.  
  
-   Per impostazione predefinita, i campi sono di lunghezza variabile e separati da un delimitatore. Per specificare il tipo di delimitatore, utilizzare le opzioni della riga di comando < variable_length_column_options >. Per specificare i campi a lunghezza fissa, usare le opzioni della riga di comando < fixed_width_column_options >.  
  
Per specificare il percorso di origine dati:  
  
-   Il percorso di origine dati può essere un percorso di rete o un percorso locale in una directory nel server durante il caricamento.  
  
-   Per specificare tutti i file in una directory, immettere il percorso della directory aggiungendo il * carattere jolly.  Il caricatore non carica i file da qualsiasi sottodirectory che si trovano nel percorso dei dati di origine... Gli errori di caricamento quando esiste una directory in un file gzip.  
  
-   Per specificare alcuni dei file in una directory, utilizzare una combinazione di caratteri e il * con caratteri jolly.  
  
Per caricare più file con un unico comando:  
  
-   Tutti i file devono trovarsi nella stessa directory.  
  
-   I file devono essere tutti i file di testo, tutti i file gzip o una combinazione di file di testo e gzip.  
  
-   Nessuno dei file possono contenere informazioni di intestazione.  
  
-   Tutti i file è necessario utilizzare lo stesso tipo di codifica di carattere. Vedere l'opzione-e.  
  
-   Tutti i file devono essere caricati nella stessa tabella.  
  
-   Tutti i file verranno concatenati e caricati come se si tratta di un file e le righe rifiutate verranno inviata a un file singolo rifiuto.  
  
Esempi:  
  
-   -i \\\loadserver\loads\daily\\*.gz  
  
-   -i \\\loadserver\loads\daily\\*.txt  
  
-   -i \\\loadserver\loads\daily\monday.*  
  
-   -i \\\loadserver\loads\daily\monday.txt  
  
-   -i \\\loadserver\loads\daily\\*  
  
**-R** *load_failure_file_name*  
Se sono presenti errori di caricamento, **dwloader** archivia la riga che non è riuscita per il caricamento e la descrizione dell'errore, le informazioni di errore in un file denominato *load_failure_file_name*. Se il file esiste già, dwloader sovrascriverà il file esistente. *load_failure_file_name* viene creato quando si verifica il primo errore. Se tutte le righe caricate correttamente, *load_failure_file_name* non è stato creato.  
  
**-fh** *number_header_rows*  
Il numero di righe da ignorare all'inizio di *source_data_file_name*. Il valore predefinito è 0.  
  
<variable_length_column_options>  
Le opzioni per un *source_data_file_name* che è delimitata da caratteri di colonne a lunghezza variabile. Per impostazione predefinita, *source_data_file_name* contiene caratteri ASCII nelle colonne a lunghezza variabile.  
  
Per i file ASCII, i valori null sono rappresentato posizionando consecutivamente delimitatori. Ad esempio, in un file delimitati da pipe ("|"), un valore NULL è indicato da "| |". In un file delimitato da virgole, un valore NULL è indicato da ",". Inoltre, il **-E** (-emptyStringAsNull) deve essere specificata l'opzione. Per ulteriori informazioni su -E, vedere di seguito.  
  
**-e** *character_encoding*  
Specifica un tipo di codifica dei caratteri per i dati da caricare dal file di dati. Le opzioni sono ASCII (impostazione predefinita), UTF8, UTF16 o UTF16BE, dove è little-endian UTF16 e UTF16BE è big endian. Queste opzioni sono la distinzione tra maiuscole e minuscole.  
  
**-t** *field_delimiter*  
Il delimitatore per ogni campo (colonna) della riga. Il delimitatore di campo è di uno o più di questi caratteri di escape ASCII o valori esadecimali ASCII...  
  
|Nome|Carattere escape|Caratteri esadecimali|  
|--------|--------------------|-----------------|  
|Scheda|\t|0x09|  
|Ritorno a capo (CR)|\r|0x0d|  
|Avanzamento riga (LF)|\n|0x0a|  
|CRLF|\r\n|0x0d0x0a|  
|Virgola|','|0x2c|  
|Virgoletta doppia|\\"|0x22|  
|Virgoletta singola|\\'|0x27|  
  
Per specificare il carattere barra verticale nella riga di comando, racchiuderlo tra virgolette doppie, "|". Questo modo si evita errata interpretazione dal parser della riga di comando. Altri caratteri sono racchiusi tra virgolette.  
  
Esempi:  
  
-t "|"  
  
-t ' '  
  
-t 0x0a  
  
-t \t  
  
-t '~|~'  
  
**-r** *row_delimiter*  
Il delimitatore per ogni riga del file di dati di origine. Il delimitatore di riga è uno o più valori ASCII.  
  
Per specificare un ritorno a capo (CR), un avanzamento riga (LF) o un carattere di tabulazione come delimitatore, è possibile utilizzare i caratteri di escape (\r, \n, \t) o i relativi valori esadecimali (0 x, 0D, 09). Per specificare altri caratteri speciali come delimitatori, utilizzare il valore esadecimale.  
  
Esempi di CR LF +:  
  
-r \r\n  
  
-r 0x0d0x0a  
  
Esempi di CR:  
  
-r \r  
  
-r 0x0d  
  
Esempi di nuova riga:  
  
-r \n  
  
-r 0x0a  
  
Un avanzamento riga è necessaria per Unix. Un CR è necessario per Windows.  
  
**-s** *string_delimiter*  
Il delimitatore per i dati stringa tipo di campo di un file di input di testo delimitato. Il delimitatore di stringa è uno o più valori ASCII.  Può essere specificato come un carattere (ad esempio, -s *) o come valore esadecimale (ad esempio, -s 0x22 per le virgolette).  
  
Esempi:  
  
-s *  
  
-s 0x22  
  
< fixed_width_column_options >  
Le opzioni per un file di dati di origine con colonne a lunghezza fissa. Per impostazione predefinita, *source_data_file_name* contiene caratteri ASCII nelle colonne a lunghezza variabile.  
  
Le colonne a larghezza fissa non sono supportate quando-e è UTF8.  
  
**-w** *fixed_width_config_file*  
Percorso e nome del file di configurazione che specifica il numero di caratteri in ogni colonna. Ogni campo deve essere specificato.  
  
Il file deve trovarsi nel server durante il caricamento. Il percorso può essere un percorso UNC, di relativo o assoluto. Ogni riga in *fixed_width_config_file* contiene il nome di una colonna e il numero di caratteri per la colonna. È una riga per ogni colonna, come indicato di seguito, e l'ordine nel file deve corrispondere all'ordine nella tabella di destinazione:  
  
*column_name*=*num_chars*  
  
*column_name*=*num_chars*  
  
File di configurazione a larghezza fissato di esempio:  
  
SalesCode=3  
  
SalesID=10  
  
Righe di esempio *source_data_file_name*:  
  
230Shirts0056  
  
320Towels1356  
  
Nell'esempio precedente, la prima riga caricata avrà SalesCode = '230' e SalesID = 'Shirts0056'. La riga caricata in secondo luogo sarà necessario SalesCode = '320' e SaleID = 'Towels1356'.  
  
Per informazioni su come gestire iniziali e finali di conversione di tipo spazi o i dati in modalità a larghezza fissa, vedere [per dwloader le regole di conversione del tipo di dati](dwloader-data-type-conversion-rules.md).  
  
**-e** *character_encoding*  
Specifica un tipo di codifica dei caratteri per i dati da caricare dal file di dati. Le opzioni sono ASCII (impostazione predefinita), UTF8, UTF16 o UTF16BE, dove è little-endian UTF16 e UTF16BE è big endian. Queste opzioni sono la distinzione tra maiuscole e minuscole.  
  
Le colonne a larghezza fissa non sono supportate quando-e è UTF8.  
  
**-r** *row_delimiter*  
Il delimitatore per ogni riga del file di dati di origine. Il delimitatore di riga è uno o più valori ASCII.  
  
Per specificare un ritorno a capo (CR), un avanzamento riga (LF) o un carattere di tabulazione come delimitatore, è possibile utilizzare i caratteri di escape (\r, \n, \t) o i relativi valori esadecimali (0 x, 0D, 09). Per specificare altri caratteri speciali come delimitatori, utilizzare il valore esadecimale.  
  
Esempi di CR LF +:  
  
-r \r\n  
  
-r 0x0d0x0a  
  
Esempi di CR:  
  
-r \r  
  
-r 0x0d  
  
Esempi di nuova riga:  
  
-r \n  
  
-r 0x0a  
  
Un avanzamento riga è necessaria per Unix. Un CR è necessario per Windows.  
  
**-D** { **AMG** | agm | mdy | myd |  DMY | dym | *custom_date_format* }  
Specifica l'ordine di mese (m), (d) giorno e anno (y) per tutti i campi datetime nel file di input. L'ordine predefinito è AMG. Per specificare più formati di ordine per lo stesso file di origine, utilizzare l'opzione-dt.  
  
ymd | dmy  
agm e dmy consentono gli stessi formati di input. Entrambi consentono l'anno essere all'inizio o alla fine della data. Ad esempio, per entrambi **agm** e **dmy** , formati di data potrebbe aver 2013-02-03 o 02-03-2013 nel file di input.  
  
ydm  
È possibile caricare solo input formattate come agm in colonne di tipo di dati datetime e smalldatetime. Non è possibile caricare agm valori in una colonna di tipo di dati datetimeoffset, datetime2 o Data.  
  
mdy  
Consente di mdy <month> <space> <day> <comma> <year>.  
  
Esempi di dati di input per il 1 ° gennaio 1975 mdy:  
  
-   1 ° gennaio 1975.  
  
-   01 gen 75  
  
-   Jan/1/75  
  
-   01011975  
  
myd  
Esempi di file di input per marzo 04,2010: 2010-04-03, 2010/3/4  
  
dym  
Esempi di file di input per 04 marzo 2010: 2010-04-03, 2010/4/3  
  
*custom_date_format*  
*custom_date_format* è un formato di data personalizzato (ad esempio, MM/GG/AAAA) e incluso solo per la compatibilità. dwloader non non enfoce il formato della data personalizzato. Al contrario, quando si specifica un formato di date personalizzato, **dwloader** verrà convertito l'impostazione di ymd, ydm, mdy, ydm, dym o dmy corrispondente.  
  
Ad esempio, se si specifica – D MM/GG/AAAA, dwloader prevede tutti di input devono essere ordinati in primo luogo, con mese e giorno e quindi anno (mdy). Non applica 2 caratteri mesi, giorni cifra 2 e 4 cifre come specificato dal formato di date personalizzato. Di seguito sono riportati alcuni esempi dei modi le date possono essere formattate nel file di input quando il formato data è – D MM/GG/AAAA: 01/02/2013, Jan.02.2013, 1/2/2013  
  
Per informazioni di formattazione più complete, vedere [per dwloader le regole di conversione del tipo di dati](dwloader-data-type-conversion-rules.md).  
  
**-dt** *datetime_format_file*  
Ogni formato di datetime è specificato in un file denominato *datetime_format_file*. A differenza dei parametri della riga di comando, parametri del file che includono spazi non devono essere racchiusi tra virgolette doppie. È possibile modificare il formato di data/ora quando si caricano dati. Il file di dati di origine e di colonna corrispondente nella tabella di destinazione devono avere lo stesso formato.  
  
Ogni riga contiene il nome di una colonna nella tabella di destinazione e il formato di datetime.  
  
Esempi:  
  
`LastReceiptDate=ymd`  
  
`ModifiedDate=dym`  
  
**-d** *staging_database_name*  
Il nome del database che conterrà la tabella di gestione temporanea. Il valore predefinito è il database specificato con l'opzione -T, ovvero il database per la tabella di destinazione. Per ulteriori informazioni sull'utilizzo di un database di gestione temporanea, vedere [creare il Database di gestione temporanea](staging-database.md).  
  
**-M** *load_mode_option*  
Specifica se accodare, upsert, o ricaricare i dati. Viene aggiunta la modalità predefinita.  
  
Aggiungere  
Il caricatore inserisce righe alla fine delle righe esistenti nella tabella di destinazione.  
  
fastappend  
Il caricatore inserisce righe direttamente, senza utilizzare una tabella temporanea, alla fine delle righe esistenti nella tabella di destinazione. fastappend richiede la multi-transazione (-m) opzione. Quando si utilizza fastappend, non è possibile specificare un database di gestione temporanea. Viene eseguito alcun rollback con fastappend, il che significa che il ripristino da un carico interrotto o non deve essere gestito dal proprio processo di caricamento.  
  
Upsert **-K***merge_column* [,... *n* ]  
Il caricatore Usa l'istruzione Merge SQL Server per aggiornare le righe esistenti e inserire nuove righe.  
  
L'opzione -K specifica le colonne su cui basare il merge. Queste colonne formano una chiave di tipo merge, che deve rappresentare una riga univoca. Se la chiave di tipo merge esiste nella tabella di destinazione, la riga viene aggiornata. Se la chiave di tipo merge non esiste nella tabella di destinazione, la riga viene aggiunto.  
  
Per le tabelle hash distribuita, la chiave di tipo merge deve essere o includere la colonna di distribuzione.  
  
Per le tabelle replicate, la chiave di tipo merge è la combinazione di uno o più colonne. Queste colonne vengono specificate in base alle esigenze dell'applicazione.  
  
Più colonne devono essere delimitato da virgole senza spazi, o delimitato da virgole con spazi e racchiuso tra virgolette singole.  
  
Se due righe nella tabella di origine hanno valori di chiave di tipo merge corrispondenti, le rispettive righe devono essere identiche.  
  
Ricarica  
Il caricatore tronca la tabella di destinazione prima di inserire i dati di origine.  
  
**-b** *batchsize*  
Consigliato solo per l'utilizzo in base al supporto Microsoft, *batchsize* è la dimensione di batch SQL Server per la copia di massa DMS esegue istanze di SQL Server nei nodi di calcolo.  Quando *batchsize* viene specificato, SQL Server PDW sostituiranno le dimensioni di caricamento batch che viene calcolata in modo dinamico per ogni carico.  
  
A partire da SQL Server 2012 PDW, il nodo controllo calcola dinamicamente una dimensione di batch per ogni carico per impostazione predefinita. Il calcolo automatico si basa su diversi parametri, ad esempio la dimensione della memoria, il tipo di tabella di destinazione, dello schema di tabella di destinazione, il tipo di carico, dimensioni del file e la classe di risorse dell'utente.  
  
Ad esempio, se la modalità di caricamento è FASTAPPEND e la tabella include un indice columnstore cluster, SQL Server PDW verrà tentativo predefinito da utilizzare una dimensione di batch pari a 1.048.576, in modo che i gruppi di righe verrà chiuso e carico direttamente nel columnstore senza passare attraverso il archivio delta. Se le dimensioni del batch pari a 1.048.576 non consente la memoria, dwloader sceglierà una batchsize più piccola.  
  
Se il tipo di caricamento FASTAPPEND, il *batchsize* si applica al caricamento di dati nella tabella, in caso contrario *batchsize* si applica al caricamento di dati nella tabella di gestione temporanea.  
  
<reject_options>  
Specifica le opzioni per determinare il numero di errori di caricamento che consentirà il caricatore. Se gli errori di caricamento superano la soglia, il caricatore verrà interrotta e non eseguire il commit di tutte le righe.  
  
**-rt** { **valore** | percentuale}  
Specifica se il parametro -*reject_value* nel **-rv** *reject_value* è un numero di righe (valore) del valore letterale o una percentuale di errori (percentuale). Il valore predefinito è.  
  
L'opzione di percentuale è un calcolo in tempo reale che si verifica a intervalli in base all'opzione - r.  
  
Ad esempio, se i tentativi di caricamento per caricare 100 righe e 25 non riescono e 75 esito positivo, il numero di errori è 25%.  
  
**-rv** *reject_value*  
Specifica il numero o la percentuale di rifiuti di riga consentiti prima di interrompere il carico. Il **-rt** opzione determina se *reject_value* si intende il numero di righe o la percentuale di righe.  
  
Il valore predefinito *reject_value* è 0.  
  
Se utilizzato con il valore di -rt, il caricatore Arresta il carico quando il conteggio delle righe rifiutate supera reject_value.  
  
Quando utilizzare con la percentuale -rt, il caricatore calcola la percentuale a intervalli (-opzione rs). Pertanto, in cui può superare la percentuale di righe con errori *reject_value*.  
  
**rs -** *reject_sample_size*  
Utilizzato con il `-rt percentage` opzione per specificare i controlli di percentuale incrementale. Ad esempio, se reject_sample_size è 1000, il caricatore verrà calcolata la percentuale di righe con errori dopo che ha tentato di caricare 1000 righe. La percentuale di righe con errori vengono ricalcolati dopo tenta di caricare ogni 1000 righe di aggiuntive.  
  
**-c**  
Rimuove gli spazi vuoti da sinistra a destra di char, nchar, varchar e nvarchar campi. Converte ogni campo che contiene solo spazi vuoti a una stringa vuota.  
  
Esempi:  
  
' ' viene troncato a '  
  
'abc' viene troncato a 'abc'  
  
Quando – c viene utilizzato con -E, l'operazione, E si verifica per primo. I campi che contengono solo spazi vuoti vengono convertiti in una stringa vuota e non su NULL.  
  
**-E**  
Convertire le stringhe vuote in NULL. Il valore predefinito è per non eseguire queste conversioni.  
  
**-m**  
Utilizzare la modalità multi-transaction per la seconda fase di caricamento; Quando si caricano i dati dalla tabella di gestione temporanea in una tabella distribuita.  
  
Con **– m**, SQL Server PDW esegue ed esegue il commit carichi in parallelo. Vengono eseguite più velocemente rispetto alle modalità di caricamento predefinito, ma non è sicuro per transazione.  
  
Senza **– m**, SQL Server PDW esegue ed esegue il commit carica in modo seriale tra le distribuzioni all'interno di ogni nodo di calcolo e, contemporaneamente, tra i nodi di calcolo. Questo metodo è più lento rispetto alla transazione a più modalità, ma transazione-safe.  
  
**-m** è facoltativo per *aggiungere*, *ricaricare*, e *upsert*.  
  
**-m** per fastappend è necessario.  
  
**-m** non può essere utilizzato con le tabelle replicate.  
  
**-m** si applica solo alla seconda fase di caricamento. Non è valido per la prima fase di caricamento; il caricamento dei dati nella tabella di gestione temporanea.  
  
Viene eseguito alcun rollback con la modalità multi-transazione, il che significa che il ripristino da un carico interrotto o non deve essere gestito dal proprio processo di caricamento.  
  
Si consiglia di utilizzare **– m** solo durante il caricamento in una tabella vuota, in modo da poter ripristinare senza perdita di dati. Per recuperare da un errore di carico: eliminare la tabella di destinazione, risolvere il problema di caricamento, ricreare la tabella di destinazione e rieseguire il carico.  
  
**-N**  
Verificare che il dispositivo di destinazione disponga di un certificato di SQL Server PDW valido da un'autorità attendibile. Utilizzare questa opzione per garantire i dati non è soggetta a Hijack da un utente malintenzionato e inviato a un percorso non autorizzato. Il certificato deve essere già installato nel dispositivo. L'unico metodo supportato per installare il certificato è per l'amministratore del dispositivo di installarlo utilizzando lo strumento Gestione configurazione. Chiedere all'amministratore del dispositivo se non si è certi che il dispositivo è installato un certificato attendibile.  
  
**-se**  
Ignora il caricamento di file vuoti. Anche questo ignora la decompressione di file vuoto gzip.  
  
## <a name="return-code-values"></a>Valori restituiti  
0 (esito positivo) o un altro valore intero (errore)  
  
In un file di comando finestra o un batch, utilizzare `errorlevel` per visualizzare il codice restituito. Esempio:  
  
```  
dwloader  
echo ReturnCode=%errorlevel%  
if not %errorlevel%==0 echo Fail  
if %errorlevel%==0 echo Success  
```  
  
Quando si usa PowerShell, usare `$LastExitCode`.  
  
## <a name="permissions"></a>Autorizzazioni  
Richiede l'autorizzazione di carico e le autorizzazioni applicabili (INSERT, UPDATE, DELETE) nella tabella di destinazione. Richiede l'autorizzazione di creazione (per la creazione di una tabella temporanea) nel database di gestione temporanea. Se non viene utilizzato un database di gestione temporanea, l'autorizzazione CREATE è necessario nel database di destinazione. 

<!-- MISSING LINK
For more information, see [Grant permissions to load data](grant-permissions-to-load-data.md).  
-->
  
## <a name="general-remarks"></a>Osservazioni generali  
Per informazioni sulle conversioni dei tipi di dati durante il caricamento con dwloader, vedere [per dwloader le regole di conversione del tipo di dati](dwloader-data-type-conversion-rules.md).  
  
Se un parametro include uno o più spazi, racchiuderlo tra virgolette doppie.  
  
È consigliabile eseguire il caricatore dal relativo percorso di installazione. L'eseguibile dwloader pre-installato con il dispositivo e si trova nella directory C:\Program Files\Microsoft SQL Server Data Warehouse\DWLoader.  
  
È possibile eseguire l'override di un parametro che viene specificato nel file di parametro (-opzione f) specificandolo come un parametro della riga di comando.  
  
È possibile eseguire contemporaneamente più istanze del caricatore. Il numero massimo di istanze del caricatore è preconfigurato e non può essere modificato. 

<!-- MISSING LINK
For the maximum number of loads per appliance, see [Minimum and Maximum Values](minimum-maximum-values.md)  
-->
  
Dati caricati potrebbero richiedere più o meno spazio nel dispositivo nel percorso di origine. È possibile eseguire test importazioni di subset di dati per stimare l'utilizzo del disco.  
  
Sebbene **dwloader** è un processo di transazione e riporterà normalmente in caso di errore, ma non può essere implementata nuovamente una volta completato il caricamento bulk è stato completato correttamente. Per annullare un oggetto attivo **dwloader** elaborare, premere CTRL + C.  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
Le dimensioni totali di tutti i carichi che si verificano contemporaneamente deve essere minore di LOG_SIZE per il database, si consiglia la dimensione totale di tutti i caricamenti simultanei sono inferiore al 50% del LOG_SIZE. Per ottenere questa limitazione delle dimensioni, è possibile suddividere i grandi carichi in più batch. Per ulteriori informazioni su LOG_SIZE, vedere [CREATE DATABASE](../t-sql/statements/create-database-parallel-data-warehouse.md)  
  
Quando si caricano più file con il comando di caricamento di uno, tutte le righe rifiutate vengono scritti nello stesso file di rifiuto. Il file di rifiuto non viene visualizzato il file di input contiene ogni riga rifiutato.  
  
Una stringa vuota non deve essere utilizzata come delimitatore. Quando una stringa vuota viene utilizzata come un delimitatore di riga, il caricamento avrà esito negativo. Se utilizzato come delimitatore di colonna, il carico ignora il delimitatore e continua a utilizzare il valore predefinito "|" come delimitatore di colonna. Quando viene utilizzato come delimitatore di stringa, una stringa vuota viene ignorata e viene applicato il comportamento predefinito.  
  
## <a name="locking-behavior"></a>Comportamento di blocco  
**dwloader** il comportamento di blocco varia a seconda di *load_mode_option*.  
  
-   **aggiungere** – accodamento è consigliata e l'opzione più comune. Aggiungere il caricamento dei dati in una tabella di gestione temporanea. Il blocco viene descritto dettagliatamente di seguito.  
  
-   **aggiungere Fast** – aggiungere Fast carica direttamente nella tabella finale l'acquisizione di un blocco di tabella ExclusiveUpdate ed è l'unica modalità che non utilizza una tabella di gestione temporanea.  
  
-   **ricaricare** – Ricarica carica i dati in una tabella di gestione temporanea e richiede un blocco esclusivo sulla tabella di gestione temporanea e la tabella finale. Caricamento non è consigliata per operazioni simultanee.  
  
-   **Upsert** – Upsert carica i dati in una tabella di gestione temporanea e quindi esegue un'operazione di unione dalla tabella di gestione temporanea per la tabella finale. Upsert non richiede un blocco esclusivo sulla tabella finale. Quando si utilizza upsert, le prestazioni possono variare. Testare il comportamento nell'ambiente in uso.  
  
### <a name="locking-behavior"></a>Comportamento di blocco  
**Un blocco in modalità append**  
  
Aggiungere può essere eseguito in modalità multi-transazionale (tramite l'argomento – m), ma non è sicura delle transazioni. Pertanto aggiungere deve essere utilizzato come un'operazione transazionale (senza utilizzare l'argomento – m). Sfortunatamente, durante l'operazione INSERT SELECT finale, è attualmente circa sei volte più lenta rispetto alla modalità transazionale più modalità transazionale.  
  
La modalità append carica i dati in due fasi. La fase uno carica i dati dal file di origine in una tabella di gestione temporanea contemporaneamente (di frammentazione). La fase due carica i dati dalla tabella di gestione temporanea per la tabella finale. La seconda fase esegue un **INSERT INTO... Selezionare WITH (TABLOCK)** operazione. Nella tabella seguente viene illustrato il comportamento di blocco per la tabella finale e il comportamento di registrazione quando si utilizza modalità di aggiunta:  
  
|Tipo di tabella|Più transazioni<br />Modalità (-m)|La tabella è vuota|Concorrenza supportata|Registrazione|  
|--------------|-----------------------------------|------------------|-------------------------|-----------|  
|Heap|Sì|Sì|Sì|minimo|  
|Heap|Sì|No|Sì|minimo|  
|Heap|no|Sì|no|minimo|  
|Heap|no|No|no|minimo|  
|Cl|Sì|Sì|no|minimo|  
|Cl|Sì|No|Sì|Completo|  
|Cl|no|Sì|no|minimo|  
|Cl|no|No|Sì|Completo|  
  
Illustrato nella tabella precedente **dwloader** usando la modalità append, il caricamento in un heap o di una tabella di un indice cluster (CI), con o senza il flag di multi-transazionale e il caricamento in una tabella vuota o una tabella non vuota. Il blocco e la registrazione di comportamento di ogni tale combinazione di carico viene visualizzato nella tabella. Ad esempio, il caricamento di fase (2) con la modalità append in un indice cluster senza la modalità multi-transazionale e in un oggetto vuoto tabella sarà PDW creare un blocco esclusivo sulla tabella e la registrazione è minima. Ciò significa che un cliente non sarà in grado di caricare simultaneamente (2) fase e query in una tabella vuota. Tuttavia, quando si caricano con la stessa configurazione in una tabella non vuota, PDW non emetterà un blocco esclusivo sulla tabella e la concorrenza è possibile. Sfortunatamente, si verifica la registrazione completa, rallentare il processo.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-simple-dwloader-example"></a>A. Esempio semplice dwloader  
L'esempio seguente illustra l'avvio del **caricatore** con solo le opzioni necessarie selezionate. Altre opzioni vengono estratti dal file di configurazione globale, *loadparamfile.txt*.  
  
Esempio utilizza l'autenticazione di SQL Server.  
  
```  
--Load over Ethernet  
dwloader.exe -S 10.192.63.148 -U mylogin -P 123jkl -f /configfiles/loadparamfile.txt  
  
--Load over InfiniBand to appliance named MyPDW  
dwloader.exe -S MyPDW-SQLCTL01 -U mylogin -P 123jkl -f /configfiles/loadparamfile.txt  
```  
  
Lo stesso esempio con l'autenticazione di Windows.  
  
```  
--Load over Ethernet  
dwloader.exe -S 10.192.63.148 -W -f /configfiles/loadparamfile.txt  
  
--Load over InfiniBand to appliance named MyPDW  
dwloader.exe -S MyPDW-SQLCTL01 -W -f /configfiles/loadparamfile.txt  
```  
  
Esempio di utilizzo di argomenti per un file di origine e file degli errori.  
  
```  
--Load over Ethernet  
dwloader.exe -U mylogin -P 123jkl -S 10.192.63.148  -i C:\SQLData\AWDimEmployees.csv -T AdventureWorksPDW2012.dbo.DimEmployees -R C:\SQLData\LoadErrors  
```  
  
### <a name="b-load-data-into-an-adventureworks-table"></a>B. Caricare i dati in una tabella di AdventureWorks  
Nell'esempio seguente fa parte di uno script batch che carica i dati in **AdventureWorksPDW2012**.  Per visualizzare lo script completo, aprire il file aw_create.bat fornito con il **AdventureWorksPDW2012** pacchetto di installazione. 

<!-- Missing link
For more information, see [Install AdventureWorksPDW2012](install-adventureworkspdw2012.md).  
-->

Il seguente frammento di script utilizza dwloader per caricare i dati nelle tabelle DimAccount e DimCurrency. Questo script utilizza un indirizzo Ethernet. Se è stata utilizzando InfiniBand, server sarebbe *< appliance_name >*`-SQLCTL01`.  
  
```  
set server=10.193.63.134  
set user=<MyUser>  
set password=<MyPassword>  
  
set schema=AdventureWorksPDW2012.dbo  
set load="C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\dwloader.exe"  
set mode=reload  
  
--Loads data into the AdventureWorksPDW2012.dbo.DimAccount table  
--Source data is stored in the file DimAccount.txt,   
--which is in the current directory.  
  
set t1=DimAccount  
%load% -S %server% -E -M %mode% -e Utf16 -i .\%t1%.txt -T %schema%.%t1% -R %t1%.bad -t "|" -r \r\n -U %user% -P %password%   
  
--Loads data from the DimCurrency.txt file into  
--AdventureWorksPDW2012.dbo.DimCurrency  
set t1=DimCurrency  
%load% -S %server% -E -M %mode% -e Utf16 -i .\%t1%.txt -T %schema%.%t1% -R %t1%.bad -t "|" -r \r\n -U %user% -P %password%  
```  
  
Di seguito è riportato il DDL per la tabella DimAccount.  
  
```  
CREATE TABLE DimAccount(  
AccountKey int NOT NULL,  
ParentAccountKey int,  
AccountCodeAlternateKey int,  
ParentAccountCodeAlternateKey int,  
AccountDescription nvarchar(50),  
AccountType nvarchar(50),  
Operator nvarchar(50),  
CustomMembers nvarchar(300),  
ValueType nvarchar(50),  
CustomMemberOptions nvarchar(200))  
with (CLUSTERED INDEX(AccountKey),  
DISTRIBUTION = REPLICATE);  
```  
  
Di seguito è riportato un esempio del file di dati, DimAccount.txt, che contiene i dati da caricare nella tabella DimAccount.  
  
```  
--Sample of data in the DimAccount.txt load file.  
  
1||1||Balance Sheet||~||Currency|  
2|1|10|1|Assets|Assets|+||Currency|  
3|2|110|10|Current Assets|Assets|+||Currency|  
4|3|1110|110|Cash|Assets|+||Currency|  
5|3|1120|110|Receivables|Assets|+||Currency|  
6|5|1130|1120|Trade Receivables|Assets|+||Currency|  
7|5|1140|1120|Other Receivables|Assets|+||Currency|  
8|3|1150|110|Allowance for Bad Debt|Assets|+||Currency|  
9|3|1160|110|Inventory|Assets|+||Currency|  
10|9|1162|1160|Raw Materials|Assets|+||Currency|  
11|9|1164|1160|Work in Process|Assets|+||Currency|  
12|9|1166|1160|Finished Goods|Assets|+||Currency|  
13|3|1170|110|Deferred Taxes|Assets|+||Currency|  
```  
  
### <a name="c-load-data-from-the-command-line"></a>C. Caricare i dati dalla riga di comando  
Lo script dell'esempio B può essere sostituito tramite l'immissione di tutti i parametri della riga di comando, come illustrato nell'esempio seguente.  
  
```  
C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\dwloader.exe –S <Control node IP> -E –M reload –e UTF16 -i .\DimAccount.txt –T AdventureWorksPDW2012.dbo.DimAccount –R DimAccount.bad –t "|" –r \r\n –U <login> -P <password>  
```  
  
Descrizione dei parametri della riga di comando:  
  
-   *C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\dwloader.exe* è il percorso di installazione di dwloader.exe.  
  
-   *-S* è seguito dall'indirizzo IP del nodo di controllo.  
  
-   *-E* specifica per caricare le stringhe vuote come valori NULL.  
  
-   *-M ricaricare* specifica per troncare la tabella di destinazione prima di inserire i dati di origine.  
  
-   *-e UTF16* indica il file di origine utilizza little-endian codifica dei caratteri tipo.  
  
-   *-i.\DimAccount.txt* specifica i dati in un file denominato DimAccount.txt presente nella directory corrente.  
  
-   *-T AdventureWorksPDW2012.dbo.DimAccount* specifica il nome in 3 parti della tabella per ricevere i dati.  
  
-   *-R DimAccount.bad* specifica le righe che non riescono a caricare un file denominato DimAccount.bad verranno scritto.  
  
-   *– t "|"*  indica i campi nel file di input, DimAccount.txt, sono separati dal carattere di barra verticale.  
  
-   *-r \r\n* specifica ogni riga in DimAccount.txt termina con un ritorno a capo e avanzamento riga.  
  
-   *-U < login_name > -P <password>*  Specifica account di accesso e password per l'account di accesso che disponga delle autorizzazioni per eseguire il caricamento.  
  

<!-- MISSING LINK

## See Also  
[Common Metadata Query Examples](metadata-query-examples.md)  

-->
  
