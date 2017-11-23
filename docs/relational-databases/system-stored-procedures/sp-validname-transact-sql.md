---
title: sp_validname (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_validname
- sp_validname_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_validname
ms.assetid: d51c53c2-1332-407f-b725-4983f2e710eb
caps.latest.revision: "32"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5e010d546f38b315624a8a905e8042792f6bed2c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spvalidname-transact-sql"></a>sp_validname (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Controlla se i nomi degli identificatori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono validi. Tutti i dati di valore non binari e diverso da zero, inclusi i dati Unicode che possono essere archiviati con il **nchar**, **nvarchar**, o **ntext** vengono inoltre accettati come caratteri validi per i tipi di dati, nomi degli identificatori.  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] alla [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_validname [@name =] 'name'   
     [, [@raise_error =] raise_error]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@name=** ] **'***nome***'**  
 È il nome del [identificatori](../../relational-databases/databases/database-identifiers.md) per cui si desidera controllare la validità. *nome* è **sysname**, non prevede alcun valore predefinito. *nome* non può essere NULL, non può essere una stringa vuota e non può contenere un carattere zero binario.  
  
 [  **@raise_error=** ] *raise_error*  
 Viene specificato se generare un errore. *raise_error* è **bit**, con un valore predefinito è 1. Ciò indica che i messaggi di errore vengono visualizzati. Se il valore è 0, i messaggi di errore non vengono visualizzati.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="see-also"></a>Vedere anche  
 [Motore di database Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [NCHAR &#40; Transact-SQL &#41;](../../t-sql/functions/nchar-transact-sql.md)   
 [nchar e nvarchar &#40; Transact-SQL &#41;](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md)   
 [ntext, testo e immagine &#40; Transact-SQL &#41;](../../t-sql/data-types/ntext-text-and-image-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
