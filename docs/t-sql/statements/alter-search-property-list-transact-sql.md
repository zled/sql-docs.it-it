---
title: ALTER SEARCH PROPERTY LIST (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/10/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ALTER_SEARCH_PROPERTY_TSQL
- ALTER_SEARCH_PROPERTY_LIST_TSQL
- ALTER SEARCH PROPERTY LIST
- ALTER SEARCH PROPERTY
- ALTER_SEARCH_TSQL
- ALTER SEARCH
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], search property lists
- search property lists [SQL Server], altering
- ALTER SEARCH PROPERTY LIST statement
ms.assetid: 0436e4a8-ca26-4d23-93f1-e31e2a1c8bfb
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 652603c40a2d38381441ea27e96e9b22525ea969
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47708919"
---
# <a name="alter-search-property-list-transact-sql"></a>ALTER SEARCH PROPERTY LIST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Aggiunge una proprietà di ricerca specificata o la elimina dall'elenco delle proprietà di ricerca specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
ALTER SEARCH PROPERTY LIST list_name  
{  
   ADD 'property_name'  
     WITH   
      (   
          PROPERTY_SET_GUID = 'property_set_guid'  
        , PROPERTY_INT_ID = property_int_id  
      [ , PROPERTY_DESCRIPTION = 'property_description' ]  
      )  
 | DROP 'property_name'   
}  
;  
```  
  
## <a name="arguments"></a>Argomenti  
 *list_name*  
 Nome dell'elenco di proprietà da modificare. *list_name* is an identifier.  
  
 Per visualizzare i nomi degli elenchi delle proprietà esistenti, usare la vista del catalogo [sys.registered_search_property_lists](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md), come illustrato di seguito:  
  
```  
SELECT name FROM sys.registered_search_property_lists;  
```  
  
 ADD  
 Aggiunge una proprietà di ricerca specificata all'elenco delle proprietà specificato da *list_name*. La proprietà è registrata per l'elenco delle proprietà di ricerca. Prima di utilizzare le proprietà appena aggiunte per la ricerca di proprietà, è necessario ripopolare l'indice o gli indici full-text associati. Per altre informazioni, vedere [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md).  
  
> [!NOTE]  
>  Per aggiungere una proprietà di ricerca specificata a un elenco delle proprietà di ricerca, è necessario specificare i relativi GUID del set di proprietà (*property_set_guid*) e ID int della proprietà (*property_int_id*). Per ulteriori informazioni, vedere Acquisizione di identificatori e GUID del set di proprietà" più avanti in questo argomento.  
  
 *property_name*  
 Specifica il nome da utilizzare per identificare la proprietà nelle query full-text. *property_name* deve identificare in modo univoco la proprietà all'interno del set di proprietà. Un nome di proprietà può contenere spazi interni. La lunghezza massima consentita per *property_name* è 256 caratteri. Questo nome può essere un nome descrittivo, ad esempio Autore o Indirizzo abitazione, oppure il nome canonico Windows della proprietà, ad esempio **System.Author** o **System.Contact.HomeAddress**.  
  
 Gli sviluppatori devono usare il valore specificato per *property_name* per identificare la proprietà nel predicato [CONTAINS](../../t-sql/queries/contains-transact-sql.md). Quando si aggiunge una proprietà è quindi importante specificare un valore che rappresenti in modo significativo la proprietà definita dal GUID del set di proprietà specificato (*property_set_guid*) e l'identificatore della proprietà (*property_int_id*). Per ulteriori informazioni sui nomi di proprietà, vedere la sezione "Osservazioni" più avanti in questo argomento.  
  
 Per visualizzare i nomi di proprietà attualmente presenti in un elenco delle proprietà di ricerca del database corrente, usare la vista del catalogo [sys.registered_search_properties](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md) come illustrato di seguito:  
  
```  
SELECT property_name FROM sys.registered_search_properties;  
```  
  
 PROPERTY_SET_GUID ='*property_set_guid*'  
 Specifica l'identificatore del set di proprietà a cui appartiene la proprietà. Si tratta di un identificatore univoco globale (GUID, Globally Unique Identifier). Per informazioni sull'acquisizione di questo valore, vedere la sezione "Osservazioni" più avanti in questo argomento.  
  
 Per visualizzare il GUID del set di proprietà di qualsiasi proprietà presente in un elenco delle proprietà di ricerca del database corrente, usare la vista del catalogo [sys.registered_search_properties](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md), come illustrato di seguito:  
  
```  
SELECT property_set_guid FROM sys.registered_search_properties;  
```  
  
 PROPERTY_INT_ID =*property_int_id*  
 Specifica il numero intero che identifica la proprietà all'interno del set di proprietà. Per informazioni sull'acquisizione di questo valore, vedere la sezione "Osservazioni".  
  
 Per visualizzare l'identificatore dell'intero di qualsiasi proprietà presente in un elenco delle proprietà di ricerca del database corrente, usare la vista del catalogo [sys.registered_search_properties](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md), come illustrato di seguito:  
  
```  
SELECT property_int_id FROM sys.registered_search_properties;  
```  
  
> [!NOTE]  
>  Una determinata combinazione di *property_set_guid* e *property_int_id* deve essere univoca in un elenco di proprietà di ricerca specificato. Se si tenta di aggiungere una combinazione esistente, l'operazione ALTER SEARCH PROPERTY ha esito negativo e viene restituito un errore. Ciò significa che è possibile definire un solo nome per una proprietà specificata.  
  
 PROPERTY_DESCRIPTION ='*property_description*'  
 Specifica una descrizione della proprietà definita dall'utente. *property_description* è una stringa composta da un massimo di 512 caratteri. Questa opzione è facoltativa.  
  
 DROP  
 Elimina la proprietà specificata dall'elenco delle proprietà specificato da *list_name*. L'eliminazione di una proprietà ne annulla la registrazione, pertanto non è più possibile effettuare ricerche che la riguardino.  
  
## <a name="remarks"></a>Remarks  
 Ogni indice full-text può disporre di un solo elenco delle proprietà di ricerca.  
  
 Per consentire l'esecuzione di query su una proprietà di ricerca specificata, è necessario aggiungerla all'elenco delle proprietà di ricerca dell'indice full-text, quindi ripopolare l'indice.  
  
 Quando si specifica una proprietà è possibile disporre le clausole PROPERTY_SET_GUID, PROPERTY_INT_ID e PROPERTY_DESCRIPTION in qualsiasi ordine, come elenco delimitato da virgole tra parentesi, ad esempio:  
  
```  
ALTER SEARCH PROPERTY LIST CVitaProperties  
ADD 'System.Author'   
WITH (   
      PROPERTY_DESCRIPTION = 'Author or authors of a given document.',  
      PROPERTY_SET_GUID   = 'F29F85E0-4FF9-1068-AB91-08002B27B3D9',   
      PROPERTY_INT_ID = 4   
      );  
