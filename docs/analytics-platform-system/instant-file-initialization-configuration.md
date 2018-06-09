---
title: Configurare l'inizializzazione immediata dei File - Analitica Platform System | Documenti Microsoft
description: Configurare l'inizializzazione immediata dei File nel sistema della piattaforma Analitica. Inizializzazione immediata dei file è una funzionalità di SQL Server che consente operazioni di file di dati eseguire più rapidamente.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: f2c1e0e17e2cbfb5816632a25ecdebe5d92ee024
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34706749"
---
# <a name="instant-file-initialization-configuration"></a>Configurazione di inizializzazione immediata dei File
Inizializzazione immediata dei file è una funzionalità di SQL Server che consente operazioni di file di dati eseguire più rapidamente. Selezionando la casella per attivare l'inizializzazione immediata dei File migliorerà le prestazioni di SQL Server PDW. Tuttavia, se ciò comporta un rischio per la sicurezza per l'utente business, quindi lasciare deselezionata la casella.  
  
> [!IMPORTANT]  
> Quando è abilitata l'inizializzazione immediata dei file, SQL Server bits eliminato con zeri non vengono sovrascritte.  Questo comportamento è stato possibile creare una vulnerabilità di sicurezza se utenti non autorizzati ottengono l'accesso ai dati eliminati. Tuttavia, SQL Server PDW limita questo rischio assicurando che il database di SQL Server e i file di backup sono sempre associati a un'istanza di SQL Server. solo l'account del servizio SQL Server e all'amministratore locale può accedere ai dati eliminati in SQL Server PDW.  
  
L'inizializzazione immediata dei file non è disponibile quando è abilitata la crittografia TDE.  
  
## <a name="add-permission-for-the-backup-account"></a>Aggiungere l'autorizzazione per l'Account di Backup  
Il processo di backup richiede una credenziale di rete (account utente di Windows) che può accedere al percorso di archiviazione di backup. Si autorizza PDW come utilizzare l'account utilizzando il [sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md) procedura. Vedere [BACKUP DATABASE](../t-sql/statements/backup-database-parallel-data-warehouse.md) per l'intero processo di backup. Per utilizzare l'inizializzazione immediata dei file, concedere all'account di backup di `Perform volume maintenance tasks` autorizzazione.  
  
1.  Nel server di backup, aprire il **criteri di sicurezza locali** applicazione (`secpol.msc`).  
  
2.  Nel riquadro sinistro espandere **Criteri locali**, quindi fare clic su **Assegnazione diritti utente**.  
  
3.  Nel riquadro destro fare doppio clic su **Esecuzione attività di manutenzione volume**.  
  
4.  Fare clic su **Aggiungi utente o gruppo** e aggiungere tutti gli account utente usati per i backup.  
  
5.  Fare clic su **Applica**, quindi chiudere tutte le finestre di dialogo di **Criteri di sicurezza locali** .  
  
## <a name="to-turn-instant-file-initialization-on-or-off"></a>Per attivare o disattivare la inizializzazione immediata dei File  
  
1.  Avviare Gestione configurazione. Per altre informazioni, vedere [avviare Gestione configurazione &#40;Analitica Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  Nel riquadro a sinistra di Configuration Manager, fare clic su **inizializzazione immediata dei File**.  
  
3.  Per attivare l'inizializzazione immediata dei file, selezionare la casella accanto a **abilitare inizializzazione immediata dei File in tutti i nodi**. Per disattivare l'inizializzazione immediata dei file, deselezionare la casella accanto a **abilitare inizializzazione immediata dei File in tutti i nodi**.  
  
    > [!WARNING]  
    > Quando si disattiva l'inizializzazione immediata dei file, le considerazioni di sicurezza descritti sopra per la funzionalità potrebbero comunque applicate ai file eliminati durante l'inizializzazione immediata dei file è stato abilitato.  
  
4.  Fare clic su **Applica**. La modifica verrà propagata tramite le istanze di SQL Server in SQL Server PDW al successivo che riavvio dei servizi il dispositivo. Per riavviare i servizi di dispositivo, vedere [PDW stato del servizio &#40;Analitica Platform System&#41;](pdw-services-status.md).  
  
5.  È possibile ripetere i passaggi descritti in precedenza come **Aggiungi autorizzazione per l'Account di Backup** per rimuovere il **eseguire attività di manutenzione volume** autorizzazione.  
  
![Inizializzazione di File immediata DWConfig Appliance PDW](./media/instant-file-initialization-configuration/SQL_Server_PDW_DWConfig_ApplPDWInstant.png "SQL_Server_PDW_DWConfig_ApplPDWInstant")  
  
Per ulteriori informazioni sull'inizializzazione immediata dei file, vedere [inizializzazione immediata dei File](http://technet.microsoft.com/library/ms175935(v=SQL.105).aspx).  
  
