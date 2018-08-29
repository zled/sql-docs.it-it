---
title: sp_browsemergesnapshotfolder (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_browsemergesnapshotfolder
- sp_browsemergesnapshotfolder_TSQL
helpviewer_keywords:
- sp_browsemergesnapshotfolder
ms.assetid: e248642f-5fea-4ed7-be1a-36ff75abcfde
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 153abe2a9466c6f0496dfe86b852571828111a43
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43020999"
---
# <a name="spbrowsemergesnapshotfolder-transact-sql"></a>sp_browsemergesnapshotfolder (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il percorso completo dell'ultimo snapshot generato per una pubblicazione di tipo merge. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_browsemergesnapshotfolder [@publication= ] 'publication'  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication=**] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* viene **sysname**, non prevede alcun valore predefinito.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**snapshot_folder**|**nvarchar(2000)**|Percorso completo della directory snapshot.|  
  
## <a name="remarks"></a>Note  
 **sp_browsemergesnapshotfolder** viene utilizzata nella replica di tipo merge.  
  
 Se la pubblicazione è configurata in modo da generare file di snapshot sia nella directory di lavoro del server di pubblicazione che nella cartella snapshot del server di pubblicazione, nel set di risultati saranno presenti due righe, delle quali la prima contiene la cartella snapshot della pubblicazione e la seconda contiene la directory di lavoro del server di pubblicazione.  
  
 **sp_browsemergesnapshotfolder** è utile per determinare la directory in cui vengono generati i file di snapshot di tipo merge. Il percorso della cartella e il relativo contenuto possono quindi essere copiati su supporti rimovibili e lo snapshot può essere utilizzato per la sincronizzazione di una sottoscrizione da una posizione snapshot alternativa.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server oppure **db_owner** ruolo predefinito del database possono eseguire **sp_browsemergesnapshotfolder**.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
