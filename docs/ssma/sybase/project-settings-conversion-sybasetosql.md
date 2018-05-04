---
title: Impostazioni (conversione) (SybaseToSQL) del progetto | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: eeb80fa5-f530-4f21-beee-25f5a4b8ace6
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: a45639be8209a9d6996cd89d6fda1ddd195bfda0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="project-settings-conversion-sybasetosql"></a>Impostazioni del progetto (conversione) (SybaseToSQL)
La pagina di conversione del **impostazioni progetto** la finestra di dialogo contiene le impostazioni che consentono di personalizzare la modalità SSMA Converte la sintassi di Sybase Adaptive Server Enterprise (ASE) per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o la sintassi SQL Azure.  
  
Il riquadro di conversione è disponibile nel **impostazioni progetto** e **impostazioni di progetto predefinite** finestre di dialogo:  
  
-   Se si desidera specificare impostazioni per tutti i progetti SSMA, il **strumenti** dal menu **impostazioni di progetto predefinite**, fare clic su **generale** nella parte inferiore del riquadro sinistro e quindi fare clic su **conversione**.  
  
-   Per specificare le impostazioni per il progetto corrente, il **strumenti** dal menu **impostazioni progetto**, fare clic su **generale** nella parte inferiore del riquadro sinistro e quindi fare clic su **conversione**.  
  
## <a name="miscellaneous-options"></a>Opzioni varie  
**@@ERROR**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]O ASE e SQL Azure usare i codici di errore diversi.  
  
Utilizzare questa impostazione per specificare il tipo di messaggio (errore o avviso) contenente SSMA nel riquadro di Output o elenco errori quando viene rilevato un riferimento a **@@ERROR**  nel codice di base.  
  
-   Se si seleziona **convertire e contrassegnare con avviso**, SSMA convertirà le istruzioni e contrassegnarli con commenti di avviso.  
  
-   Se si seleziona **con errore**, SSMA ignorerà la conversione e contrassegnare le istruzioni con commenti di errore.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/Optimistic:** convertire e contrassegnare con avviso  
  
**Modalità completa:** contrassegno con l'errore  
  
**Conversione dell'operatore LIKE**  
Specifica se convertire come operandi in modo che corrisponda Sybase ASE. Il punto è che Sybase Taglia spazi vuoti finali in un modello like. La soluzione consiste nell'eseguire un cast dell'espressione a destra di un tipo di dati di lunghezza fissa con una precisione di massimo.  
  
-   Selezionare **conversione semplice** per convertire le espressioni senza alcuna correzione.  
  
-   Per utilizzare l'istruzione select comportamento ASE **eseguire il Cast a lunghezza fissa.**  
  
Quando si seleziona una modalità di conversione nella modalità, SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/Optimistic**: conversione semplice  
  
**Modalità**: eseguire il Cast a lunghezza fissa  
  
**CONVERTIRE O ESEGUIRE IL CAST DI STRINGHE VUOTE PER I TIPI NUMERICI**  
Specifica come gestire le stringhe vuote all'interno di espressioni di CONVERT o CAST con un tipo numerico come argomento di tipo di dati. Le opzioni seguenti sono disponibili per questa impostazione:  
  
-   Selezionare **conversione semplice** per convertire le espressioni senza alcuna correzione.  
  
-   Se **stringa vuota come zero numerico** è selezionata, quindi il parametro di stringa {s} verrà sostituito con ltrim(rtrim({s})) case quando "" quindi 0 else {s} espressione dell'estremità  
  
Quando si seleziona una modalità di conversione nella modalità, SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/Optimistic**: conversione semplice  
  
**Modalità**: stringa vuota come zero numerico  
  
**Concatenazione Null**  
Questa impostazione specifica come convertire la concatenazione di stringhe con valori NULL. Per questa impostazione specifica, è possono impostare le opzioni seguenti:  
  
-   **Eseguire il wrapping con la funzione ISNULL:** se questa opzione è impostata, verrà incluso ogni non costante 'string_expression' nella concatenazione ISNULL(string_expression) e i valori null verranno sostituite con una stringa vuota.  
  
-   **Mantenere la sintassi corrente**  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/Optimistic:** mantenere sintassi corrente  
  
**Modalità completa:** il wrapping con la funzione ISNULL  
  
