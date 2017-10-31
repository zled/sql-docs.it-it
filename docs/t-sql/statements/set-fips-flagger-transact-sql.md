---
title: SET FIPS_FLAGGER (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FIPS_FLAGGER
- SET_FIPS_FLAGGER_TSQL
- FIPS_FLAGGER_TSQL
- SET FIPS_FLAGGER
dev_langs:
- TSQL
helpviewer_keywords:
- SET FIPS_FLAGGER statement
- FIPS 127-2 standard
- FIPS_FLAGGER option
ms.assetid: e82f6bee-6cf6-4061-be22-9ad2e8e9d3d6
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4c28fd5419aec8bf15745150288b6878fd65ac1f
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="set-fipsflagger-transact-sql"></a>SET FIPS_FLAGGER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Specifica il controllo della conformità con lo standard FIPS 127-2, basato sullo standard ISO. Per informazioni sulla conformità a FIPS per SQL Server, vedere [illustrato come utilizzare SQL Server 2016 in modalità FIPS 140-2-compatibile](https://support.microsoft.com/help/4014354/how-to-use-sql-server-2016-in-fips-140-2-compliant-mode). 
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
SET FIPS_FLAGGER ( 'level' |  OFF )  
```  
  
## <a name="arguments"></a>Argomenti  
 **'** *livello* **'**  
 Livello di conformità con lo standard FIPS 127-2 in base a cui vengono controllate tutte le operazioni del database. Se un'operazione di database è in conflitto con il livello degli standard ISO scelti, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] genera un avviso.  
  
 *livello* deve essere uno dei valori seguenti.  
  
|Valore|Description|  
|-----------|-----------------|  
|ENTRY|Controllo degli standard per la conformità di base con ISO.|  
|FULL|Controllo degli standard per la conformità totale con ISO.|  
|INTERMEDIATE|Controllo degli standard per la conformità a livello intermedio con ISO.|  
|OFF|Nessun controllo di conformità degli standard.|  
  
## <a name="remarks"></a>Osservazioni  
 L'impostazione di `SET FIPS_FLAGGER` è impostata in fase di analisi e non in esecuzione o di esecuzione. Impostazione in fase di analisi significa che se l'istruzione SET è presente nel batch o stored procedure, viene attivata indipendentemente dal fatto che l'esecuzione del codice raggiunga effettivamente tale punto. e `SET` istruzione eseguita prima dell'esecuzione di tutte le istruzioni. Ad esempio, anche se il `SET` istruzione si trova in un `IF...ELSE` blocco di istruzioni che non viene mai raggiunto durante l'esecuzione, il `SET` istruzione viene comunque eseguita perché la `IF...ELSE` blocco viene analizzato.  
  
 Se `SET FIPS_FLAGGER` è impostato in una stored procedure, il valore di `SET FIPS_FLAGGER` viene ripristinato dopo il controllo viene restituito dalla stored procedure. Pertanto, un `SET FIPS_FLAGGER` istruzione specificata nel linguaggio SQL dinamico non ha alcun effetto sulle istruzioni successive l'istruzione SQL dinamica.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  

