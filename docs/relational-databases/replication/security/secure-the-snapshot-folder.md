---
title: "Sicurezza della cartella snapshot | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "snapshot [replica di SQL Server], sicurezza"
ms.assetid: 3cd877d1-ffb8-48fd-a72b-98eb948aad27
caps.latest.revision: 46
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 46
---
# Sicurezza della cartella snapshot
  La cartella snapshot è una directory in cui vengono archiviati i file di snapshot. È consigliabile dedicare questa directory esclusivamente all'archiviazione degli snapshot. Concedere all'agente snapshot l'autorizzazione di scrittura per la cartella e verificare che l'autorizzazione di lettura sia concessa solo all'account di Windows utilizzato dall'agente di merge o dall'agente di distribuzione per accedere alla cartella. L'account di Windows associato all'agente deve essere un account di dominio per poter accedere a una cartella snapshot posizionata in un computer remoto.  
  
> [!NOTE]  
>  Controllo Account utente (UAC) consente agli amministratori di gestire i propri diritti utente elevati (detti anche *privilegi*). Quando l'esecuzione avviene in sistemi operativi con Controllo account utente abilitato, gli amministratori non utilizzano i propri diritti amministrativi, ma eseguono la maggior parte delle azioni come utenti standard (non amministrativi), assumendo temporaneamente i diritti di amministratore solo se necessario. Controllo account utente può impedire l'accesso amministrativo alla condivisione snapshot. Le autorizzazioni per la condivisione snapshot devono pertanto essere concesse in modo esplicito agli account di Windows utilizzati dall'agente snapshot, dall'agente di distribuzione e dall'agente di merge. È necessario eseguire questa operazione anche se gli account di Windows sono membri del gruppo Administrators.  
  
 Quando si configura un server di distribuzione tramite configurazione guidata distribuzione o la creazione guidata nuova pubblicazione, per impostazione predefinita la cartella snapshot in un percorso locale: x:\Programmi\Microsoft \ Microsoft SQL Server\\*\< istanza>*\Mssql\Repldata.. Se si utilizza un server di distribuzione remoto o le sottoscrizioni pull, è necessario specificare una condivisione di rete UNC (ad esempio \\\\<*computername >*\snapshot) anziché un percorso locale.  
  
 Quando si concedono le autorizzazioni di accesso alla cartella snapshot, è necessario valutare il tipo di accesso che verrà utilizzato per la cartella. In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 2003 vengono utilizzate le schede di finestre di dialogo seguenti:  
  
-   Se si specifica un percorso locale, concedere le autorizzazioni mediante il **sicurezza** scheda della finestra di **proprietà** la finestra di dialogo per la cartella.  
  
-   Se si specifica una condivisione di rete, concedere le autorizzazioni mediante il **condivisione** scheda della finestra di **proprietà** la finestra di dialogo per la cartella.  
  
    > [!NOTE]  
    >  Se l'agente di replica viene eseguito nel server di distribuzione, utilizzare il **sicurezza** scheda della finestra di **proprietà** la finestra di dialogo per la cartella per concedere le autorizzazioni per l'account Windows utilizzato per eseguire l'agente. Eseguire questa operazione anche in caso di utilizzo di una condivisione di rete. Ciò è applicabile all'agente di merge e all'agente di distribuzione per una sottoscrizione push e all'agente snapshot quando il server di pubblicazione e il server di distribuzione risiedono nello stesso computer.  
  
 Per ulteriori informazioni sull'impostazione di autorizzazioni per i percorsi locali e le condivisioni di rete, vedere la documentazione di Windows.  
  
> [!NOTE]  
>  Se una pubblicazione viene rimossa, la replica tenta di rimuovere la cartella snapshot nel contesto di sicurezza dell'account del servizio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Se questo account non dispone di privilegi sufficienti, accedere con un account che dispone di privilegi adeguati e rimuovere manualmente la cartella. Richiede la rimozione di una cartella di **Modifica** privilegi se la cartella è un percorso locale o **controllo completo** privilegi se la cartella è un percorso di rete.  
  
## Recapito di snapshot tramite FTP  
 Sebbene sia consigliabile dal punto di vista della sicurezza archiviare gli snapshot in una condivisione UNC, gli snapshot possono essere archiviati in una condivisione FTP e quindi recapitati a un Sottoscrittore tramite FTP. Quando si configura il server FTP, verificare che la directory virtuale esponga una condivisione UNC sottostante che consente l'accesso in scrittura all'agente snapshot per la pubblicazione.  
  
 Per configurare un Sottoscrittore in modo che recuperi lo snapshot tramite FTP, impostare innanzitutto un server FTP con un account di accesso e password per l'FTP che consenta ai Sottoscrittori l'accesso in lettura per poter scaricare i file di snapshot.  
  
 Per recapitare gli snapshot tramite FTP, vedere [recapitare Snapshot tramite FTP](../../../relational-databases/replication/publish/deliver-a-snapshot-through-ftp.md).  
  
 Per informazioni sull'impostazione e modifica della password per l'accesso agli snapshot tramite FTP, vedere la sezione "Recapito di Snapshot tramite FTP" nell'argomento [proteggere il server di pubblicazione](../../../relational-databases/replication/security/secure-the-publisher.md).  
  
## Vedere anche  
 [Posizioni alternative della cartella snapshot](../../../relational-databases/replication/alternate-snapshot-folder-locations.md)   
 [Inizializzazione di una sottoscrizione con uno snapshot](../../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [Procedure consigliate per la sicurezza della replica](../../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Sicurezza e protezione & #40; Replica & #41;](../../../relational-databases/replication/security/security-and-protection-replication.md)   
 [Trasferimento di snapshot tramite FTP](../../../relational-databases/replication/transfer-snapshots-through-ftp.md)  
  
  