**Conversione di stringhe vuote**  
Questa impostazione specifica come convertire le stringhe vuote. Per questa impostazione specifica, è possono impostare le opzioni seguenti:  
  
-   **Sostituire tutte le espressioni stringa con spazi**  
  
-   **Sostituire le costanti di stringa vuoto con lo spazio**  
  
-   Utilizzare il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/ comportamento di SQL Azure, seleziona **mantenere sintassi corrente**.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/Optimistic:** mantenere sintassi corrente  
  
**Modalità completa:** sostituire tutte le espressioni stringa con spazi  
  
**Conversione di stringa binaria di CAST e CONVERT**  
La conversione di valori binari in numeri può restituire valori diversi su piattaforme diverse. Ad esempio, su x86 processori, CONVERT (integer, 0x00000100) restituisce 65536 in ASE e 256 in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. ASE restituisce inoltre valori diversi a seconda dell'ordine dei byte.  
  
Utilizzare questa impostazione per controllare la modalità di conversione di SSMA converte e le espressioni CASE che contengono valori binari:  
  
-   Selezionare **conversione semplice** per convertire le espressioni senza alcun avviso o di una correzione. Usare questa impostazione se è noto che il server di base dispone di un ordine di byte che non richiede modifiche del valore binario.  
  
-   Selezionare **convertire e correggere** per convertire e correggere le espressioni per l'utilizzo in SSMA [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Verrà invertito l'ordine dei byte in valori letterali costanti. Tutti gli altri valori binari (ad esempio binarie variabili e colonne) verranno contrassegnati con errori. Utilizzare questo valore se si sa che il server di base dispone di un ordine di byte che richiede le modifiche ai valori binari.  
  
-   Selezionare **convertire e contrassegnare con avviso** per convertire e correggere le espressioni e contrassegnare tutti SSMA convertire espressioni con commenti di avviso.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita:** convertire e contrassegnare con avviso  
  
**La modalità ottimistico:** conversione semplice  
  
**Modalità completa:** convertire e correggere  
  
**SQL dinamico**  
Utilizzare questa impostazione per specificare il tipo di messaggio (errore o avviso) contenente SSMA nel riquadro di Output o elenco errori quando viene rilevato nel codice ASE istruzioni SQL dinamiche.  
  
-   Se si seleziona **convertire e contrassegnare con avviso**, SSMA convertirà il SQL dinamico e contrassegnare le istruzioni con commenti di avviso.  
  
-   Se si seleziona **con errore**, SSMA ignorerà la conversione e contrassegnare le istruzioni con commenti di errore.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/Optimistic:** convertire e contrassegnare con avviso  
  
**Modalità completa:** contrassegno con l'errore  
  
