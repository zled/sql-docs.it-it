---
title: Rimozione di SSMA per Sybase componenti (SybaseToSQL) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: aec09593-17d9-4ec2-ac56-3cd8851406fd
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: bd57909a4aade0a07da76f0e222fb21e58e643c3
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="removing-ssma-for-sybase-components-sybasetosql"></a>Rimozione di SSMA per Sybase componenti (SybaseToSQL)
Una volta terminata la migrazione dei database di Sybase Adaptive Server Enterprise (ASE) per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è possibile disinstallare i componenti SSMA. È possibile disinstallare i componenti client in qualsiasi momento, ma non è necessario disinstallare il pacchetto di estensione da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] a meno che non si è certi che i database migrati non usare più funzioni di **ssma_syb** dello schema del **sysdb** database.  
  
## <a name="uninstalling-the-ssma-for-sybase-client"></a>Disinstallazione di SSMA per Sybase Client  
È possibile disinstallare SSMA utilizzando **Aggiungi / Rimuovi programmi**.  
  
**Per disinstallare SSMA**  
  
1.  Nel Pannello di controllo aprire **Aggiungi / Rimuovi programmi**.  
  
2.  Selezionare **Microsoft SQL Server Migration Assistant per Sybase**, quindi fare clic su **rimuovere**.  
  
3.  Per confermare che si desidera disinstallare SSMA, fare clic su **Sì**.  
  
## <a name="uninstalling-the-extension-pack"></a>Disinstallare il pacchetto di estensione  
Se si è certi dei database migrati non utilizzano gli oggetti di **sysdb.ssma_syb** dello schema, è possibile rimuovere il pacchetto di estensione utilizzando **Aggiungi / Rimuovi programmi**.  
  
Per disinstallare il pacchetto di estensione  
  
1.  Nel Pannello di controllo aprire **Aggiungi / Rimuovi programmi**.  
  
2.  Selezionare **Microsoft SQL Server Migration Assistant per Sybase estensione Pack**, quindi fare clic su **rimuovere**.  
  
3.  Per confermare che si desidera disinstallare il pacchetto di estensione, fare clic su **Sì**.  
  
4.  Nelle istanze di con la pagina degli script di Database di utilità, fare clic su **Avanti**.  
  
5.  Nella pagina parametri di connessione, selezionare il metodo di autenticazione e quindi fare clic su **Avanti**.  
  
    L'autenticazione di Windows utilizzerà le credenziali di Windows per tentare di accedere all'istanza di SQL Server. Se si seleziona autenticazione di SQL Server, è necessario immettere un nome di account di accesso di SQL Server e una password.  
  
6.  Nella pagina operazione completata, fare clic su **OK**.  
  
7.  Nell'ultima pagina, fare clic su **uscita**.  
  
Dopo la disinstallazione, è possibile verificare che il **sysdb.ssma_syb** schema ed eventualmente l'intero **sysdb** del database, è stato rimosso utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]. Tuttavia, se si utilizzano altri prodotti SSMA, anche usano il **sysdb** database. Se il database esista e si è certi che nessun altro database fanno riferimento a oggetti in questo database, è possibile scollegare il database.  
  
## <a name="see-also"></a>Vedere anche  
[Installazione di SSMA per Sybase Client &#40; SybaseToSQL &#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)  
[Installazione dei componenti SSMA in SQL Server &#40; SybaseToSQL &#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
  