```  
  
> [!NOTE]  
>  In questo esempio viene utilizzato il nome della proprietà, `System.Author`, che è simile al concetto dei nomi di proprietà canonici introdotti in Windows Vista (nome canonico di Windows).  
  
## <a name="obtaining-property-values"></a>Acquisizione dei valori delle proprietà  
 La ricerca full-text esegue il mapping di una proprietà di ricerca a un indice full-text tramite il GUID del relativo set di proprietà e l'ID di tipo integer della proprietà. Per informazioni su come ottenere questi valori per le proprietà definite da Microsoft, vedere [Trovare GUID del set di proprietà e ID di tipo integer delle proprietà per le proprietà di ricerca](../../relational-databases/search/find-property-set-guids-and-property-integer-ids-for-search-properties.md). Per informazioni sulle proprietà definite da un fornitore di software indipendente (ISV, Independent Software Vendor), vedere la documentazione di tale fornitore.  
  
## <a name="making-added-properties-searchable"></a>Ricerca delle proprietà aggiunte  
 L'aggiunta di una proprietà di ricerca a un elenco delle proprietà di ricerca ne comporta la registrazione. È possibile specificare immediatamente nelle query [CONTAINS](../../t-sql/queries/contains-transact-sql.md) una proprietà appena aggiunta. Tuttavia, le query full-text con ambito proprietà su una proprietà appena aggiunta non restituiscono documenti finché l'indice full-text associato non viene ripopolato. Ad esempio, la query con ambito proprietà seguente eseguita su una proprietà appena aggiunta, *new_search_property*, non restituisce documenti finché l'indice full-text associato alla tabella di destinazione (*table_name*) non viene ripopolato:  
  
```  
SELECT column_name  
FROM table_name  
WHERE CONTAINS( PROPERTY( column_name, 'new_search_property' ), 
               'contains_search_condition');  
