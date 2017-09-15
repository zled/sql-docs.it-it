---
title: Selezionare - comando SQL | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- select [ODBC]
ms.assetid: 2149c3ca-3a71-446d-8d53-3d056e2f301a
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3604d435a8a95e3690d335e25e1a94b3bbb0b1a1
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="select---sql-command"></a>Selezionare - comando SQL
Recupera dati da una o più tabelle.  
  
 Il Driver ODBC di Visual FoxPro supporta la sintassi del linguaggio Visual FoxPro native per questo comando. Per informazioni specifiche del driver, vedere **Driver osservazioni**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SELECT [ALL | DISTINCT]  
   [Alias.] Select_Item [AS Column_Name]  
   [, [Alias.] Select_Item [AS Column_Name] ...]   
FROM [DatabaseName!]Table [Local_Alias]  
   [, [DatabaseName!]Table [Local_Alias] ...]   
[WHERE JoinCondition [AND JoinCondition  
…]  
   [AND | OR FilterCondition [AND | OR FilterCondition ...]]]  
[GROUP BY GroupColumn [, GroupColumn ...]]  
[HAVING FilterCondition]  
[UNION [ALL] SELECTCommand]  
[ORDER BY Order_Item [ASC | DESC] [, Order_Item [ASC | DESC] ...]]  
```  
  
## <a name="arguments"></a>Argomenti  
  
> [!NOTE]  
>  Oggetto *sottoquery*, a cui gli argomenti seguenti, è un'istruzione SELECT all'interno di un'istruzione SELECT e devono essere racchiusi tra parentesi. È possibile avere fino a due sottoquery allo stesso livello (non annidati) nella clausola WHERE. (Vedere la sezione degli argomenti). Sottoquery possono contenere più condizioni di join.  
  
 [Tutti &#124; DISTINCT] [*Alias*.] *Select_Item* [AS *Column_Name*] [, [*Alias*.] *Select_Item* [AS *Column_Name*]...]  
 La clausola SELECT specifica i campi, costanti ed espressioni che vengono visualizzate nei risultati della query.  
  
 Per impostazione predefinita, tutti vengono visualizzate tutte le righe nei risultati della query.  
  
 DISTINCT esclude i duplicati di tutte le righe dai risultati della query.  
  
> [!NOTE]  
>  È possibile usare DISTINCT una sola volta per ogni clausola SELECT.  
  
 *Alias*. qualifica i nomi di elemento corrispondenti. Ogni elemento specificato con *Select_Item* genera una colonna dei risultati della query. Se due o più elementi hanno lo stesso nome, includere l'alias di tabella e un periodo prima del nome di elemento per impedire che le colonne viene duplicato.  
  
 *Select_Item* specifica un elemento da includere nei risultati della query. Un elemento può essere uno dei valori seguenti:  
  
-   Il nome di un campo da una tabella nella clausola FROM.  
  
-   Costante che specifica che lo stesso valore di costante deve essere visualizzato in ogni riga dei risultati della query.  
  
-   Un'espressione che può essere il nome di una funzione definita dall'utente.  
  
 **Funzioni definite dall'utente con l'istruzione SELECT**  
  
 Benché l'uso di funzioni definite dall'utente nella clausola SELECT offre evidenti vantaggi, è necessario considerare anche le restrizioni seguenti:  
  
-   La velocità delle operazioni eseguite con l'istruzione SELECT può essere limitata dalla velocità con cui vengono eseguite tali funzioni definite dall'utente. Le modifiche di volume elevato che coinvolgono le funzioni definite dall'utente potrebbero essere effettuate tramite API e funzioni definite dall'utente scritte in linguaggio C o assembly migliore.  
  
-   L'unica modalità affidabile per passare valori alle funzioni definite dall'utente richiamate da selezionare è dall'elenco degli argomenti passato alla funzione quando viene richiamata.  
  
-   Anche se provare e di individuare una modifica apparentemente non consentita che funziona correttamente in una determinata versione di FoxPro, non c'è garanzia che continuano a funzionare nelle versioni successive.  
  
 Oltre a queste restrizioni, funzioni definite dall'utente sono consentite nella clausola SELECT. Tuttavia, tenere presente che l'utilizzo dell'istruzione SELECT può rallentare le prestazioni.  
  
 Le funzioni di campo seguenti sono disponibili per l'utilizzo con un elemento selezionato è un campo o un'espressione che include un campo:  
  
-   AVG (*Select_Item*): calcola la media di una colonna di dati numerici.  
  
-   CONTEGGIO (*Select_Item*), Conta il numero di selezionare gli elementi in una colonna. Count conta il numero di righe nell'output della query.  
  
-   MIN (*Select_Item*), determina il valore minimo di *Select_Item* in una colonna.  
  
-   MAX (*Select_Item*), determina il valore massimo di *Select_Item* in una colonna.  
  
-   SUM (*Select_Item*), ovvero totali delle righe di una colonna di dati numerici.  
  
 È possibile nidificare le funzioni di campo.  
  
 AS *Column_Name*  
 Specifica l'intestazione di una colonna nell'output della query. Questo è utile quando *Select_Item* è un'espressione o contiene un campo (funzione) e si desidera assegnare alla colonna un nome significativo. *Column_Name* può essere un'espressione non può contenere caratteri (ad esempio, spazi) che non sono consentiti nei nomi di campo di tabella.  
  
 DA [*DatabaseName*!] *Tabella* [*Local_Alias*] [, [*DatabaseName*!] *Tabella* [*Local_Alias*]...]  
 Elenca le tabelle che contengono i dati recuperati dalla query. Se nessuna tabella è aperta, Visual FoxPro consente di visualizzare il **aprire** nella finestra di dialogo in modo che è possibile specificare il percorso del file. Dopo che è stato aperto, la tabella rimane aperta dopo la query è stata completata.  
  
 *DatabaseName*! Specifica il nome di un database diverso da quello specificato con l'origine dati. È necessario includere il nome del database che contiene la tabella, se il database non è specificato con l'origine dati. Include il delimitatore punto esclamativo (!) dopo il nome del database e prima del nome di tabella.  
  
 *Local_Alias* specifica un nome temporaneo per la tabella denominata *tabella*. Se si specifica un alias locale, è necessario utilizzare l'alias locale anziché il nome della tabella in tutta l'istruzione SELECT. L'alias locale non incidono sull'ambiente di Visual FoxPro.  
  
 DOVE *JoinCondition* [AND *JoinCondition* ...]    [E &#124; O *FilterCondition* [AND &#124; O *FilterCondition* ...]]  
 Indica di Visual FoxPro da includere solo alcuni record nei risultati della query. In cui è necessario per recuperare dati da più tabelle.  
  
 *Elemento JoinCondition* specifica i campi che si collegano tabelle nella clausola FROM. Se si include più di una tabella in una query, è necessario specificare una condizione di join per ogni tabella dopo il primo.  
  
> [!IMPORTANT]  
>  Quando si crea le condizioni di join, considerare le informazioni seguenti:  
  
-   Se si includono due tabelle in una query e non si specifica una condizione di join, ogni record nella prima tabella fa parte di ogni record nella seconda tabella, purché siano soddisfatte le condizioni di filtro. Una query può produrre risultati di lunga durati.  
  
-   Prestare attenzione quando si uniscono le tabelle con i campi vuoti perché Visual FoxPro coincide con i campi vuoti. Ad esempio, se si partecipa Customer. ZIP e fattura. COMPRIMERE e se cliente che contiene i codici postali zip 100 vuoti e fattura contiene i codici postali zip 400 vuoti, l'output della query contiene 40.000 record supplementari dovuti i campi vuoti. Utilizzare il **(vuoto)** funzione per eliminare i record vuoto dall'output della query.  
  
-   È necessario utilizzare l'operatore AND per la connessione di più condizioni di join. Ogni condizione di join ha il formato seguente:  
  
     *FieldName1 confronto FieldName2*  
  
     *FieldName1* è il nome di un campo da una tabella, *FieldName2* è il nome di un campo da un'altra tabella, e *confronto* è uno degli operatori descritti nella tabella seguente.  
  
|Operatore|Confronto|  
|--------------|----------------|  
|=|Uguale a|  
|==|Esattamente uguale a|  
|LIKE|SQL COME|  
|<>, !=, #|Diverso da|  
|>|Più di|  
|>=|Maggiore o uguale a|  
|<|Minore di|  
|<=|Minore o uguale a|  
  
 Quando si utilizza l'operatore = con stringhe, funziona in modo diverso, a seconda dell'impostazione di SET ANSI. Quando SET ANSI è impostata su OFF, Visual FoxPro considera i confronti di stringhe in modo familiare agli utenti di Xbase. Quando il SET ANSI è impostata su ON, Visual FoxPro segue gli standard ANSI per confronti tra stringhe. Vedere [SET ANSI](../../odbc/microsoft/set-ansi-command.md) e [SET EXACT](../../odbc/microsoft/set-exact-command.md) per ulteriori informazioni sulla modalità di Visual FoxPro esegue confronti tra stringhe.  
  
 *FilterCondition* specifica i criteri che i record devono soddisfare per essere inclusi nei risultati della query. È possibile includere molte condizioni in una query di filtro desiderati, la connessione con l'operatore AND o OR (operatore). È inoltre possibile utilizzare l'operatore NOT per invertire il valore di un'espressione logica, o è possibile utilizzare **(vuoto)** per verificare la presenza di un campo vuoto. *FilterCondition* può accettare uno qualsiasi dei formati negli esempi seguenti:  
  
 **Esempio 1** *FieldName1 confronto FieldName2*  
  
 `customer.cust_id = orders.cust_id`  
  
 **Esempio 2** *espressione di confronto FieldName*  
  
 `payments.amount >= 1000`  
  
 **Esempio 3** *FieldName confronto* tutti (*sottoquery*)  
  
 `company < ALL ;`  
  
 `(SELECT company FROM customer WHERE country = "USA")`  
  
 Quando la condizione di filtro include tutti, il campo deve soddisfare la condizione di confronto per tutti i valori generati dalla sottoquery prima che il record è inclusa nei risultati della query.  
  
 **Esempio 4** *FieldName confronto* qualsiasi &#124; ALCUNI (*sottoquery*)  
  
 `company < ANY ;`  
  
 `(SELECT company FROM customer WHERE country = "USA")`  
  
 Quando la condizione di filtro include una o più, il campo deve soddisfare la condizione di confronto per almeno uno dei valori generati dalla sottoquery.  
  
 Nell'esempio seguente viene verificato se i valori nel campo sono all'interno di un intervallo di valori specificato:  
  
 **Esempio 5** *FieldName* [NOT] BETWEEN *Start_Range* AND *End_Range*  
  
 `customer.postalcode BETWEEN 90000 AND 99999`  
  
 Nell'esempio seguente verifica se almeno una riga soddisfa i criteri nella sottoquery. Quando la condizione di filtro include EXISTS, la condizione di filtro restituisce True (. T.), a meno che la sottoquery restituisce un set vuoto.  
  
 **Esempio 6** [NOT] esiste (*sottoquery*)  
  
 `EXISTS ;`  
  
 `(SELECT * FROM orders WHERE customer.postalcode =`  
  
 `orders.postalcode)`  
  
 **Esempio 7** *FieldName* [NOT] IN *Value_Set*  
  
 `customer.postalcode NOT IN ("98052","98072","98034")`  
  
 Quando la condizione di filtro include IN, il campo deve contenere uno dei valori prima che il record è inclusa nei risultati della query.  
  
 **Esempio 8** *FieldName* [NOT] IN (*sottoquery*)  
  
 `customer.cust_id IN ;`  
  
 `(SELECT orders.cust_id FROM orders WHERE orders.city="Seattle")`  
  
 In questo caso il campo deve contenere uno dei valori restituiti dalla sottoquery prima che il record è inclusa nei risultati della query.  
  
 **Esempio 9** *FieldName* [NOT] LIKE *cExpression*  
  
 `customer.country NOT LIKE "USA"`  
  
 Questa condizione di filtro di ricerca per ogni campo che corrisponde a *cExpression*. È possibile utilizzare il segno di percentuale (%) e caratteri jolly di sottolineatura (_) come parte di *cExpression*. Il carattere di sottolineatura rappresenta un singolo carattere sconosciuto nella stringa.  
  
 Clausola GROUP BY *GroupColumn* [, *GroupColumn* ...]  
 Gruppi di righe nella query in base ai valori in una o più colonne. *GroupColumn* può essere uno dei seguenti:  
  
-   Il nome di un campo di tabella normale.  
  
-   Un campo che include una funzione di campo SQL.  
  
-   Un'espressione numerica che indica la posizione della colonna nella tabella dei risultati. (Il numero di colonna più a sinistra è 1).  
  
 CON *FilterCondition*  
 Specifica una condizione di filtro che gruppi devono soddisfare per essere inclusi nei risultati della query. HAVING deve essere utilizzato con GROUP BY e possono includere molte condizioni di filtro desiderati, connessi tramite l'operatore AND o OR (operatore). È inoltre possibile utilizzare non per invertire il valore di un'espressione logica.  
  
 *FilterCondition* non può contenere una sottoquery.  
  
 Una clausola HAVING senza una clausola GROUP BY si comporta come una clausola WHERE. È possibile utilizzare gli alias locali e funzioni di campi nella clausola HAVING. Utilizzare una clausola WHERE per migliorare le prestazioni se la clausola HAVING non contiene funzioni alcun campo.  
  
 [UNION [ALL] *SELECTCommand*]  
 Combina i risultati finali della selezione di uno con i risultati finali di selezionare un altro. Per impostazione predefinita, un'unione controlla i risultati combinati ed Elimina le righe duplicate. Utilizzare le parentesi per combinare più clausole di unione.  
  
 UNIONE tutti impedisce eliminando le righe duplicate dai risultati combinati.  
  
 Le clausole unione seguire queste regole:  
  
-   È possibile usare UNION per combinare le sottoquery.  
  
-   Entrambi i comandi SELECT devono avere lo stesso numero di colonne nell'output query.  
  
-   Ogni colonna nei risultati della query di uno selezionare deve avere lo stesso tipo di dati e la stessa larghezza della colonna corrispondente in altro selezionare.  
  
-   Solo l'istruzione SELECT finale può avere una clausola ORDER BY, deve fare riferimento alle colonne di output tramite un numero. Se una clausola ORDER BY è inclusa, influisce su risultati completo.  
  
 È inoltre possibile utilizzare la clausola UNION per simulare un outer join.  
  
 Quando si uniscono due tabelle in una query, solo i record con valori corrispondenti nei campi di join sono inclusi nell'output. Se un record nella tabella padre non dispone di un record corrispondente della tabella figlio, il record nella tabella padre non è incluso nell'output. Un outer join consente di includere tutti i record nella tabella padre nell'output, con i record corrispondenti nella tabella figlio. Per creare un outer join in Visual FoxPro, è necessario utilizzare un comando SELECT nidificato, come nell'esempio seguente:  
  
```  
SELECT customer.company, orders.order_id, orders.emp_id ;  
FROM customer, orders ;  
WHERE customer.cust_id = orders.cust_id ;  
UNION ;  
SELECT customer.company, 0, 0 ;  
FROM customer ;  
WHERE customer.cust_id NOT IN ;  
(SELECT orders.cust_id FROM orders)  
```  
  
> [!NOTE]  
>  Assicurarsi di includere lo spazio che precede immediatamente ogni punto e virgola. In caso contrario, si riceverà un errore.  
  
 La sezione del comando prima che la clausola UNION consente di selezionare i record da entrambe le tabelle che dispongono di valori corrispondenti. Le società di clienti che non contengono le fatture associate non sono incluse. La sezione del comando dopo la clausola UNION consente di selezionare i record nella tabella di clienti che non contengono record nella tabella orders corrispondenti.  
  
 Sulla seconda sezione del comando, tenere presente quanto segue:  
  
-   L'istruzione SELECT racchiusa tra parentesi viene elaborata per prima. Questa istruzione crea una selezione di tutti i numeri di cliente nella tabella orders.  
  
-   La clausola WHERE consente di trovare tutti i numeri di cliente nella tabella di clienti che non sono presenti nella tabella orders. Poiché la prima sezione del comando fornito tutte le società che ha un numero cliente nella tabella orders, tutte le società nella tabella customer sono ora inclusi nei risultati della query.  
  
-   Poiché le strutture delle tabelle incluse in un'unione devono essere identiche, esistono due segnaposto nella seconda istruzione SELECT per rappresentare *orders.order_id* e *orders.emp_id* dalla prima istruzione SELECT istruzione.  
  
    > [!NOTE]  
    >  I segnaposto devono essere dello stesso tipo dei campi che rappresentano. Se il campo è di tipo data, il segnaposto deve essere {/ /}. Se il campo è un campo di tipo carattere, il segnaposto deve essere una stringa vuota ("").  
  
 ORDER BY *Order_Item* [ASC &#124; DESC] [, *Order_Item* [ASC &#124; DESC]...]  
 Ordina i risultati della query in base ai dati in una o più colonne. Ogni *Order_Item* deve corrispondere a una colonna nei risultati della query e può essere uno dei seguenti:  
  
-   Un campo in una tabella da che è anche un elemento select nella clausola SELECT principale (non in una sottoquery).  
  
-   Un'espressione numerica che indica la posizione della colonna nella tabella dei risultati. (La colonna più a sinistra è il numerica 1.)  
  
 ASC specifica un ordine crescente dei risultati della query, in base a ordine degli elementi ed è il valore predefinito per ORDER BY.  
  
 DESC consente di specificare un ordine decrescente dei risultati della query.  
  
 Risultati della query vengono visualizzati non ordinati, se non si specifica un ordine con ORDER BY.  
  
## <a name="remarks"></a>Osservazioni  
 Selezionare è un comando SQL compilato in Visual FoxPro come qualsiasi altro comando di Visual FoxPro. Quando si utilizzano selezionare da costituire una query, Visual FoxPro interpreta la query e recupera i dati specificati dalle tabelle. È possibile creare una query di selezione dalla finestra del prompt dei comandi o da un programma Visual FoxPro (come con qualsiasi altro comando di Visual FoxPro).  
  
> [!NOTE]  
>  Selezionare non rispetta la condizione di filtro corrente specificata con filtro impostato.  
  
## <a name="driver-remarks"></a>Sezione Osservazioni di driver  
 Quando l'applicazione invia l'istruzione ODBC SQL SELECT all'origine dati, il Driver ODBC di Visual FoxPro converte il comando al comando di Visual FoxPro selezionare senza conversione, a meno che il comando contiene una sequenza di escape ODBC. Sintassi di Visual FoxPro vengono convertiti gli elementi racchiusi tra una sequenza di escape ODBC. Per ulteriori informazioni sull'utilizzo di ODBC sequenze di escape, vedere [funzioni di data e ora](../../odbc/microsoft/time-and-date-functions-visual-foxpro-odbc-driver.md) e nel *riferimento per programmatori di Microsoft ODBC*, vedere [sequenze di Escape ODBC](../../odbc/reference/develop-app/escape-sequences-in-odbc.md) .  
  
## <a name="see-also"></a>Vedere anche  
 [CREA TABELLA - SQL](../../odbc/microsoft/create-table-sql-command.md)   
 [INSERT - SQL](../../odbc/microsoft/insert-sql-command.md)   
 [SET ANSI](../../odbc/microsoft/set-ansi-command.md)   
 [SET ESATTO](../../odbc/microsoft/set-exact-command.md)
