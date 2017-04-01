---
title: "Transazioni tra database non supportate per il mirroring del database o i gruppi di disponibilit&#224; Always On (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "mirroring del database [SQL Server], interoperabilità"
  - "transazioni tra database [SQL Server]"
  - "transazioni [mirroring del database]"
  - "Gruppi di disponibilità [SQL Server], interoperabilità"
  - "risoluzione di problemi [SQL Server], transazioni tra database"
ms.assetid: 9f7ed895-ad65-43e3-ba08-00d7bff1456d
caps.latest.revision: 33
ms.author: "mikeray"
manager: "jhubbard"
---
# Transazioni tra database non supportate per il mirroring del database o i gruppi di disponibilit&#224; Always On (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Questo argomento descrive il supporto delle transazioni tra database e delle transazioni distribuite per i gruppi di disponibilità Always On e il mirroring del database.  
  
## Supporto delle transazioni tra database nella stessa istanza di SQL Server  
Le transazioni tra database all'interno della stessa istanza di SQL Server non sono supportate per i gruppi di disponibilità Always On (SQL Server). Ciò significa che due database in una transazione tra database non possono essere ospitati dalla stessa istanza di SQL Server. Questo vale anche se tali database fanno parte dello stesso gruppo di disponibilità.  
  
Anche le transazioni tra database non sono supportate per il mirroring del database.  
  
##  <a name="dtcsupport"></a> Supporto delle transazioni distribuite  
Le transazioni distribuite sono supportate con Gruppi di disponibilità Always On. Questo vale per le transazioni distribuite tra database ospitati da due istanze diverse di SQL Server. Si applica anche alle transazioni distribuite tra SQL Server e un altro server conforme a DTC.  
 
Microsoft Distributed Transaction Coordinator (MSDTC o DTC) è un servizio Windows che offre l'infrastruttura delle transazioni per i sistemi distribuiti. MSDTC consente alle applicazioni client di includere più origini dati in un'unica transazione di cui viene quindi eseguito il commit in tutti i server inclusi nella transazione. Ad esempio, è possibile usare MSDTC per coordinare le transazioni che interessano più database in server diversi.

Una nuova funzionalità di SQL Server 2016 consente di usare le transazioni distribuite nei casi in cui uno o più database della transazione sono inclusi in un gruppo di disponibilità. Nelle versioni precedenti a SQL Server 2016 le transazioni distribuite non erano supportate per i database inclusi in gruppi di disponibilità. SQL Server 2016 può registrare un gestore risorse per ogni database. Questa nuova funzionalità permette alle transazioni distribuite di includere database di gruppi di disponibilità.

  
 Devono essere soddisfatti i requisiti seguenti:  
  
-   Gruppi di disponibilità deve essere in esecuzione in Windows Server 2012 R2 o Windows Server 2016. Per Windows Server 2012 R2, è necessario installare l'aggiornamento in KB3090973 disponibile all'indirizzo [https://support.microsoft.com/en-us/kb/3090973](https://support.microsoft.com/en-us/kb/3090973).  
  
-   I gruppi di disponibilità devono essere creati con il comando **CREATE AVAILABILITY GROUP** e la clausola **WITH DTC_SUPPORT = PER_DB**. Attualmente non è possibile modificare un gruppo di disponibilità esistente.  

- Tutte le istanze di SQL Server che verranno incluse nel gruppo di disponibilità devono essere SQL Server 2016 o versioni successive.
  
 
 ## Transazioni distribuite non supportate
 I casi specifici in cui le transazioni distribuite non sono supportate includono:
 
 -  Casi in cui più database coinvolti nella transazione sono inclusi nello stesso gruppo di disponibilità.
 
 -  Casi in cui è presente almeno un database in un gruppo di disponibilità e un altro database nella stessa istanza di SQL Server. 
 
 -  Casi in cui il gruppo di disponibilità non è stato creato con la transazione distribuita abilitata.
 
 -  Mirroring del database.
 
 ## Consiglio
 Negli ambienti di produzione è necessario inserire il servizio DTC nel cluster. Se il servizio DTC non viene inserito nel cluster, SQL Server userà il servizio DTC locale. Con il servizio DTC locale, si riduce la disponibilità complessiva della soluzione. Quando il servizio DTC viene inserito nel cluster, le transazioni in-process possono essere recuperate se il nodo del cluster ha esito negativo.
 
 > [!IMPORTANT]
 > Determinare il risultato predefinito appropriato delle transazioni che DTC non riesce a risolvere per il proprio ambiente.  Per informazioni su come configurare il risultato predefinito, vedere [Opzione di configurazione del server in-doubt xact resolution](../../../database-engine/configure-windows/in-doubt-xact-resolution-server-configuration-option.md).
  
## Scenario di esempio con mirroring del database  
 Nell'esempio di mirroring del database seguente si illustra come può verificarsi un'incoerenza logica. In questo esempio un'applicazione utilizza una transazione tra database per inserire due righe di dati. Una riga viene inserita in una tabella in un database con mirroring, A, l'altra viene inserita in un altro database, B. Il database A viene sottoposto a mirroring in modalità a protezione elevata con failover automatico. Durante il commit della transazione, il database A diventa non disponibile e viene automaticamente eseguito il failover della sessione di mirroring sul mirror del database A.  
  
 Dopo il failover, è possibile che il commit della transazione tra database abbia esito positivo sul database B, ma non sul database di cui è stato eseguito il failover. Questa situazione si verifica qualora il server principale originale del database A non abbia inviato il log per la transazione tra database al server mirror prima dell'errore. Dopo il failover, tale transazione non è più presente nel nuovo server principale. I database A e B diventano incoerenti perché i dati inseriti nel database B rimangono inalterati, mentre quelli inseriti nel database A sono stati persi.  
  
 Uno scenario analogo può verificarsi quando si utilizza una transazione MS DTC. Ad esempio, dopo il failover, il nuovo server principale contatta MS DTC. MS DTC, tuttavia, non rileva il nuovo server principale e termina tutte le transazioni di cui si sta preparando il commit e per le quali in altri database il commit viene considerato eseguito.  
  
> [!NOTE]  
>  L'uso del mirroring del database con DTC o di Gruppi di disponibilità Always On con DTC in modi non approvati in questo argomento non è supportato.  Ciò non implica che gli aspetti del prodotto non correlati a DTC non sono supportati, ma i problemi causati dall'uso improprio delle transazioni distribuite non saranno supportati.  
  
## Vedere anche  
 [Gruppi di disponibilità Always On: interoperabilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/always-on-availability-groups-interoperability-sql-server.md)  
  
  