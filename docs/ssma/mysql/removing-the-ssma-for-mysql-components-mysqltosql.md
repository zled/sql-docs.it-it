---
title: Rimozione di SSMA per i componenti di MySQL (MySQLToSql) | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-mysql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Uninstalling, Extension pack
- Uninstalling, SSMA for MySQL client
ms.assetid: 87cdbd49-a0c9-4b00-8a93-34188b18d11a
caps.latest.revision: 10
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: ca102048105f75e9788115eafbb5bcd8dc907052
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="removing-the-ssma-for-mysql-components-mysqltosql"></a>Rimozione di SSMA per i componenti di MySQL (MySQLToSql)
Al termine di migrazione di database da MySQL a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è possibile disinstallare i componenti SSMA. È possibile disinstallare i componenti client in qualsiasi momento. Tuttavia, se si disinstalla il pacchetto di estensione da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , quindi SSMA non supporterà più migrazione dei dati da MySQL al database di destinazione (SQL Server o SQL Azure) usando il modulo di migrazione dei dati lato Server.  
  
## <a name="uninstalling-the-ssma-for-mysql-client"></a>Disinstallazione di SSMA per Client di MySQL  
È possibile disinstallare SSMA utilizzando **Aggiungi / Rimuovi programmi**.  
  
**Per disinstallare di SSMA**  
  
1.  Nel Pannello di controllo aprire **Aggiungi / Rimuovi programmi**.  
  
2.  Selezionare **Microsoft SQL Server Migration Assistant per MySQL**, quindi fare clic su **rimuovere**.  
  
3.  Per confermare che si desidera disinstallare SSMA, fare clic su **Sì**.  
  
## <a name="uninstalling-the-extension-pack"></a>Disinstallare il pacchetto di estensione  
È possibile rimuovere il pacchetto di estensione utilizzando **Aggiungi / Rimuovi programmi**.  
  
**Per disinstallare il pacchetto di estensione**  
  
1.  Nel Pannello di controllo aprire **Aggiungi / Rimuovi programmi**.  
  
2.  Selezionare **Microsoft SQL Server Migration Assistant per MySQL estensione Pack**, quindi fare clic su **rimuovere**.  
  
3.  Per confermare che si desidera disinstallare il pacchetto di estensione, fare clic su **Sì**.  
  
4.  Nelle istanze con pagina utilità degli script del Database, selezionare un'istanza e quindi fare clic su **Avanti**.  
  
5.  Nella pagina parametri di connessione, selezionare il metodo di autenticazione e quindi fare clic su **Avanti**.  
  
    L'autenticazione di Windows utilizzerà le credenziali di Windows per tentare di accedere all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Se si seleziona [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] l'autenticazione, è necessario immettere un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] nome account di accesso e password.  
  
6.  Nella pagina operazione completata, fare clic su **OK**.  
  
7.  Nell'ultima pagina, fare clic su **uscita**.  
  
Dopo aver completato il processo di disinstallazione, è possibile confermare che gli oggetti nel **sysdb.ssma_MySQL** schema ed eventualmente l'intero **sysdb** del database, è stato rimosso utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]. Tuttavia, se si utilizzano altri prodotti SSMA, anche usano il **sysdb** database. Se il database esista e si è certi che nessun altro database fanno riferimento agli oggetti in questo database, è possibile scollegare il database.  
  
## <a name="see-also"></a>Vedere anche  
[Installazione di SSMA per Client di MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/installing-ssma-for-mysql-client-mysqltosql.md)  
[Installazione di componenti SSMA in SQL Server](http://msdn.microsoft.com/en-us/6772d0c5-258f-4d7b-afb0-b5f810e71af1)  
  
