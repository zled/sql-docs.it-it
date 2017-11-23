---
title: CREARE una funzione (SQL Data Warehouse) | Documenti Microsoft
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 8cad1b2c-5ea0-4001-9060-2f6832ccd057
caps.latest.revision: "14"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 69f4f470cf049deb3ce3b38a2bcb75f37265b31b
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="create-function-sql-data-warehouse"></a>CREARE una funzione (SQL Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Consente di creare una funzione definita dall'utente in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Una funzione definita dall'utente è un [!INCLUDE[tsql](../../includes/tsql-md.md)] routine che accetta parametri, esegue un'azione, ad esempio un calcolo complesso e restituisce il risultato dell'azione come valore. Il valore restituito deve essere un valore scalare (singolo). Utilizzare questa istruzione per creare una routine riutilizzabile che può essere utilizzata in queste modalità:  
  
-   Nelle istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)], ad esempio SELECT.  
  
-   Nelle applicazioni che chiamano la funzione.  
  
-   Nella definizione di un'altra funzione definita dall'utente.  
  
-   Per definire un vincolo CHECK su una colonna.  
  
-   Per sostituire una stored procedure.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
--Transact-SQL Scalar Function Syntax  
CREATE FUNCTION [ schema_name. ] function_name   
( [ { @parameter_name [ AS ] parameter_data_type   
    [ = default ] }   
    [ ,...n ]  
  ]  
)  
RETURNS return_data_type  
    [ WITH <function_option> [ ,...n ] ]  
    [ AS ]  
    BEGIN   
        function_body   
        RETURN scalar_expression  
    END  
[ ; ]  
  
<function_option>::=   
{  
    [ SCHEMABINDING ]  
  | [ RETURNS NULL ON NULL INPUT | CALLED ON NULL INPUT ]  
}  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *schema_name*  
 Nome dello schema a cui appartiene la funzione definita dall'utente.  
  
 *nome_funzione*  
 Nome della funzione definita dall'utente. Nomi di funzione devono essere conformi alle regole per gli identificatori e devono essere univoci all'interno del database e al relativo schema.  
  
> [!NOTE]  
>  È necessario apporre le parentesi dopo il nome della funzione anche se non viene specificato alcun parametro.  
  
 @*parameter_name*  
 Parametro della funzione definita dall'utente. È possibile dichiarare uno o più parametri.  
  
 Una funzione può avere al massimo 2.100 parametri. Il valore di ciascun parametro dichiarato deve essere specificato dall'utente quando viene eseguita la funzione, a meno che non venga definito un valore predefinito per tale parametro.  
  
 Specificare un nome di parametro utilizzando come primo carattere il simbolo di chiocciola (@). I nomi di parametro devono essere conformi alle regole per gli identificatori. I parametri sono locali rispetto alla funzione. È pertanto possibile utilizzare gli stessi nomi di parametro in altre funzioni. I parametri possono rappresentare solo costanti, non nomi di tabella, di colonna o di altri oggetti di database.  
  
