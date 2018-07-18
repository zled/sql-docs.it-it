---
title: sp_OAMethod (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_OAMethod
- sp_OAMethod_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_OAMethod
ms.assetid: 1dfaebe2-c7cf-4041-a586-5d04faf2e25e
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: ef5d79a14aaee0b8f23738c3e359e37032d80318
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="spoamethod-transact-sql"></a>sp_OAMethod (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Chiama un metodo di un oggetto OLE.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_OAMethod objecttoken , methodname  
    [ , returnvalue OUTPUT ]   
    [ , [ @parametername = ] parameter [ OUTPUT ] [ ...n ] ]   
```  
  
## <a name="arguments"></a>Argomenti  
 *vengono restituite le*  
 È il token di oggetto di un oggetto OLE creato in precedenza tramite **sp_OACreate**.  
  
 *NomeMetodo*  
 Nome del metodo dell'oggetto OLE da chiamare.  
  
 *ReturnValue***OUTPUT**  
 Valore restituito del metodo dell'oggetto OLE. Se specificato, deve essere una variabile locale del tipo di dati appropriato.  
  
 Se il metodo restituisce un valore singolo, specificare una variabile locale per *returnvalue*, che restituisce il metodo restituisce un valore nella variabile locale o non si specifica *returnvalue*, che restituisce il metodo valore restituito al client come set di risultati a colonna singola e una sola riga.  
  
 Se il metodo restituisce il valore è un oggetto OLE, *returnvalue* deve essere una variabile locale di tipo di dati **int**. Nella variabile locale viene archiviato un token di oggetto utilizzabile in altre stored procedure di automazione OLE.  
  
 Quando il metodo restituisce il valore è una matrice, se *returnvalue* viene specificato, è impostato su NULL.  
  
 Viene generato un errore in uno dei casi seguenti:  
  
-   *ReturnValue* viene specificato, ma il metodo non restituisce un valore.  
  
-   Il metodo restituisce una matrice a più di due dimensioni.  
  
-   Il metodo restituisce una matrice come parametro di output.  
  
 [  *@parametername* * * =**] *parametro*[ **OUTPUT** ]  
 Parametro del metodo. Se specificato, *parametro* deve essere un valore del tipo di dati appropriato.  
  
 Per ottenere il valore restituito di un parametro di output, *parametro* deve essere una variabile locale del tipo di dati appropriato, e **OUTPUT** deve essere specificato. Se viene specificato un parametro costante oppure se **OUTPUT** viene omesso, qualsiasi restituito valore da un parametro di output viene ignorato.  
  
 Se specificato, *parametername* deve essere il nome del [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] parametro denominato. Si noti che  **@** *parametername*non è un [!INCLUDE[tsql](../../includes/tsql-md.md)] variabile locale. Il simbolo di chiocciola (**@ * *) viene rimosso, e *parametername*viene passato all'oggetto OLE come nome del parametro. Tutti i parametri denominati devono essere specificati dopo tutti i parametri posizionali.  
  
 *n*  
 Segnaposto che indica la possibilità di specificare più parametri.  
  
> [!NOTE]  
>  *@parametername* può essere un parametro denominato perché fa parte del metodo specificato e viene passata all'oggetto. Gli altri parametri della stored procedure vengono specificati in base alla posizione e non in base al nome.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o un numero diverso da zero (esito negativo) corrispondente al valore intero del codice HRESULT restituito dall'oggetto di automazione OLE.  
  
 Per ulteriori informazioni sui codici restituiti HRESULT, [OLE Automation codici restituiti e informazioni sull'errore](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="result-sets"></a>Set di risultati  
 Se il valore restituito del metodo è una matrice a una o due dimensioni, la matrice viene restituita al client come set di risultati:  
  
-   Una matrice unidimensionale viene restituita al client come set di risultati a riga singola con lo stesso numero di colonne del numero di elementi nella matrice. In altri termini, la matrice viene restituita come (colonne).  
  
-   Una matrice bidimensionale viene restituita al client come set di risultati costituito da un numero di colonne pari al numero di elementi della prima dimensione della matrice e un numero di righe pari al numero di elementi della seconda dimensione della matrice. In altri termini, la matrice viene restituita come (colonne, righe).  
  
 Quando il valore restituito da una proprietà o metodo valore è una matrice, **sp_OAGetProperty** o **sp_OAMethod** restituisce un set di risultati al client. I parametri di output dei metodi non possono essere rappresentati da matrici. Queste procedure eseguono un'analisi di tutti i valori di dati della matrice per determinare quali sono i tipi di dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] appropriati e la lunghezza di dati da utilizzare per ogni colonna del set di risultati. Per una colonna specifica queste procedure utilizzano il tipo di dati e la lunghezza necessari per rappresentare tutti i valori di dati della colonna.  
  
 Se a tutti i valori di dati di una colonna è associato lo stesso tipo di dati, tale tipo verrà applicato all'intera colonna. Se i valori di dati di una colonna sono tipi di dati diversi, il tipo di dati della colonna viene scelto in base allo schema seguente.  
  
||int|float|money|datetime|varchar|nvarchar|  
|------|---------|-----------|-----------|--------------|-------------|--------------|  
|**int**|**int**|**float**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**float**|**float**|**float**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**money**|**money**|**money**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**datetime**|**varchar**|**varchar**|**varchar**|**datetime**|**varchar**|**nvarchar**|  
|**varchar**|**varchar**|**varchar**|**varchar**|**varchar**|**varchar**|**nvarchar**|  
|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|  
  
## <a name="remarks"></a>Osservazioni  
 È inoltre possibile utilizzare **sp_OAMethod** per ottenere un valore della proprietà.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo predefinito del server **sysadmin** .  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-calling-a-method"></a>A. Chiamata di un metodo  
 L'esempio seguente chiama il `Connect` metodo creato in precedenza **SQLServer** oggetto.  
  
```  
EXEC @hr = sp_OAMethod @object, 'Connect', NULL, 'my_server',  
    'my_login', 'my_password';  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object  
    RETURN  
END;  
```  
  
### <a name="b-getting-a-property"></a>B. Recupero di una proprietà  
 Nell'esempio seguente viene ottenuto il `HostName` proprietà (dell'oggetto creato in precedenza **SQLServer** oggetto) e lo archivia in una variabile locale.  
  
```  
DECLARE @property varchar(255);  
EXEC @hr = sp_OAMethod @object, 'HostName', @property OUT;  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object  
    RETURN  
END;  
PRINT @property;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Automazione OLE Stored procedure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [Script di automazione OLE di esempio](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