GO   
```  
  
 Per avviare un popolamento completo, usare l'istruzione [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41; ](../../t-sql/statements/alter-fulltext-index-transact-sql.md) seguente:  
  
```  
USE database_name;  
GO  
ALTER FULLTEXT INDEX ON table_name START FULL POPULATION;  
GO  
```  
  
> [!NOTE]  
>  Il ripopolamento non è necessario dopo l'eliminazione di una proprietà da un elenco di proprietà, perché solo le proprietà che rimangono nell'elenco delle proprietà di ricerca sono disponibili per le query full-text.  
  
## <a name="related-references"></a>Riferimenti correlati  
 **Per creare un elenco di proprietà**  
  
-   [CREATE SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](../../t-sql/statements/create-search-property-list-transact-sql.md)  
  
 **Per eliminare un elenco di proprietà**  
  
-   [DROP SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](../../t-sql/statements/drop-search-property-list-transact-sql.md)  
  
 **Per aggiungere o rimuovere un elenco di proprietà in un indice full-text**  
  
-   [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md)  
  
 **Per eseguire un popolamento in un indice full-text**  
  
-   [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md)  
  
##  <a name="Permissions"></a> Permissions  
 È necessario disporre dell'autorizzazione CONTROL per l'elenco di proprietà.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-adding-a-property"></a>A. Aggiunta di una proprietà  
 Nell'esempio seguente vengono aggiunte diverse proprietà (`Title`, `Author` e `Tags`) a un elenco delle proprietà denominato `DocumentPropertyList`.  
  
> [!NOTE]  
>  Per un esempio in cui viene creato l'elenco di proprietà `DocumentPropertyList`, vedere [CREATE SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](../../t-sql/statements/create-search-property-list-transact-sql.md).  
  
```  
ALTER SEARCH PROPERTY LIST DocumentPropertyList  
   ADD 'Title'   
   WITH ( PROPERTY_SET_GUID = 'F29F85E0-4FF9-1068-AB91-08002B27B3D9', PROPERTY_INT_ID = 2,   
      PROPERTY_DESCRIPTION = 'System.Title - Title of the item.' );  
  
ALTER SEARCH PROPERTY LIST DocumentPropertyList   
    ADD 'Author'  
   WITH ( PROPERTY_SET_GUID = 'F29F85E0-4FF9-1068-AB91-08002B27B3D9', PROPERTY_INT_ID = 4,   
      PROPERTY_DESCRIPTION = 'System.Author - Author or authors of the item.' );  
  
ALTER SEARCH PROPERTY LIST DocumentPropertyList   
    ADD 'Tags'  
   WITH ( PROPERTY_SET_GUID = 'F29F85E0-4FF9-1068-AB91-08002B27B3D9', PROPERTY_INT_ID = 5,   
      PROPERTY_DESCRIPTION = 
          'System.Keywords - Set of keywords (also known as tags) assigned to the item.' );  
```  
  
> [!NOTE]  
>  È necessario associare un elenco delle proprietà di ricerca specificato a un indice full-text prima di utilizzarlo per query con ambito proprietà. A tale scopo, usare un'istruzione [ALTER FULLTEXT INDEX](../../t-sql/statements/alter-fulltext-index-transact-sql.md) e specificare la clausola SET SEARCH PROPERTY LIST.  
  
### <a name="b-dropping-a-property"></a>B. Eliminazione di una proprietà  
 Nell'esempio seguente viene eliminata la proprietà `Comments` dall'elenco delle proprietà `DocumentPropertyList`.  
  
```  
ALTER SEARCH PROPERTY LIST DocumentPropertyList  
DROP 'Comments' ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](../../t-sql/statements/create-search-property-list-transact-sql.md)   
 [DROP SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](../../t-sql/statements/drop-search-property-list-transact-sql.md)   
 [sys.registered_search_properties &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md)   
 [sys.registered_search_property_lists &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)   
 [sys.dm_fts_index_keywords_by_property &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-property-transact-sql.md)   
 [Eseguire ricerche nelle proprietà dei documenti con elenchi delle proprietà di ricerca](../../relational-databases/search/search-document-properties-with-search-property-lists.md)   
 [Trovare GUID del set di proprietà e ID di tipo integer delle proprietà per le proprietà di ricerca](../../relational-databases/search/find-property-set-guids-and-property-integer-ids-for-search-properties.md)  
  
  
