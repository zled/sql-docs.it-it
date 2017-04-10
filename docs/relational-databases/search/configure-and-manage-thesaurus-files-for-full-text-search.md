---
title: "Configurare e gestire i file del thesaurus per la ricerca full-text | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-search"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "indici full-text [SQL Server], file del thesaurus"
  - "thesaurus [ricerca full-text], configurazione"
  - "thesaurus [ricerca full-text]"
ms.assetid: 3ef96a63-8a52-45be-9a1f-265bff400e54
caps.latest.revision: 84
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 83
---
# Configurare e gestire i file del thesaurus per la ricerca full-text
  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le query full-text consentono di eseguire una ricerca di sinonimi dei termini specificati dall'utente tramite l'utilizzo di un thesaurus. In un *thesaurus* di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene definito un set di sinonimi per una lingua specifica. Gli amministratori di sistema possono definire due forme di sinonimi, i set di espansione e i set di sostituzione. Sviluppando un thesaurus basato sui dati full-text in uso, è possibile ampliare in modo efficace l'ambito delle query full-text su tali dati. La corrispondenza con il thesaurus si verifica per tutte le query [FREETEXT](../../t-sql/queries/freetext-transact-sql.md) e [FREETEXTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md) e per tutte le query [CONTAINS](../../t-sql/queries/contains-transact-sql.md) e [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) che specificano la clausola FORMSOF THESAURUS.  
  
##  <a name="tasks"></a> Attività di base per la configurazione di un file del thesaurus  
 Prima che le query di ricerca full-text nell'istanza del server siano in grado di eseguire la ricerca di sinonimi in una determinata lingua, è necessario definire mapping del thesaurus (sinonimi) per tale lingua. È necessario configurare manualmente ogni thesaurus per definire gli elementi seguenti:  
  
-   Impostazione dei segni diacritici  
  
     Per un determinato thesaurus, tutti i criteri di ricerca supportano o non supportano la distinzione relativa ai segni diacritici come la tilde (**~**), l'accento acuto (**´**) o l'umlaut (**¨**), ovvero *supportano la distinzione tra caratteri accentati e non accentati* o *non supportano la distinzione tra caratteri accentati e non accentati*. Si supponga, ad esempio, di specificare la sostituzione del criterio "café" con altri criteri in una query di ricerca full-text. Se il thesaurus non supporta la distinzione tra caratteri accentati e non accentati, tramite la ricerca full-text verranno sostituiti i criteri "café" e "cafe". Se il thesaurus supporta la distinzione tra caratteri accentati e non accentati, tramite la ricerca full-text verrà sostituito solo il criterio "café". Per impostazione predefinita, un thesaurus non supporta la distinzione tra caratteri accentati e non accentati.  
  
-   Set di espansione  
  
     Un set di espansione contiene un gruppo di sinonimi, ad esempio "writer", "author" e "journalist", che vengono sostituiti gli uni con gli altri da una query full-text. Le query che contengono una corrispondenza per uno dei sinonimi in un set di espansione vengono espanse per includere ogni altro sinonimo nel set di espansione stesso.  
  
     Per altre informazioni, vedere "Struttura XML di un set di espansione" più avanti in questo argomento.  
  