**Conversione di controllo di uguaglianza**  
In [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/ SQL Azure, se l'impostazione di ANSI_NULLS è on, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/ SQL Azure restituisce UNKNOWN quando un confronto di uguaglianza contiene un valore null. Se ANSI_NULLS è impostata su, i confronti di uguaglianza che contengono valori null restituiscono true se la colonna di confrontata e l'espressione o due espressioni sono entrambi null. Di uguaglianza predefinito (ANSINULL OFF) Sybase ASE confronti si comportano come [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/ SQL Azure con ANSI_NULLS OFF.  
  
-   Se si seleziona **conversione semplice**, SSMA convertirà il codice ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/ sintassi SQL Azure senza controlli aggiuntivi per i valori null. Utilizzare questa impostazione se ANSI_NULLS è impostata su [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/ SQL Azure o se si desidera modificare i confronti di uguaglianza per ogni caso.  
  
-   Se si seleziona **valori NULL è consigliabile**, SSMA aggiungerà i controlli per i valori null con la clausola IS NULL e IS NOT NULL.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/Optimistic:** conversione semplice  
  
**Modalità completa:** provare a NULL valori  
  
**Stringhe di formato**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/ Azure SQL non supporta più il *format_string* argomento nelle istruzioni PRINT e RAISERROR. Il *format_string* variabile supportati inserire parametri sostituibili direttamente nella stringa e quindi sostituendo i parametri in fase di esecuzione. In alternativa, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] richiede la stringa completa con un valore letterale stringa o una stringa compilata utilizzando una variabile. Per ulteriori informazioni, vedere la "PRINT ([!INCLUDE[tsql](../../includes/tsql_md.md)])" argomento nella [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione in linea.  
  
Quando SSMA rileva un *format_string* argomento, è possibile compilare una stringa letterale utilizzando le variabili o creare una nuova variabile e compilare una stringa utilizzando la variabile.  
  
-   Per utilizzare un valore letterale stringa per le funzioni PRINT e RAISERROR, selezionare **creare una nuova stringa**.  
  
    In questa modalità, se un'istruzione PRINT o RAISERROR non vengono usati i segnaposto e le variabili locali, l'istruzione viene modificato. Caratteri di percentuale doppio (%) vengono convertiti in un singolo carattere di percentuale % nei valori letterali di stringa di stampa.  
  
    Se viene utilizzata un'istruzione PRINT o RAISERROR segnaposto e uno o più variabili locali, come illustrato nell'esempio seguente:  
  
    ```  
    PRINT 'Total: %1!%%', @percent  
    ```  
    SSMA viene convertito nella sintassi seguente:  
  
    ```  
    PRINT 'Total: '+ CAST(@percent AS varchar(max)) + '%'  
    ```  
    Se *format_string* è una variabile, ad esempio nell'istruzione seguente:  
  
    ```  
    PRINT @fmt, @arg1, @arg2  
    ```  
    SSMA non è possibile eseguire una conversione di stringa semplice e deve creare una nuova variabile:  
  
    ```  
    DECLARE @print_format_1 varchar(max)  
    SET @print_format_1  =   
        REPLACE (@fmt, '%%', '%')  
    SET @print_format_1  =   
        REPLACE (@print_format_1, '%1!',   
        CAST (@arg1 AS varchar(max)))  
    SET @print_format_1  =   
        REPLACE (@print_format_1, '%2!',   
        CAST (@arg2 AS varchar(max)))  
    PRINT @print_format_1  
    ```  
    Quando utilizza **creare una nuova stringa** modalità SSMA si presuppone che il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] opzione CONCAT_NULL_YIELDS_NULL è OFF. Pertanto, SSMA non verifica per gli argomenti null.  
  
-   Per creare una nuova variabile per ogni istruzione PRINT e RAISERROR e quindi utilizzare tale variabile per il valore stringa SSMA, selezionare **Crea nuova variabile**.  
  
    In questa modalità, se un'istruzione PRINT o RAISERROR non vengono utilizzati i segnaposto e le variabili locali, SSMA sostituisce tutti i caratteri di percentuale doppio (%) con i singoli caratteri percentuale per la conformità con [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/ sintassi SQL Azure.  
  
    Se viene utilizzata un'istruzione PRINT o RAISERROR segnaposto e uno o più variabili locali, come illustrato nell'esempio seguente:  
  
    ```  
    PRINT 'Total: %1!%%', @percent  
    ```  
    SSMA viene convertito nella sintassi seguente:  
  
    ```  
    DECLARE @print_format_1 varchar(max)  
    SET @print_format_1 = 'Total: %1!%'  
    SET @print_format_1  =   
        REPLACE (@print_format_1, '%1!',   
        ISNULL(CAST (@percent AS VARCHAR(max)), ''))  
    PRINT @print_format_1  
    ```  
    Se *format_string* è una variabile, ad esempio nell'istruzione seguente:  
  
    ```  
    PRINT @fmt, @arg1, @arg2  
    ```  
    SSMA consente di creare una nuova variabile come indicato di seguito, verifica dei valori null in ogni argomento:  
  
    ```  
    DECLARE @print_format_1 varchar(max)  
    SET @print_format_1  =   
        REPLACE (@fmt, '%%', '%')  
    SET @print_format_1  =   
        REPLACE (@print_format_1, '%1!',   
        ISNULL(CAST (@arg1 AS varchar(max)),''))  
    SET @print_format_1  =   
        REPLACE (@print_format_1, '%2!',   
        ISNULL(CAST (@arg2 AS varchar(max)),''))  
    PRINT @print_format_1  
    ```  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/Optimistic:** creare nuova stringa  
  
**Modalità completa:** Crea nuova variabile  
  
**Inserire un valore esplicito in una colonna timestamp**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/ Azure SQL non supporta l'inserimento di valori espliciti in una colonna timestamp.  
  
-   Per escludere colonne timestamp da istruzioni INSERT, selezionare **colonna Escludi**.  
  
-   Per stampare un messaggio di errore ogni volta che è una colonna timestamp in un'istruzione INSERT, selezionare **con errore**. In questa modalità, le istruzioni INSERT non verranno convertite e verranno contrassegnate con i commenti di errore.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/Optimistic:** colonna Escludi  
  
**Modalità completa:** contrassegno con l'errore  
  
**Archiviare gli oggetti temporanei definiti nelle procedure**  
Questa impostazione specifica se le definizioni di oggetti temporanei che vengono visualizzati nelle procedure devono essere archiviate nei metadati di origine durante la conversione.  
  
-   Selezionare **Sì** per archiviare nei metadati.  
  
-   Selezionare **n** se gli oggetti non devono essere archiviati.  
  
**La modalità predefinita/ottimistico:** Sì  
  
**Modalità completa:** No  
  
**Conversione della tabella proxy**  
Specifica se le tabelle di base proxy vengono convertite in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/ tabelle di SQL Azure, o sono non convertito e il codice è contrassegnato con commenti di errore.  
  
-   Selezionare **convertire** per convertire le tabelle di proxy in tabelle normali.  
  
-   Selezionare **con errore** semplicemente contrassegnare il codice del proxy tabella con i commenti di errore.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/Optimistic/Full:** contrassegno con l'errore  
  
**Numero di messaggio di base di RAISERROR**  
I messaggi utente ASE vengono archiviati in ogni database. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] i messaggi dell'utente sono archiviati centralmente e resi disponibili tramite il **Sys. Messages** vista del catalogo. Inoltre i messaggi utente ASE partono 20000, ma [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] messaggi di errore partono 50001.  
  
Questa impostazione specifica il numero di aggiungere il numero di messaggio utente ASE per convertirlo in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] messaggio utente. Se il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] presenta messaggi utente nella **Sys. Messages** vista del catalogo, potrebbe essere necessario modificare questo numero su un valore superiore. Si tratta pertanto i numeri di messaggio convertito non siano in conflitto con i numeri di messaggio esistente.  
  
