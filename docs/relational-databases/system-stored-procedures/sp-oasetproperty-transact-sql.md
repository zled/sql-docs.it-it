---
title: sp_OASetProperty (Transact-SQL) | Microsoft Docs
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
- sp_OASetProperty
- sp_OASetProperty_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_OASetProperty
ms.assetid: 0fe7d554-6b67-4d55-9d3e-4096802c47f8
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 689549b2741e4b334f664cf7662204702686a93f
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43023741"
---
# <a name="spoasetproperty-transact-sql"></a>sp_OASetProperty (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Imposta una proprietà di un oggetto OLE su un nuovo valore.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_OASetProperty objecttoken , propertyname , newvalue [ , index... ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *vengono restituite le*  
 È il token di oggetto di un oggetto OLE creato in precedenza da **sp_OACreate**.  
  
 *propertyname*  
 Nome della proprietà dell'oggetto OLE da impostare su un nuovo valore.  
  
 *NewValue*  
 Nuovo valore della proprietà con il tipo di dati appropriato.  
  
 *index*  
 Parametro di indice. Se specificato, *indice* deve essere un valore del tipo di dati appropriato.  
  
 Ad alcune proprietà sono associati parametri. Tali proprietà sono denominate proprietà indicizzate e i parametri corrispondenti sono denominati parametri di indice. A una proprietà possono essere associati più parametri di indice.  
  
> [!NOTE]  
>  I parametri di questa stored procedure vengono specificati in base alla posizione, non in base al nome.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o un numero diverso da zero (esito negativo) corrispondente al valore intero del codice HRESULT restituito dall'oggetto di automazione OLE.  
  
 Per altre informazioni sui codici restituiti HRESULT, vedere [OLE Automation codici restituiti e informazioni sull'errore](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo predefinito del server **sysadmin** .  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente imposta la `HostName` proprietà (dell'oggetto creato in precedenza **SQLServer** oggetto) su un nuovo valore.  
  
```  
EXEC @hr = sp_OASetProperty @object, 'HostName', 'Gizmo';  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object  
    RETURN  
END'  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Automazione OLE Stored procedure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [Script di automazione OLE di esempio](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
