---
title: Escludere un server di destinazione da un server master | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- target servers [SQL Server], defecting
- SQL Server Agent jobs, master servers
- master servers [SQL Server], defecting target servers
- defecting target servers
ms.assetid: a6da262b-7b38-4ce4-bfd6-6a557c6e8a84
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 35f113cfd0e038940c00b710b31f254da6343805
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37305041"
---
# <a name="defect-a-target-server-from-a-master-server"></a>Escludere un server di destinazione da un server master
  In questo argomento viene descritto come escludere un server di destinazione da un server master in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] o SQL Server Management Objects (SMO). Eseguire questa procedura dal server di destinazione.  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Security](#Security)  
  
-   **Per escludere un server di destinazione utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [SMO](#PowerShellProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 Per eseguire questa stored procedure, è necessario essere un membro del ruolo predefinito del server `sysadmin`.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-defect-a-target-server-from-a-master-server"></a>Per escludere un server di destinazione da un server master  
  
1.  In **Esplora oggetti**espandere un server configurato come server di destinazione.  
  
2.  Fare clic con il pulsante destro del mouse su **SQL Server Agent**, scegliere **Amministrazione multiserver**e fare clic su **Escludi**.  
  
3.  Fare clic su **Sì** per confermare l'esclusione del server di destinazione da un server master.  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
  
#### <a name="to-defect-a-target-server-from-a-master-server"></a>Per escludere un server di destinazione da un server master  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**.  
  
```  
sp_msx_defect ;  
```  
  
 Per altre informazioni, vedere [sp_msx_defect &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-defect-transact-sql).  
  
##  <a name="PowerShellProcedure"></a> Usando SQL Server Management Objects (SMO)  
 Utilizzare la `MsxDefect Method`.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un ambiente multiserver](create-a-multiserver-environment.md)   
 [Amministrazione automatizzata in un'organizzazione](automated-administration-across-an-enterprise.md)   
 [Escludere più server di destinazione da un server master](defect-multiple-target-servers-from-a-master-server.md)  
  
  