Si noti quanto segue:  
  
-   I messaggi di ASE nell'intervallo 17000 19999 dalla tabella sysmessages del sistema e non vengono convertiti.  
  
-   Se il numero di messaggi a cui fa riferimento nell'istruzione RAISERROR è una costante, SSMA aggiungerà il numero di messaggio di base per la costante per determinare il numero di messaggio nuovo utente.  
  
-   Se il numero di messaggi a cui fa riferimento è una variabile o espressione, SSMA verrà creata una variabile locale intermedia.  
  
-   In modalità ottimistica SSMA si presuppone che il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] opzione CONCAT_NULL_YIELDS_NULL è disattivata ed non esegue alcun controllo per gli argomenti null.  
  
-   In modalità estesa, SSMA verifica per gli argomenti null.  
  
-   RAISERROR con ERRORDATA *elenco* non viene convertito.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/ottimistica/Full:** 30001  
  
**Oggetti di sistema**  
Utilizzare questa impostazione per specificare il tipo di messaggio (errore o avviso) contenente SSMA nel riquadro di Output o elenco errori quando viene rilevato l'utilizzo di oggetti di sistema di base.  
  
-   Se si seleziona **convertire e contrassegnare con avviso**, SSMA convertirà i riferimenti agli oggetti di sistema e verranno contrassegnate come istruzioni con commenti di avviso.  
  
-   Se si seleziona **con errore**, SSMA non convertirà i riferimenti a oggetti di sistema e verranno contrassegnate come istruzioni con commenti di errore.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/Optimistic:** convertire e contrassegnare con avviso  
  
**Modalità completa:** contrassegno con l'errore  
  
**Identificatori non risolti**  
Utilizzare questa impostazione per specificare il tipo di messaggio (errore o avviso) contenente SSMA nel riquadro di Output o elenco errori quando è in grado di risolvere un identificatore.  
  
-   Se si seleziona **convertire e contrassegnare con avviso**, SSMA tenterà di convertire i riferimenti a identificatori non risolti e verranno contrassegnate come istruzioni con commenti di avviso.  
  
-   Se si seleziona **con errore**, SSMA non convertirà il riferimento agli identificatori non risolti e verranno contrassegnate come istruzioni con commenti di errore.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/Optimistic:** convertire e contrassegnare con avviso  
  
