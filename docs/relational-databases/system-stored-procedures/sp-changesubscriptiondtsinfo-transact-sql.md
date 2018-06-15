---
title: sp_changesubscriptiondtsinfo (Transact-SQL) | Documenti Microsoft
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
- sp_changesubscriptiondtsinfo
- sp_changesubscriptiondtsinfo_TSQL
helpviewer_keywords:
- sp_changesubscriptiondtsinfo
ms.assetid: 64fc085f-f81b-493b-b59a-ee6192d9736d
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 55c43914d883ce5f704ad6c7648d473bd38611fb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32990986"
---
# <a name="spchangesubscriptiondtsinfo-transact-sql"></a>sp_changesubscriptiondtsinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifica le proprietà dei pacchetti DTS di una sottoscrizione. Questa stored procedure viene eseguita nel database di sottoscrizione del Sottoscrittore.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_changesubscriptiondtsinfo [ [ @job_id = ] job_id ]  
    [ , [ @dts_package_name= ] 'dts_package_name' ]  
    [ , [ @dts_package_password= ] 'dts_package_password' ]  
    [ , [ @dts_package_location= ] 'dts_package_location' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@job_id=**] *job_id*  
 ID di processo dell'agente di distribuzione per la sottoscrizione push. *job_id* viene **varbinary(16)**, non prevede alcun valore predefinito. Per trovare l'ID di processo di distribuzione, eseguire **sp_helpsubscription** o **sp_helppullsubscription**.  
  
 [ **@dts_package_name**=] **'***dts_package_name***'**  
 Nome del pacchetto DTS. *dts_package_name* è un **sysname**, con un valore predefinito è NULL. Ad esempio, per specificare un pacchetto denominato **DTSPub_Package**, si specificherà `@dts_package_name = N'DTSPub_Package'`.  
  
 [ **@dts_package_password**=] **'***dts_package_password***'**  
 Specifica la password per il pacchetto. *dts_package_password* viene **sysname** con un valore predefinito è NULL, che indica che la proprietà della password deve rimanere invariata.  
  
> [!NOTE]  
>  A ogni pacchetto DTS deve essere associata una password.  
  
 [ **@dts_package_location**=] **'***dts_package_location***'**  
 Specifica la posizione del pacchetto. *dts_package_location* è un **nvarchar(12**, con un valore predefinito è NULL, che indica che il percorso del pacchetto deve rimanere invariata. Il percorso del pacchetto può essere modificato per **distributore** o **sottoscrittore**.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_changesubscriptiondtsinfo** viene utilizzato per la replica snapshot e transazionali che corrispondono solo le sottoscrizioni push.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server, **db_owner** ruolo predefinito del database o l'autore della sottoscrizione può eseguire **sp_changesubscriptiondtsinfo**.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
