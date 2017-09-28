---
title: SET TEXTSIZE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 04/12/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TEXTSIZE_TSQL
- TEXTSIZE
- SET_TEXTSIZE_TSQL
- SET TEXTSIZE
dev_langs:
- TSQL
helpviewer_keywords:
- SET TEXTSIZE statement
- SELECT statement [SQL Server], text size returned
- size [SQL Server], text and image data
- TEXTSIZE option
- text size returned [SQL Server]
ms.assetid: 787154a6-39a6-4dd6-a6d0-67b4364f95d5
caps.latest.revision: 38
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2d9925b382a7d09722846ca7da583fb92fe4609c
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="set-textsize-transact-sql"></a>SET TEXTSIZE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Specifica la dimensione del **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, **testo**, **ntext** , e **immagine** dati restituiti da un'istruzione SELECT.  
  
> [!IMPORTANT]  
>  **ntext**, **testo**, e **immagine** tipi di dati verranno rimossa in una versione futura di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Evitare di utilizzare questi tipi di dati in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni che attualmente li utilizzano. Usare in alternativa **nvarchar(max)**, **varchar(max)**e **varbinary(max)** .  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
SET TEXTSIZE { number }   
```  
  
## <a name="arguments"></a>Argomenti  
 *number*  
 È la lunghezza di **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, **testo**, **ntext**, o **immagine** dati, in byte. *numero* è un intero con un valore massimo di 2147483647 (2 GB).  Il valore-1 indica dimensioni illimitate. Il valore 0 Reimposta le dimensioni per il valore predefinito di 4 KB.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client (versione 10.0 e versioni successive) e il Driver ODBC per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] automaticamente specificare `-1` (illimitato) per la connessione.  
  
 **I driver più vecchi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008:** il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client Provider OLE DB (versione 9) per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] impostata automaticamente TEXTSIZE su 2147483647 quando ci si connette.  
  
## <a name="remarks"></a>Osservazioni  
 L'impostazione SET TEXTSIZE influisce il @@TEXTSIZE (funzione).  
  
 L'opzione TEXTSIZE viene impostata in fase di esecuzione, non in fase di analisi.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="see-also"></a>Vedere anche  
 [@@TEXTSIZE &#40;Transact-SQL&#41;](../../t-sql/functions/textsize-transact-sql.md)   
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  