**Modalità completa:** contrassegno con l'errore  
  
## <a name="system-function-options"></a>Opzioni della funzione di sistema  
**CHARINDEX, funzione**  
In ASE, CHARINDEX restituisce NULL solo se tutte le espressioni di input sono NULL. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]O SQL Azure restituirà NULL se qualsiasi espressione di input è NULL.  
  
-   Per utilizzare il comportamento di base, selezionare **funzione Replace**. Tutte le chiamate alla funzione CHARINDEX viene sostituito con una chiamata a CHARINDEX_VARCHAR o CHARINDEX_NVARCHAR funzione definita dall'utente in base al tipo dei parametri passati (creato nel database utente con il nome di schema 's2ss') per emulare il comportamento di Sybase ASE.  
  
-   Utilizzare il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/ comportamento di SQL Azure, seleziona **mantenere sintassi corrente**.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/Optimistic:** mantenere sintassi corrente  
  
**Modalità completa:** sostituire (funzione)  
  
**Funzione DATALENGTH**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] O SQL Azure e ASE diversi nel valore restituito dalla funzione DATALENGTH quando il valore è uno spazio singolo. In questo caso, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/ SQL Azure restituisce 0 e ASE restituisce 1.  
  
-   Per utilizzare il comportamento di base, selezionare **funzione Replace**. Tutte le chiamate alla funzione DATALENGTH vengono sostituite con l'espressione CASE per emulare il comportamento di Sybase ASE.  
  
-   Utilizzare il valore predefinito [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] / comportamento di SQL Azure, seleziona **mantenere sintassi corrente**.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/Optimistic:** mantenere sintassi corrente  
  
**Modalità completa:** sostituire (funzione)  
  
**Index_col-funzione**  
ASE supporta facoltativa *user_id* argomento della funzione INDEX_COL; tuttavia, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/ SQL Azure non supporta questo argomento. Se si utilizza il *user_id* argomento, questa funzione non può essere convertita in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/ sintassi SQL Azure.  
  
-   Per utilizzare il comportamento di base, selezionare **funzione Convert**. Se il codice contiene la *user_id* SSMA argomento verrà visualizzato un errore.  
  
-   Per visualizzare un messaggio di errore ogni volta che viene rilevato che INDEX_COL, selezionare **con errore**. SSMA riferimenti alla funzione non viene convertito e contrassegnerà l'istruzione con commenti di errore.  
  
**Modalità predefinita/Optimistic/Full:** contrassegno con l'errore  
  
**Funzione INDEX_COLORDER**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]O SQL Azure non dispone di una funzione di sistema INDEX_COLORDER.  
  
-   Per utilizzare il comportamento di base, selezionare **funzione Convert**. Tutte le chiamate alla funzione INDEX_COLORDER viene sostituito con una chiamata a una funzione definita dall'utente con lo stesso nome INDEX_COLORDER (creato nel database utente con il nome di schema 's2ss'), che emula il comportamento di Sybase ASE.  
  
-   Per stampare un messaggio di errore ogni volta che viene rilevato che INDEX_COLORDER, selezionare **con errore**. SSMA riferimenti alla funzione non viene convertito e contrassegnerà l'istruzione con commenti di errore.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/Optimistic/Full:** contrassegno con l'errore  
  
**Le funzioni LEFT e RIGHT**  
A sinistra e destra funzioni Sybase si comportano in modo diverso per il parametro di lunghezza negativa.  
  
-   Per utilizzare il comportamento di base, selezionare **funzione Replace**. Il parametro della lunghezza verrà quindi sostituito con l'espressione CASE restituisce null per un valore negativo.  
  
-   Per utilizzare il comportamento di SQL Server, selezionare **mantenere sintassi corrente**  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/Optimistic:** mantenere sintassi corrente  
  
**Modalità completa:** sostituire (funzione)  
  
> [!NOTE]  
> Se il parametro della lunghezza è un valore letterale e non un'espressione complessa, il valore di lunghezza viene sempre sostituito con il valore null indipendentemente dalle impostazioni di progetto.  
  
**Funzione NEXT_IDENTITY**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]O SQL Azure non dispone di una funzione di sistema NEXT_IDENTITY.  
  
