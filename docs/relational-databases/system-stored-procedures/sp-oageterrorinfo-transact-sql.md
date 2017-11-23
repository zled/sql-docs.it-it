---
title: sp_OAGetErrorInfo (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_OAGetErrorInfo_TSQL
- sp_OAGetErrorInfo
dev_langs: TSQL
helpviewer_keywords: sp_OAGetErrorInfo
ms.assetid: ceecea08-456f-4819-85d9-ecc9647d7187
caps.latest.revision: "16"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b107c2599e11a81a401a08bfba2a20df3b5962e8
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spoageterrorinfo-transact-sql"></a>sp_OAGetErrorInfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ottiene informazioni sull'errore di automazione OLE.  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_OAGetErrorInfo [ objecttoken ]  
    [ , source OUTPUT ]   
    [ , description OUTPUT ]   
    [ , helpfile OUTPUT ]   
    [ , helpid OUTPUT ]   
```  
  
## <a name="arguments"></a>Argomenti  
 *vengono restituite le*  
 Il token di oggetto di un oggetto OLE creato in precedenza tramite **sp_OACreate** o è NULL. Se *vengono restituite le* è specificato, vengono restituite informazioni sull'errore per l'oggetto. Se viene specificato NULL, vengono restituite le informazioni sull'errore relative all'intero batch.  
  
 *origine* **OUTPUT**  
 Origine delle informazioni sull'errore. Se specificato, deve essere locale **char**, **nchar**, **varchar**, o **nvarchar** variabile. Se necessario, il valore restituito viene troncato in base alla dimensione della variabile locale.  
  
 *Descrizione* **OUTPUT**  
 Descrizione dell'errore. Se specificato, deve essere locale **char**, **nchar**, **varchar**, o **nvarchar** variabile. Se necessario, il valore restituito viene troncato in base alla dimensione della variabile locale.  
  
 *HelpFile* **OUTPUT**  
 File della Guida relativo all'oggetto OLE. Se specificato, deve essere locale **char**, **nchar**, **varchar**, o **nvarchar** variabile. Se necessario, il valore restituito viene troncato in base alla dimensione della variabile locale.  
  
 *HelpID* **OUTPUT**  
 ID di contesto del file della Guida. Se specificato, deve essere locale **int** variabile.  
  
> [!NOTE]  
>  I parametri di questa stored procedure vengono specificati in base alla posizione, non in base al nome.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o un numero diverso da zero (esito negativo) corrispondente al valore intero del codice HRESULT restituito dall'oggetto di automazione OLE.  
  
 Per ulteriori informazioni sui codici restituiti HRESULT, vedere [OLE Automation codici restituiti e informazioni sull'errore](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="result-sets"></a>Set di risultati  
 Se non viene specificato alcun parametro di output, le informazioni sull'errore vengono restituite al client come set di risultati.  
  
|Nomi colonna|Tipo di dati|Description|  
|------------------|---------------|-----------------|  
|**Errore**|**Binary(4)**|Rappresentazione binaria del numero di errore.|  
|**Origine**|**nvarchar(nn)**|Origine dell'errore.|  
|**Description**|**nvarchar(nn)**|Descrizione dell'errore.|  
|**HelpFile**|**nvarchar(nn)**|File della Guida relativo all'origine.|  
|**HelpID**|**int**|ID di contesto della Guida nel file di origine della Guida.|  
  
## <a name="remarks"></a>Osservazioni  
 Stored procedure di ogni chiamata a un'automazione OLE (tranne **sp_OAGetErrorInfo**) le informazioni sull'errore, pertanto, **sp_OAGetErrorInfo** recupera informazioni sull'errore solo per OLE più recente Automazione di chiamata di stored procedure. Si noti che poiché **sp_OAGetErrorInfo** non ripristina le informazioni sull'errore, può essere chiamato più volte per ottenere le stesse informazioni di errore.  
  
 Nella tabella seguente vengono elencati gli errori di automazione OLE e le cause più comuni.  
  
|Errore e codice HRESULT|Causa più comune|  
|-----------------------|------------------|  
|**Tipo di variabile non valido (0x80020008)**|Tipo di dati di un [!INCLUDE[tsql](../../includes/tsql-md.md)] valore passato come un parametro di metodo non corrispondeva il [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] tipo di dati del parametro del metodo o un valore NULL è stato passato come parametro di metodo.|  
|**Nome sconosciuto (0x8002006)**|Il nome di proprietà o metodo specificato non è stato trovato per l'oggetto specificato.|  
|**Stringa di classe non valida (0x800401f3)**|Il valore ProgID o CLSID specificato non è registrato come oggetto OLE in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Server di automazione OLE personalizzati devono essere registrati prima può essere implementati con **sp_OACreate**. Questa operazione può essere eseguita tramite l'utilità Regsvr32.exe per server (. dll) in-process, o **/REGSERVER** switch della riga di comando per i server locali (.exe).|  
|**Esecuzione del server fallita (0x80080005)**|L'oggetto OLE specificato è registrato come server OLE locale (file exe), ma non è stato possibile trovare o avviare il file.|  
|**Il modulo specificato non trovato (0x8007007e)**|L'oggetto OLE specificato è registrato come server OLE in-process (file dll), ma non è stato possibile trovare o caricare il file.|  
|**Tipo non corrispondente (0x80020005)**|Il tipo di dati di una variabile locale [!INCLUDE[tsql](../../includes/tsql-md.md)] utilizzata per l'archiviazione del valore restituito di una proprietà o un metodo non corrisponde al tipo di dati di [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] del valore restituito della proprietà o del metodo oppure è stato richiesto il valore restituito di una proprietà o un metodo ma non viene restituito alcun valore.|  
|**Il tipo di dati o il valore del parametro 'context' di sp_OACreate non è valido (0x8004275B)**|Il valore del parametro di contesto deve essere 1, 4 o 5.|  
  
 Per ulteriori informazioni sull'elaborazione dei codici restituiti HRESULT, vedere [OLE Automation codici restituiti e informazioni sull'errore](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo predefinito del server **sysadmin** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono visualizzate le informazioni sull'errore di automazione OLE.  
  
```  
DECLARE @output varchar(255);  
DECLARE @hr int;  
DECLARE @source varchar(255);  
DECLARE @description varchar(255);  
PRINT 'OLE Automation Error Information';  
EXEC @hr = sp_OAGetErrorInfo @object, @source OUT, @description OUT;  
IF @hr = 0  
BEGIN  
    SELECT @output = '  Source: ' + @source  
    PRINT @output  
    SELECT @output = '  Description: ' + @description  
    PRINT @output  
END  
ELSE  
BEGIN  
    PRINT '  sp_OAGetErrorInfo failed.'  
    RETURN  
END;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Automazione OLE Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [Script di automazione OLE di esempio](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