> [!NOTE]  
>  ANSI_WARNINGS non viene applicata quando vengono passati parametri a una stored procedure, una funzione definita dall'utente oppure in caso di dichiarazione e impostazione delle variabili in un'istruzione batch. Ad esempio, se una variabile viene definita come **char (3)**e quindi impostato su un valore maggiore di tre caratteri, i dati vengono troncati alla dimensione definita e l'inserimento o aggiornamento istruzione ha esito positivo.  
  
 *parameter_data_type*  
 È il tipo di dati del parametro. Per [!INCLUDE[tsql](../../includes/tsql-md.md)] funzioni, tutti i tipi di dati scalari supportati [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] sono consentiti. Il tipo di dati timestamp (rowversion) non è un tipo supportato.  
  
 [=*predefinito* ]  
 Valore predefinito del parametro. Se un *predefinito* valore è definito, la funzione può essere eseguita senza specificare un valore per tale parametro.  
  
 Se a un parametro della funzione è associato un valore predefinito, alla chiamata della funzione è necessario specificare la parola chiave DEFAULT per recuperare il valore predefinito. Questo comportamento risulta diverso dall'utilizzo di parametri con valore predefinito nelle stored procedure in cui l'omissione del parametro implica l'utilizzo del valore predefinito.  
  
 *return_data_type*  
 Valore restituito di una funzione scalare definita dall'utente. Per [!INCLUDE[tsql](../../includes/tsql-md.md)] funzioni, tutti i tipi di dati scalari supportati [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] sono consentiti. Il tipo di dati timestamp (rowversion) non è un tipo supportato. I tipi non scalari cursore e la tabella non sono consentiti.  
  
 *function_body*  
 Serie di [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzioni.  Il function_body non può contenere un'istruzione SELECT e non può fare riferimento a dati del database.  Il function_body non può fare riferimento a tabelle o viste. Il corpo della funzione può chiamare altre funzioni deterministiche, ma non è possibile chiamare funzioni non deterministiche. 
  
 Nelle funzioni scalari, *function_body* è una serie di [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzioni che in combinazione restituiscono un valore scalare.  
  
 *scalar_expression*  
 Specifica il valore scalare restituito dalla funzione scalare.  
  
 **\<function_option >:: =** 
  
 Specifica che la funzione includerà una o più delle opzioni seguenti.  
  
 SCHEMABINDING  
 Specifica che la funzione è associata agli oggetti di database a cui fa riferimento. Quando la clausola SCHEMABINDING viene specificata, non è possibile apportare agli oggetti di base modifiche che hanno effetto sulla definizione della funzione. È necessario prima modificare o eliminare la definizione della funzione per rimuovere le dipendenze dall'oggetto da modificare.  
  
 L'associazione della funzione agli oggetti cui fa riferimento viene rimossa solo quando viene eseguita una delle azioni seguenti:  
  
-   La funzione viene eliminata.  
  
-   La funzione viene modificata tramite l'istruzione ALTER senza specificare l'opzione SCHEMABINDING.  
  
 Una funzione può essere associata a uno schema solo se vengono soddisfatte le condizioni seguenti:  
  
-   Funzioni definite dall'utente a cui fa riferimento la funzione sono anche associati a schema.  
  
-   Le funzioni e altre funzioni definite dall'utente a cui fa riferimento la funzione viene fatto riferimento utilizzando un nome di uno o due parti.  
  
-   Le funzioni predefinite e altre funzioni definite dall'utente nello stesso database possono fare riferimento solo all'interno del corpo di funzioni definite dall'utente.  
  
-   L'utente che ha eseguito l'istruzione CREATE FUNCTION dispone dell'autorizzazione REFERENCES per gli oggetti di database a cui la funzione fa riferimento.  
  
 Per rimuovere SCHEMABINDING utilizzare ALTER  
  
 RESTITUISCE NULL NELL'INPUT NULL | **CHIAMATO SU UN INPUT NULL**  
 Specifica il **OnNULLCall** attributo di una funzione a valori scalari. Se omesso, viene utilizzata l'opzione CALLED ON NULL INPUT per impostazione predefinita. Ciò significa che viene eseguito il corpo della funzione anche se come argomento viene passato NULL.  
  
## <a name="best-practices"></a>Procedure consigliate  
 Se una funzione definita dall'utente non viene creata tramite la clausola SCHEMABINDING, le modifiche apportate agli oggetti sottostanti possono influire sulla definizione della funzione e produrre risultati imprevisti quando viene richiamata. È consigliabile implementare uno dei metodi seguenti per assicurarsi che la funzione non diventi obsoleta in seguito a modifiche degli oggetti sottostanti:  
  
-   Specificare la clausola WITH SCHEMABINDING quando si crea la funzione. In questo modo, gli oggetti a cui si fa riferimento nella definizione della funzione possono essere modificati solo se viene modificata anche la funzione.  
  
## <a name="interoperability"></a>Interoperabilità  
 In una funzione le istruzioni seguenti sono valide:  
  
-   Istruzioni di assegnazione.  
  
-   Istruzioni per il controllo di flusso, escluse le istruzioni TRY...CATCH.  
  
-   Istruzioni DECLARE che definiscono le variabili dati locali.  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
 Non è possibile utilizzare funzioni definite dall'utente per eseguire azioni che modificano lo stato del database.  
  
 È possibile nidificare le funzioni definite dall'utente, ovvero una funzione definita dall'utente ne può richiamare un'altra. Il livello di nidificazione aumenta all'avvio della funzione richiamata e diminuisce al termine dell'esecuzione della funzione. Le funzioni definite dall'utente possono essere nidificate fino a un massimo di 32 livelli. Se viene superato il livello massimo di nidificazioni, l'intera sequenza di funzioni chiamanti ha esito negativo.   
  
## <a name="metadata"></a>Metadati  
 Questa sezione elenca le viste del catalogo di sistema che è possibile utilizzare per restituire i metadati relativi a funzioni definite dall'utente.  
  
 [Sys. sql_modules](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md) : Visualizza la definizione di [!INCLUDE[tsql](../../includes/tsql-md.md)] funzioni definite dall'utente. Esempio:  
  
```  
SELECT definition, type   
FROM sys.sql_modules AS m  
JOIN sys.objects AS o   
    ON m.object_id = o.object_id   
    AND type = ('FN');  
GO  
  
```  
  
 [Sys. Parameters](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md) : Visualizza le informazioni sui parametri definiti nelle funzioni definite dall'utente.  
  
 [Sys. sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md) : Visualizza gli oggetti sottostanti a cui fa riferimento una funzione.  
  
## <a name="permissions"></a>Permissions  
 È necessario disporre dell'autorizzazione CREATE FUNCTION nel database e dell'autorizzazione ALTER per lo schema in cui la funzione è in fase di creazione.  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-using-a-scalar-valued-user-defined-function-to-change-a-data-type"></a>A. Utilizzo di una funzione scalare definita dall'utente per modificare un tipo di dati  
 Questa semplice funzione accetta un **int** del tipo di dati come input e restituisce un **10,2** il tipo di dati come output.  
  
```  
CREATE FUNCTION dbo.ConvertInput (@MyValueIn int)  
RETURNS decimal(10,2)  
AS  
BEGIN  
    DECLARE @MyValueOut int;  
    SET @MyValueOut= CAST( @MyValueIn AS decimal(10,2));  
    RETURN(@MyValueOut);  
END;  
GO  
  
SELECT dbo.ConvertInput(15) AS 'ConvertedValue';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER FUNCTION (SQL Server PDW)](http://msdn.microsoft.com/en-us/25ff3798-eb54-4516-9973-d8f707a13f6c)   
 [ELIMINARE la funzione (SQL Server PDW)](http://msdn.microsoft.com/en-us/1792a90d-0d06-4852-9dec-6de1b9cd229e)  
  
  