-   Per utilizzare il comportamento di base, selezionare **convertire funzione**. Tutte le chiamate alla funzione NEXT_IDENTITY viene sostituito con l'espressione (IDENT_CURRENT(parameter Value) + IDENT_INCR(parameter Value) che emula il comportamento di Sybase ASE.  
  
-   Per stampare un messaggio di errore ogni volta che viene rilevato che NEXT_IDENTITY, selezionare **con errore**. SSMA riferimenti alla funzione non viene convertito e contrassegnerà l'istruzione con commenti di errore.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/Optimistic/Full:** contrassegno con l'errore  
  
**Funzione PATINDEX**  
Specifica se convertire la funzione PATINDEX per corrispondere Sybase ASE comportamento. Il punto è che Sybase Taglia spazi vuoti finali in un criterio di ricerca. La soluzione alternativa è eseguire un cast dell'espressione di valore a una lunghezza fissa di tipo con una precisione massima di dati e applicano la funzione rtrim per eseguire la ricerca di modello.  
  
-   Per utilizzare l'istruzione select comportamento ASE **utilizzare**.  
  
-   Utilizzare il valore predefinito [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/ comportamento di SQL Azure, seleziona **non utilizzano**.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/Optimistic:** non usare  
  
**Modalità completa:** utilizzo  
  
**REPLICATE-funzione**  
La funzione REPLICATE ripete il numero specificato di volte in cui una stringa. In ASE, se si specifica per ripetere la stringa di zero volte, il risultato è null. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/ SQL Azure, il risultato è una stringa vuota.  
  
-   Per utilizzare il comportamento di base, selezionare **funzione Replace**. Tutte le chiamate alla funzione di replica viene sostituito con una chiamata a REPLICATE_VARCHAR o REPLICATE_NVARCHAR funzione definita dall'utente in base al tipo dei parametri passati (creato nel database utente con il nome di schema 's2ss') per emulare il comportamento di Sybase ASE.  
  
-   Utilizzare il valore predefinito [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/ comportamento di SQL Azure, seleziona **funzione Replace**.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità di modalità/Full predefinito/Optimistic:** sostituire (funzione)  
  
**Funzione TRIM (LTRIM, RTRIM)**  
Questa impostazione specifica se per sostituire le chiamate alle funzioni Trim (LTRIM, RTRIM) con le funzioni di sintassi Sybase ASE equivalenti o per mantenere la sintassi corrente. Le opzioni seguenti sono presenti per questa impostazione specifica:  
  
-   **Funzione Replace**  
  
-   **Mantenere la sintassi corrente**  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità di modalità/Full predefinito/Optimistic:** sostituire (funzione)  
  
**SUBSTRING-funzione**  
In base, la funzione `SUBSTRING(expression, start, length)` restituisce NULL se viene specificato un valore di inizio maggiore del numero di caratteri nell'espressione o lunghezza è uguale a zero. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]/ SQL Azure, l'espressione equivalente restituisce una stringa vuota.  
  
-   Per utilizzare il comportamento di base, selezionare **funzione Replace**. Tutte le chiamate di funzione SUBSTRING viene sostituito con una chiamata a SUBSTRING_VARCHAR o SUBSTRING_NVARCHAR o SUBSTRING_VARBINARY funzione definita dall'utente in base al tipo dei parametri passati (creato nel database utente con il nome di schema 's2ss') per emulare il comportamento di Sybase ASE.  
  
-   Utilizzare il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] / comportamento di SQL Azure, seleziona **mantenere sintassi corrente**.  
  
Quando si seleziona una modalità di conversione di **modalità** casella SSMA si applica l'impostazione seguente:  
  
**Modalità predefinita/Optimistic:** mantenere sintassi corrente  
  
**Modalità completa:** sostituire (funzione)  
  
## <a name="tables"></a>TABLES  
**Aggiungere la chiave primaria**  
Crea una nuova chiave primaria di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o una tabella di SQL Azure, se una tabella di accesso non dispone di alcuna chiave primaria o un indice univoco.  
  
-   **Modalità predefinita**: False  
  
-   **Modalità ottimistica**: False  
  
-   **Modalità**: True  
  
> [!NOTE]  
> Quando si è connessi a SQL Azure, è per impostazione predefinita True.  
  
## <a name="see-also"></a>Vedere anche  
[Riferimento all'interfaccia utente &#40;SybaseToSQL&#41;](../../ssma/sybase/user-interface-reference-sybasetosql.md)  
  
