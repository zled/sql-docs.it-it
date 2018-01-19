---
title: DECLARE CURSOR (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DECLARE_CURSOR_TSQL
- CURSOR_TSQL
- DECLARE CURSOR
- CURSOR
dev_langs: TSQL
helpviewer_keywords:
- DECLARE CURSOR statement
- cursors [SQL Server], attributes
- local cursors [SQL Server]
- nesting cursors
- Transact-SQL cursors, attributes
- global cursors [SQL Server]
ms.assetid: 5a3a27aa-03e8-4c98-a27e-809282379b21
caps.latest.revision: "51"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 1f09a8eb025af56d5edee0a3a4d0861b7edb515f
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="declare-cursor-transact-sql"></a>DECLARE CURSOR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Definisce gli attributi di un cursore del server [!INCLUDE[tsql](../../includes/tsql-md.md)], ad esempio lo scorrimento e la query utilizzata per compilare il set di risultati su cui agisce il cursore. L'istruzione DECLARE CURSOR supporta la sintassi basata sullo standard ISO e la sintassi che utilizza un set di estensioni [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
ISO Syntax  
DECLARE cursor_name [ INSENSITIVE ] [ SCROLL ] CURSOR   
     FOR select_statement   
     [ FOR { READ ONLY | UPDATE [ OF column_name [ ,...n ] ] } ]  
[;]  
Transact-SQL Extended Syntax  
DECLARE cursor_name CURSOR [ LOCAL | GLOBAL ]   
     [ FORWARD_ONLY | SCROLL ]   
     [ STATIC | KEYSET | DYNAMIC | FAST_FORWARD ]   
     [ READ_ONLY | SCROLL_LOCKS | OPTIMISTIC ]   
     [ TYPE_WARNING ]   
     FOR select_statement   
     [ FOR UPDATE [ OF column_name [ ,...n ] ] ]  
[;]  
```  
  
## <a name="arguments"></a>Argomenti  
 *cursor_name*  
 È il nome del [!INCLUDE[tsql](../../includes/tsql-md.md)] cursore del server definito. *cursor_name* deve essere conforme alle regole per gli identificatori.  
  
 INSENSITIVE  
 Definisce un cursore che crea una copia temporanea dei dati utilizzati dal cursore. Tutte le richieste fino al cursore vengono soddisfatte tramite questa tabella temporanea in **tempdb**; pertanto, le modifiche apportate alle tabelle di base non vengono riflesse nei dati restituiti dalle operazioni di recupero eseguite in questo cursore, e questo non è consentito modifiche. Nella sintassi ISO, se viene omessa la parola chiave INSENSITIVE, le operazioni di eliminazione e aggiornamento eseguite nelle tabelle sottostanti da parte degli utenti e di cui è stato eseguito il commit vengono riportate nelle successive operazioni di recupero.  
  
 SCROLL  
 Specifica che tutte le opzioni di recupero (FIRST, LAST, PRIOR, NEXT, RELATIVE, ABSOLUTE) sono disponibili. Se non viene specificata l'opzione SCROLL in un'istruzione DECLARE CURSOR di ISO, l'unica opzione di recupero supportata è NEXT. Non è possibile specificare SCROLL se è stata specificata l'opzione FAST_FORWARD.  
  
 *select_statement*  
 Istruzione SELECT standard che definisce il set di risultati del cursore. Le parole chiave FOR BROWSE e INTO non sono consentite all'interno di *select_statement* di una dichiarazione di cursore.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Converte in modo implicito il cursore in un altro tipo, se le clausole in *select_statement* conflitto con la funzionalità del tipo di cursore richiesto.  
  
 READ ONLY  
 Impedisce gli aggiornamenti eseguiti tramite il cursore. Non è possibile fare riferimento al cursore in una clausola WHERE CURRENT OF di un'istruzione UPDATE o DELETE. Questa opzione è prioritaria rispetto alla funzionalità di aggiornamento predefinita di un cursore.  
  
 AGGIORNAMENTO [OF *column_name* [**,**... *n*]]  
 Definisce le colonne aggiornabili nel cursore. Se viene specificato OF *column_name* [**,**... *n*] è specificato, solo le colonne elencate è possibile apportare modifiche. Se l'istruzione UPDATE viene specificata senza un elenco di colonne, è possibile aggiornare tutte le colonne.  
  
 *cursor_name*  
 È il nome del [!INCLUDE[tsql](../../includes/tsql-md.md)] cursore del server definito. *cursor_name* deve essere conforme alle regole per gli identificatori.  
  
 LOCAL  
 Specifica che l'ambito del cursore è locale rispetto al batch, alla stored procedure o al trigger in cui il cursore è stato creato. Il nome del cursore è valido solo in tale ambito. È possibile fare riferimento al cursore tramite variabili di cursore locali nel batch, nella stored procedure o nel trigger oppure tramite un parametro OUTPUT di stored procedure. Un parametro OUTPUT consente di passare il cursore locale al batch, alla stored procedure o al trigger chiamante, che può quindi assegnare il parametro a una variabile cursore per fare riferimento al cursore dopo l'esecuzione della stored procedure. Il cursore viene deallocato in modo implicito al termine del batch, della stored procedure o del trigger, a meno che non venga passato a un parametro OUTPUT. In tal caso, il cursore viene deallocato quando l'ultima variabile che vi fa riferimento viene deallocata o risulta esterna all'ambito di validità.  
  
 GLOBAL  
 Specifica che l'ambito del cursore è globale rispetto alla connessione. È possibile fare riferimento al nome del cursore in qualsiasi stored procedure o batch eseguiti tramite la connessione. Il cursore viene deallocato solo in modo implicito in fase di disconnessione.  
  
> [!NOTE]  
>  Se viene specificato né globali o locali, il valore predefinito è controllato dall'impostazione del **predefinito fino al cursore locale** opzione di database.  
  
 FORWARD_ONLY  
 Specifica che è possibile scorrere il cursore solo dalla prima all'ultima riga. FETCH NEXT è l'unica opzione dell'istruzione FETCH supportata. Se si specifica l'opzione FORWARD_ONLY senza la parola chiave STATIC, KEYSET o DYNAMIC, il cursore sarà un cursore DYNAMIC. Se vengono omesse sia l'opzione FORWARD_ONLY che l'opzione SCROLL, per impostazione predefinita viene utilizzata l'opzione FORWARD_ONLY, a meno che non sia stata specificata la parola chiave STATIC, KEYSET o DYNAMIC. I cursori STATIC, KEYSET e DYNAMIC vengono impostati automaticamente su SCROLL. A differenza delle API del database, ad esempio ODBC e ADO, l'opzione FORWARD_ONLY è supportata con cursori STATIC, KEYSET e DYNAMIC di [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 STATIC  
 Definisce un cursore che crea una copia temporanea dei dati utilizzati dal cursore. Tutte le richieste fino al cursore vengono soddisfatte tramite questa tabella temporanea in **tempdb**; pertanto, le modifiche apportate alle tabelle di base non vengono riflesse nei dati restituiti dalle operazioni di recupero eseguite in questo cursore, e questo non è consentito modifiche.  
  
 KEYSET  
 Specifica che all'apertura del cursore l'appartenenza e l'ordine delle righe nel cursore sono fissi. Il set di chiavi che identifica in modo univoco le righe è incluso in una tabella in **tempdb** noti come il **keyset**.  
  
> [!NOTE]  
>  Se la query fa riferimento ad almeno una tabella priva di indice univoco, il cursore keyset viene convertito in cursore statico.  
  
 Le modifiche a valori non chiave apportate nelle tabelle di base dal proprietario del cursore o confermate tramite commit da altri utenti sono visibili quando il proprietario scorre il cursore. Gli inserimenti eseguiti da altri utenti non sono visibili (tali inserimenti non possono essere eseguiti tramite un cursore [!INCLUDE[tsql](../../includes/tsql-md.md)] del server). Se viene eliminata una riga, un tentativo di recupero della riga restituisce un @@FETCH_STATUS -2. Le operazioni di aggiornamento di valori di chiave dall'esterno del cursore sono simili a un'operazione di eliminazione della riga precedente seguita da un'operazione di inserimento della nuova riga. La riga con i nuovi valori non è visibile e i tentativi di recupero della riga contenente i vecchi valori restituiscono un @@FETCH_STATUS -2. I nuovi valori sono visibili se l'aggiornamento viene effettuato tramite il cursore con l'aggiunta della clausola WHERE CURRENT OF.  
  
 DYNAMIC  
 Definisce un cursore in cui, durante lo scorrimento, vengono riportate tutte le modifiche ai dati apportate alle righe nel set di risultati. I valori dei dati, l'ordine e l'appartenenza delle righe possono cambiare a ogni operazione di recupero. L'opzione ABSOLUTE dell'istruzione FETCH non è supportata con cursori dinamici.  
  
 FAST_FORWARD  
 Specifica un cursore FORWARD_ONLY, READ_ONLY per il quale sono abilitate le ottimizzazioni delle prestazioni. Non è possibile specificare l'opzione FAST_FORWARD se è stata specificata l'opzione SCROLL o FOR_UPDATE.  
  
> [!NOTE]  
>  FAST_FORWARD e FORWARD_ONLY possono essere entrambe utilizzate nella stessa istruzione DECLARE CURSOR.  
  
 READ_ONLY  
 Impedisce gli aggiornamenti eseguiti tramite il cursore. Non è possibile fare riferimento al cursore in una clausola WHERE CURRENT OF di un'istruzione UPDATE o DELETE. Questa opzione è prioritaria rispetto alla funzionalità di aggiornamento predefinita di un cursore.  
  
 SCROLL_LOCKS  
 Specifica che gli aggiornamenti o le eliminazioni posizionate eseguite tramite il cursore avranno esito positivo. Durante la lettura nel cursore [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] blocca le righe in modo che siano disponibili per modifiche successive. Non è possibile specificare l'opzione SCROLL_LOCKS se è stata specificata l'opzione FAST_FORWARD o STATIC.  
  
 OPTIMISTIC  
 Specifica che gli aggiornamenti o le eliminazioni posizionate eseguite tramite il cursore non avranno esito positivo se la riga ha subito un aggiornamento dopo la lettura nel cursore. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non blocca le righe man mano che vengono lette nel cursore. Vengono invece eseguiti i confronti di **timestamp** i valori di colonna o un valore di checksum se la tabella non contiene **timestamp** colonna, per determinare se la riga è stata modificata dopo la lettura nel cursore. Se la riga è stata modificata, i tentativi di eseguire un aggiornamento o un'eliminazione posizionata hanno esito negativo. Non è possibile specificare l'opzione OPTIMISTIC se è specificata l'opzione FAST_FORWARD.  
  
 TYPE_WARNING  
 Specifica che deve essere inviato un messaggio di avviso al client quando il cursore viene convertito in modo implicito dal tipo richiesto in un altro tipo.  
  
 *select_statement*  
 Istruzione SELECT standard che definisce il set di risultati del cursore. Le parole chiave COMPUTE, COMPUTE BY, FOR BROWSE e INTO non sono consentite all'interno di *select_statement* di una dichiarazione di cursore.  
  
> [!NOTE]  
>  È possibile utilizzare un hint per la query all'interno di una dichiarazione di cursore. Tuttavia, se si utilizza anche la clausola FOR UPDATE OF, specificare l'opzione (*query_hint*) dopo FOR UPDATE OF.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Converte in modo implicito il cursore in un altro tipo, se le clausole in *select_statement* conflitto con la funzionalità del tipo di cursore richiesto. Per ulteriori informazioni, vedere l'argomento relativo alla conversione implicita dei cursori.  
  
 PER l'aggiornamento [OF *column_name* [**,**... *n*]]  
 Definisce le colonne aggiornabili nel cursore. Se viene specificato OF *column_name* [**,**...  *n* ] viene fornito, solo le colonne elencate è possibile apportare modifiche. Se l'istruzione UPDATE viene specificata senza un elenco di colonne, è possibile aggiornare tutte le colonne, a meno che non sia stata specificata l'opzione opposta READ_ONLY.  
  
## <a name="remarks"></a>Osservazioni  
 L'istruzione DECLARE CURSOR definisce gli attributi di un cursore del server [!INCLUDE[tsql](../../includes/tsql-md.md)], ad esempio lo scorrimento e la query utilizzata per compilare il set di risultati su cui agisce il cursore. L'istruzione OPEN esegue il popolamento del set di risultati e l'istruzione FETCH restituisce una riga dal set di risultati. L'istruzione CLOSE rilascia il set di risultati corrente associato al cursore. L'istruzione DEALLOCATE rilascia le risorse utilizzate dal cursore.  
  
 Nella prima forma dell'istruzione DECLARE CURSOR viene utilizzata la sintassi ISO per dichiarare il funzionamento del cursore. Nella seconda forma dell'istruzione vengono utilizzate le estensioni di [!INCLUDE[tsql](../../includes/tsql-md.md)] che consentono di definire i cursori in base allo stesso tipo di cursore utilizzato nelle funzioni di cursore delle API del database ODBC o ADO.  
  
 Non è possibile combinare le due forme dell'istruzione. Se si specifica il SCROLL o INSENSITIVE prima della parola chiave CURSOR, è possibile utilizzare le parole chiave tra il cursore e per *select_statement* parole chiave. Se si specifica delle parole chiave tra il cursore e per *select_statement* parole chiave, è possibile specificare SCROLL o INSENSITIVE prima della parola chiave CURSOR.  
  
 Se in un'istruzione DECLARE CURSOR basata sulla sintassi [!INCLUDE[tsql](../../includes/tsql-md.md)] viene omessa l'opzione READ_ONLY, OPTIMISTIC o SCROLL_LOCKS, per impostazione predefinita i cursori vengono impostati come descritto di seguito:  
  
-   Se l'istruzione SELECT non supporta aggiornamenti (autorizzazioni insufficienti, accesso a tabelle remote che non supportano aggiornamenti e così via), il cursore viene impostato come READ_ONLY.  
  
-   I cursori STATIC e FAST_FORWARD vengono impostati automaticamente come cursori READ_ONLY.  
  
-   I cursori DYNAMIC e KEYSET vengono impostati automaticamente come cursori OPTIMISTIC.  
  
 È possibile fare riferimento a nomi di cursore solo tramite altre istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)]. Non è possibile fare riferimento ai nomi di cursore con funzioni API del database. Dopo la dichiarazione del cursore, ad esempio, non è possibile fare riferimento al nome del cursore tramite le funzioni o i metodi di OLE DB, ODBC o ADO. Le righe del cursore non possono essere recuperate tramite le funzioni o i metodi di recupero API, ma solo utilizzando istruzioni FETCH [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Dopo la dichiarazione di un cursore è possibile eseguire le stored procedure di sistema seguenti per determinare le caratteristiche del cursore.  
  
|Stored procedure di sistema|Description|  
|------------------------------|-----------------|  
|**sp_cursor_list**|Restituisce l'elenco dei cursori visibili nella connessione e gli attributi corrispondenti.|  
|**sp_describe_cursor**|Descrive gli attributi di un cursore, ad esempio se si tratta di un cursore forward-only o scorrevole.|  
|**sp_describe_cursor_columns**|Descrive gli attributi delle colonne nel set di risultati del cursore.|  
|**sp_describe_cursor_tables**|Descrive le tabelle di base a cui ha avuto accesso il cursore.|  
  
 Le variabili possono essere utilizzate come parte di *select_statement* che dichiara un cursore. Dopo la dichiarazione di un cursore i valori delle variabili di cursore non cambiano.  
  
## <a name="permissions"></a>Autorizzazioni  
 Le autorizzazioni per l'istruzione DECLARE CURSOR vengono assegnate per impostazione predefinita a qualsiasi utente che dispone di autorizzazioni per l'istruzione SELECT nelle viste, tabelle e colonne utilizzate nel cursore.
 
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni

È possibile utilizzare i cursori o trigger in una tabella con un indice columnstore cluster. Questa restrizione non si applica agli indici columnstore non cluster; è possibile utilizzare i cursori e il trigger in una tabella con un indice columnstore non cluster. 
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-simple-cursor-and-syntax"></a>A. Utilizzo di una semplice sintassi per la definizione di un cursore  

Il set di risultati generato all'apertura del cursore include tutte le righe e le colonne della tabella. Questo cursore può essere aggiornato e tutti gli aggiornamenti e le eliminazioni sono rappresentati nei recuperi eseguiti su questo cursore. `FETCH NEXT` è l'unica operazione di recupero disponibile perché l'opzione `SCROLL` non è stata specificata.  

  
```  
DECLARE vend_cursor CURSOR  
    FOR SELECT * FROM Purchasing.Vendor  
OPEN vend_cursor  
FETCH NEXT FROM vend_cursor;  
```  
  
### <a name="b-using-nested-cursors-to-produce-report-output"></a>B. Utilizzo di cursori annidati per la generazione di report  
 Nell'esempio seguente viene illustrato in che modo è possibile nidificare i cursori per generare report complessi. Il cursore interno viene dichiarato per ogni fornitore.  
  
```  
SET NOCOUNT ON;  
  
DECLARE @vendor_id int, @vendor_name nvarchar(50),  
    @message varchar(80), @product nvarchar(50);  
  
PRINT '-------- Vendor Products Report --------';  
  
DECLARE vendor_cursor CURSOR FOR   
SELECT VendorID, Name  
FROM Purchasing.Vendor  
WHERE PreferredVendorStatus = 1  
ORDER BY VendorID;  
  
OPEN vendor_cursor  
  
FETCH NEXT FROM vendor_cursor   
INTO @vendor_id, @vendor_name  
  
WHILE @@FETCH_STATUS = 0  
BEGIN  
    PRINT ' '  
    SELECT @message = '----- Products From Vendor: ' +   
        @vendor_name  
  
    PRINT @message  
  
    -- Declare an inner cursor based     
    -- on vendor_id from the outer cursor.  
  
    DECLARE product_cursor CURSOR FOR   
    SELECT v.Name  
    FROM Purchasing.ProductVendor pv, Production.Product v  
    WHERE pv.ProductID = v.ProductID AND  
    pv.VendorID = @vendor_id  -- Variable value from the outer cursor  
  
    OPEN product_cursor  
    FETCH NEXT FROM product_cursor INTO @product  
  
    IF @@FETCH_STATUS <> 0   
        PRINT '         <<None>>'       
  
    WHILE @@FETCH_STATUS = 0  
    BEGIN  
  
        SELECT @message = '         ' + @product  
        PRINT @message  
        FETCH NEXT FROM product_cursor INTO @product  
        END  
  
    CLOSE product_cursor  
    DEALLOCATE product_cursor  
        -- Get the next vendor.  
    FETCH NEXT FROM vendor_cursor   
    INTO @vendor_id, @vendor_name  
END   
CLOSE vendor_cursor;  
DEALLOCATE vendor_cursor;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [@@FETCH_STATUS &#40;Transact-SQL&#41;](../../t-sql/functions/fetch-status-transact-sql.md)   
 [CLOSE &#40;Transact-SQL&#41;](../../t-sql/language-elements/close-transact-sql.md)   
 [Cursori &#40;Transact-SQL&#41;](../../t-sql/language-elements/cursors-transact-sql.md)   
 [DEALLOCATE &#40;Transact-SQL&#41;](../../t-sql/language-elements/deallocate-transact-sql.md)   
 [FETCH &#40;Transact-SQL&#41;](../../t-sql/language-elements/fetch-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