-   Set di sostituzione  
  
     Un set di sostituzione include un criterio di testo da sostituire con parole specifiche. Vedere, ad esempio, la sezione "Struttura XML di un set di sostituzione" più avanti in questo argomento.  
  
 [&#91;Torna all'inizio&#93;](#Top)  
  
##  <a name="initial_thesaurus_files"></a> Contenuto iniziale dei file del thesaurus  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] offre un set di file XML del thesaurus, uno per ogni lingua supportata. Tali file sono essenzialmente vuoti e contengono solo la struttura XML di livello principale comune a tutti i thesaurus di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e un thesaurus di esempio costituito da commenti.  
  
 Tutti i file del thesaurus disponibili in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contengono il codice XML seguente:  
  
```  
<XML ID="Microsoft Search Thesaurus">  
  
<!--  Commented out  
  
    <thesaurus xmlns="x-schema:tsSchema.xml">  
<diacritics_sensitive>0</diacritics_sensitive>  
        <expansion>  
            <sub>Internet Explorer</sub>  
            <sub>IE</sub>  
            <sub>IE5</sub>  
        </expansion>  
        <replacement>  
            <pat>NT5</pat>  
            <pat>W2K</pat>  
            <sub>Windows 2012</sub>  
        </replacement>  
        <expansion>  
            <sub>run</sub>  
            <sub>jog</sub>  
        </expansion>  
    </thesaurus>  
-->  
</XML>  
```  
  
 [&#91;Torna all'inizio&#93;](#Top)  
  
##  <a name="location"></a> Percorso dei file del thesaurus  
 Il percorso predefinito dei file del thesaurus è il seguente:  
  
 *<percorso_file_dati_SQL_Server>*\MSSQL13.MSSQLSERVER\MSSQL\FTDATA\  
  
 Tale percorso predefinito contiene i file seguenti:  
  
-   File del thesaurus specifici della lingua  
  
     Durante l'installazione, nel percorso indicato in precedenza vengono installati file del thesaurus vuoti, uno per ogni lingua supportata. Tali file possono essere personalizzati da un amministratore di sistema.  
  
     Per i nomi predefiniti dei file del thesaurus viene usato il formato seguente:  
  
     ‘ts’ + <abbreviazione lingua di tre lettere> + '.xml'  
  
     Il nome del file del thesaurus per una lingua specifica è indicato nel valore del Registro di sistema HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<nome-istanza>\MSSearch\\<abbrev-lingua>.  
  
-   File del thesaurus globale  
  
     File del thesaurus globale vuoto denominato tsGlobal.xml.  
  
 È possibile modificare il percorso e il nome di un file del thesaurus modificando la relativa chiave del Registro di sistema. Per ogni lingua, il percorso del file del thesaurus viene specificato nel seguente valore del Registro di sistema:  
  
 HKLM/SOFTWARE/Microsoft/Microsoft SQL Server/\<nome istanza>/MSSearch/Language/\<abbreviazione-lingua>/TsaurusFile  
  
 Il file del thesaurus globale corrisponde alla lingua neutra con LCID 0. Questo valore può essere modificato solo dagli amministratori.  
  
 [&#91;Torna all'inizio&#93;](#Top)  
  
##  <a name="how_queries_use_tf"></a> Modalità di utilizzo dei file del thesaurus nelle query  
 Una query sul thesaurus usano sia un thesaurus specifico della lingua sia un thesaurus globale. La query esegue innanzitutto la ricerca in un file specifico della lingua e lo carica per l'elaborazione, a meno che non sia già caricato. La query viene quindi espansa per includere i sinonimi specifici della lingua indicati dalle regole del set di espansione e del set di sostituzione nel file del thesaurus. Questi passaggi vengono quindi ripetuti per il thesaurus globale. Se, tuttavia, nel file del thesaurus specifico della lingua è già stata individuata una corrispondenza per un termine, tale termine non può essere considerato valido per la corrispondenza nel thesaurus globale.  
  
 [&#91;Torna all'inizio&#93;](#Top)  
  
##  <a name="structure"></a> Informazioni sulla struttura di un file del thesaurus  
 Ogni file del thesaurus definisce un contenitore XML, il cui ID è `Microsoft Search Thesaurus`, e un commento, `<!--` … `-->`, che contiene un thesaurus di esempio. Il thesaurus è definito in un elemento \<thesaurus> contenente esempi degli elementi figlio che definiscono l'impostazione dei segni diacritici, i set di espansione e i set di sostituzione, come indicato di seguito:  
  
-   Struttura XML dell'impostazione dei segni diacritici  
  
     L'impostazione dei segni diacritici di un thesaurus è specificata in un singolo elemento <diacritics_sensitive>, che contiene un valore intero che determina il supporto della distinzione tra caratteri accentati e non accentati, come indicato di seguito:  
  
    |Impostazione dei segni diacritici|Valore|XML|  
    |------------------------|-----------|---------|  
    |Nessuna distinzione caratteri accentati/non accentati|0|`<diacritics_sensitive>0</diacritics_sensitive>`|  
    |Distinzione caratteri accentati/non accentati|1|`<diacritics_sensitive>1</diacritics_sensitive>`|  
  
    > [!NOTE]  
    >  Questa impostazione può essere applicata solo una volta nel file e si applica a tutti i criteri di ricerca nel file. L'impostazione non può essere specificata per singoli criteri.  
  
-   Struttura XML di un set di espansione  
  
     Ogni set di espansione è racchiuso in un elemento \<expansion>. All'interno di questo elemento è possibile specificare una o più sostituzioni in un elemento \<sub>. Nel set di espansione è possibile specificare un gruppo di sostituzioni che sono sinonimi una dell'altra.  
  
     Ad esempio, è possibile modificare la sezione di espansione per considerare le sostituzioni "writer", "author" e "journalist" come sinonimi. per includere tutte le altre sostituzioni specificate nel set di espansione, vengono espanse le query di ricerca full-text che contengono corrispondenze in una sostituzione. Di conseguenza, quando nell'esempio precedente si esegue una query FORMS OF THESAURUS o FREETEXT per la parola "author", vengono restituiti anche i risultati di ricerca contenenti le parole "writer" e "journalist".  
  
     La sezione del set di espansione dell'esempio precedente sarà la seguente:  
  
    ```  
    <expansion>  
            <sub>writer</sub>  
            <sub>author</sub>  
            <sub>journalist</sub>  
    </expansion>  
    ```  
  
-   Struttura XML di un set di sostituzione  
  
     Ogni set di sostituzione è racchiuso in un elemento \<replacement>. All'interno di questo elemento è possibile specificare uno o più criteri in un elemento \<pat> e zero o più sostituzioni in elementi \<sub>, uno per sinonimo. È possibile specificare un criterio da sostituire con un set di sostituzione. I criteri e le sostituzioni possono contenere una parola o una sequenza di parole. Se non viene specificata alcuna sostituzione per un criterio, questo verrà rimosso dalla query dell'utente.  
  
     Si supponga, ad esempio, di voler eseguire query per sostituire il criterio "Win8" con "Windows Server 2012" o "Windows 8.0". Se si esegue una query full-text per "Win8", verranno restituiti solo i risultati di ricerca full-text contenenti le sostituzioni "Windows Server 2012" o "Windows 8.0". ma non quelli contenenti "Win8". Questo accade perché "Win8" è stato "sostituito" con "Windows Server 2012" e "Windows 8.0".  
  
     La sezione del set di sostituzione dell'esempio sopra descritto sarebbe:  
  
    ```  
    <replacement>  
            <pat>Win8</pat>  
            <sub>Windows Server 2012</sub>  
            <sub>Windows 8.0</sub>  
    </replacement>  
    ```  
  
     Se sono presenti due set di sostituzione con criteri di testo simili da associare, il più lungo dei due ha la precedenza. Se, ad esempio, si esegue una query FORMS OF THESAURUS per "Internet Explorer online community" e sono presenti i set di sostituzione indicati di seguito, "Internet Explorer" ha la precedenza su "Internet". La query verrà pertanto elaborata come "IE online community" o "IE 9 online community".  
  
    ```  
    <replacement>  
             <pat>Internet</pat>  
             <sub>intranet</sub>  
    </replacement>  
    ```  
  
     e  
  
    ```  
    <replacement>  
             <pat>Internet Explorer</pat>  
             <sub>IE</sub>  
             <sub>IE 9</sub>  
    </replacement>  
    ```  
  
 [&#91;Torna all'inizio&#93;](#Top)  
  
##  <a name="working_with_thesaurus_files"></a> Utilizzo dei file del thesaurus  
 **Per modificare un file del thesaurus**  
  
-   [Modifica di un file del thesaurus](#editing)  
  
 **Per caricare un file del thesaurus aggiornato**  
  
-   [sp_fulltext_load_thesaurus_file &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql.md)  
  
 **Per visualizzare il risultato della suddivisione in token di una combinazione di word breaker, thesaurus ed elenchi di parole non significative**  
  
-   [sys.dm_fts_parser &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql.md)  
  
 [&#91;Torna all'inizio&#93;](#Top)  
  
##  <a name="editing"></a> Modifica di un file del thesaurus  
 È possibile configurare il thesaurus per una lingua specifica modificando il relativo file XML. Durante l'installazione vengono installati file del thesaurus vuoti che contengono solo il contenitore \<xml> e un elemento \<thesaurus> di esempio costituito da commenti. Ai fini della corretta esecuzione delle query di ricerca full-text per la ricerca di sinonimi, è necessario creare un elemento \<thesaurus> effettivo che definisca un set di sinonimi. È possibile definire due forme di sinonimi, i set di espansione e i set di sostituzione.  
  
 **Restrizioni relative ai file del thesaurus**  
  
 Alla modifica di un file del thesaurus si applicano le restrizioni seguenti:  
  
-   Solo gli amministratori di sistema possono aggiornare, modificare o eliminare i file del thesaurus.  
  
-   Quando si usano editor di testo per modificare i file del thesaurus, è necessario salvare i file in formato Unicode e specificare gli indicatori per l'ordine dei byte (BOM).  
  
-   Le voci del thesaurus non possono essere vuote e non è possibile eseguirne il word breaking in una stringa vuota.  
  
-   Le frasi nel file del thesaurus non devono essere costituite da più di 512 caratteri.  
  
-   Un thesaurus non deve contenere alcuna voce duplicata fra le voci \<sub> dei set di espansione e gli elementi \<pat> dei set di sostituzione.  
  
 **Indicazioni per i file del thesaurus**  
  
 È consigliabile che le voci del file del thesaurus non contengano caratteri speciali, in quanto i word breaker rivelano comportamenti imprevedibili in presenza di tale tipo di caratteri. Se una voce del thesaurus contiene un carattere speciale, i word breaker usati in combinazione con la voce possono avere un comportamento imprevisto con implicazioni su una query full-text.  
  
 È consigliabile che le voci \<sub> non contengano parole non significative, in quanto tali parole vengono omesse dall'indice full-text. Le query vengono espanse per includere le voci \<sub> da un file del thesaurus e se una voce \<sub> contiene parole non significative, le dimensioni della query aumentano inutilmente.  
  
#### Per modificare un file del thesaurus  
  
1.  Aprire il file del thesaurus nel Blocco note.  
  
2.  Se si modifica un file del thesaurus per la prima volta, rimuovere le righe di commento seguenti all'inizio e alla fine del file, rispettivamente:  
  
    ```  
    <!--Commented out  
    -->  
    ```  
  
3.  Aggiungere, modificare o eliminare un set di sostituzione o set di espansione.  
  
4.  Salvare il file e chiudere il Blocco note.  
  
5.  Utilizzare [sp_fulltext_load_thesaurus_file](../../relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql.md) per caricare il contenuto del file del thesaurus in tempdb, specificando l'identificatore LCID corrispondente alla lingua del file del thesaurus. Per il file del thesaurus per la lingua inglese, denominato tsenu.xml, l'identificatore LCID corrispondente è 1033.  
  
    ```  
    USE AdventureWorks2012 ;  
    EXEC sys.sp_fulltext_load_thesaurus_file 1033;  
    GO  
    ```  
  
 [&#91;Torna all'inizio&#93;](#Top)  
  
## Vedere anche  
 [CONTAINS &#40;Transact-SQL&#41;](../../t-sql/queries/contains-transact-sql.md)   
 [CONTAINSTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/containstable-transact-sql.md)   
 [FREETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/freetext-transact-sql.md)   
 [FREETEXTTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/freetexttable-transact-sql.md)   
 [Ricerca full-text](../../relational-databases/search/full-text-search.md)  
  
  