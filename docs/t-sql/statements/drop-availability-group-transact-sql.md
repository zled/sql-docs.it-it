---
title: "ELIMINAZIONE gruppo di disponibilità (Transact-SQL) | Documenti Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_AVAILABILITY_GROUP_TSQL
- DROP AVAILABILITY GROUP
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], removing
- Availability Groups [SQL Server], Transact-SQL statements
- DROP AVAILABILITY GROUP statement
- Availability Groups [SQL Server], dropping
ms.assetid: c1600289-c990-454a-b279-dba0ebd5d63e
caps.latest.revision: 44
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c1cd1e16d7d25810d571f940aaf1dece825406c3
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="drop-availability-group-transact-sql"></a>DROP AVAILABILITY GROUP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Rimuove il gruppo di disponibilità specificato e tutte le relative repliche. Se un'istanza del server che ospita una delle repliche di disponibilità è offline quando si elimina un gruppo di disponibilità, la replica di disponibilità locale verrà eliminata dall'istanza del server quando torna online. La rimozione di un gruppo di disponibilità comporta l'eliminazione dell'eventuale listener del gruppo di disponibilità associato.  
  
> [!IMPORTANT]  
>  Se possibile, rimuovere il gruppo di disponibilità solo se connesso all'istanza del server in cui è ospitata la replica primaria. Se il gruppo di disponibilità viene rimosso dalla replica primaria, sono consentite modifiche nei database primari precedenti (senza protezione a disponibilità elevata). L'eliminazione di un gruppo di disponibilità da una replica secondaria, la replica primaria nel **RESTORING** lo stato e le modifiche non sono consentite nei database.  
  
 Per informazioni su metodi alternativi per eliminare un gruppo di disponibilità, vedere [rimuovere un gruppo di disponibilità &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/remove-an-availability-group-sql-server.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DROP AVAILABILITY GROUP group_name   
[ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *nome_gruppo*  
 Specifica il nome del gruppo di disponibilità da eliminare.  
  
## <a name="limitations-and-recommendations"></a>Limitazioni e consigli  
  
-   L'esecuzione di **DROP AVAILABILITY GROUP** richiede che la funzionalità gruppi di disponibilità AlwaysOn è abilitata nell'istanza del server. Per altre informazioni, vedere [Abilitare e disabilitare la funzionalità Gruppi di disponibilità Always On &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md).  
  
-   **DROP AVAILABILITY GROUP** non può essere eseguito come parte del batch o all'interno di transazioni. Le espressioni e le variabili non sono supportate.  
  
-   È possibile eliminare un gruppo di disponibilità da qualsiasi nodo WSFC (Windows Server Failover Clustering) che disponga delle credenziali di sicurezza corrette per il gruppo di disponibilità. In questo modo, è possibile eliminare un gruppo di disponibilità quando non rimane nessuna delle relative repliche di disponibilità.  
  
    > [!IMPORTANT]  
    >  Evitare di eliminare un gruppo di disponibilità se il cluster WSFC (Windows Server Failover Clustering) non dispone di quorum. Se è necessario eliminare un gruppo di disponibilità quando il cluster non dispone di quorum, non verrà rimosso il gruppo di disponibilità dei metadati archiviato nel cluster. Una volta che il cluster avrà riacquisito il quorum, sarà necessario eliminare nuovamente il gruppo di disponibilità per rimuoverlo dal cluster WSFC.  
  
-   In una replica secondaria, **DROP AVAILABILITY GROUP** solo deve essere utilizzato solo per i casi di emergenza. poiché, se si elimina un gruppo di disponibilità, quest'ultimo viene portato offline. Se si elimina il gruppo di disponibilità da una replica secondaria, la replica primaria non è possibile determinare se il **OFFLINE** stato si è verificato a causa di perdita del quorum, un failover forzato, o un **DROP AVAILABILITY GROUP**comando. La replica primaria passa per la **RESTORING** stato per impedire una possibile situazione Split-Brain. Per altre informazioni, vedere [How It Works: DROP AVAILABILITY GROUP Behaviors](http://blogs.msdn.com/b/psssql/archive/2012/06/13/how-it-works-drop-availability-group-behaviors.aspx) (Funzionamento: comportamenti di DROP AVAILABILITY GROUP) nel blog del Supporto Tecnico di SQL Server.  
  
## <a name="security"></a>Sicurezza  
  
### <a name="permissions"></a>Permissions  
 Richiede **ALTER AVAILABILITY GROUP** l'autorizzazione per il gruppo di disponibilità, **CONTROL AVAILABILITY GROUP** autorizzazione, **ALTER ANY AVAILABILITY GROUP** autorizzazione, o **CONTROL SERVER** autorizzazione. Per eliminare un gruppo di disponibilità non ospitato dall'istanza del server locale, è necessario **CONTROL SERVER** autorizzazione o **controllo** in tale gruppo di disponibilità.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene eliminato il gruppo di disponibilità `AccountsAG`.  
  
```  
DROP AVAILABILITY GROUP AccountsAG;  
```  
  
##  <a name="RelatedContent"></a> Contenuto correlato  
  
-   [How It Works: DROP AVAILABILITY GROUP Behaviors](http://blogs.msdn.com/b/psssql/archive/2012/06/13/how-it-works-drop-availability-group-behaviors.aspx) (Funzionamento: comportamenti di DROP AVAILABILITY GROUP) nel blog del Supporto Tecnico di SQL Server  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-availability-group-transact-sql.md)   
 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [Rimuovere un gruppo di disponibilità &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/remove-an-availability-group-sql-server.md)  
  
  

