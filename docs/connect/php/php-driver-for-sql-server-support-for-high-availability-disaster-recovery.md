---
title: Supporto per la disponibilità elevata, ripristino di emergenza per i driver Microsoft per PHP per SQL Server | Documenti Microsoft
ms.custom: ''
ms.date: 04/04/2018
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 73a80821-d345-4fea-b076-f4aabeb4af3e
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 11352389bb76440bfec32eae185d64550c249fc8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="support-for-high-availability-disaster-recovery"></a>Supporto per il ripristino di emergenza a disponibilità elevata
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

In questo argomento viene [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] supporto (aggiunto nella versione 3.0) per il ripristino di emergenza a disponibilità elevata [!INCLUDE[ssHADR](../../includes/sshadr_md.md)].  Il supporto [!INCLUDE[ssHADR](../../includes/sshadr_md.md)] è stato aggiunto in [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)]. Per altre informazioni su [!INCLUDE[ssHADR](../../includes/sshadr_md.md)], vedere la documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
Nella versione 3.0 del [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], è possibile specificare il listener del gruppo di disponibilità di un (disponibilità elevata, ripristino di emergenza) del gruppo di disponibilità (AG) nella proprietà di connessione. Se un [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] applicazione è connessa a un database AlwaysOn che esegue il failover, la connessione originale viene interrotta e l'applicazione deve aprire una nuova connessione per continuare a funzionare dopo il failover.  
  
Se non ci si connette a un listener del gruppo di disponibilità e se più indirizzi IP sono associati a un nome host, il [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] scorrerà in sequenza tutti gli indirizzi IP associati alla voce DNS. Questa operazione può richiedere tempi lunghi se il primo indirizzo IP restituito dal server DNS non è associato ad alcuna scheda di interfaccia di rete. Quando ci si connette a un listener del gruppo di disponibilità, il [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] tenta di stabilire connessioni a tutti gli indirizzi IP in parallelo e se un tentativo ha esito positivo, il driver rimuove tutti i tentativi di connessione in sospeso.  
  
> [!NOTE]  
> L'aumento del timeout di connessione e l'implementazione della logica di riesecuzione per le connessioni aumentano le probabilità che un'applicazione si connetta a un gruppo di disponibilità. Inoltre, poiché potrebbe non essere possibile stabilire una connessione a causa del failover di un gruppo di disponibilità, è opportuno implementare la logica di riesecuzione delle connessioni, finché non si ottiene la riconnessione.  
  
## <a name="connecting-with-multisubnetfailover"></a>Connessione con MultiSubnetFailover  
Il **MultiSubnetFailover** proprietà di connessione indica che l'applicazione viene distribuita in un gruppo di disponibilità o l'istanza del Cluster di Failover e che il [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] tenterà di connettersi al database del server primario [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] istanza tentando di connettersi a tutti gli IP indirizzi. Quando **MultiSubnetFailover = true** specificato per una connessione, il client riesegue i tentativi di connessione TCP più velocemente rispetto a intervalli di ritrasmissione TCP predefinita del sistema operativo. In tal modo si abilita la riconnessione a seguito di failover di un gruppo di disponibilità AlwaysOn o un'istanza del cluster di failover AlwaysOn ed è applicabile a istanze del cluster di failover o a gruppi di disponibilità su una singola subnet o su più subnet.  
  
Specificare sempre **MultiSubnetFailover = True** quando ci si connette a un listener del gruppo di disponibilità di SQL Server 2012 o di un Cluster di failover di SQL Server 2012. **MultiSubnetFailover** consente il failover più veloce per tutti i gruppi di disponibilità e istanza del cluster di failover di SQL Server 2012 e di ridurre significativamente il tempo di failover per le topologie AlwaysOn singole e su più subnet. Durante un failover su più subnet, verranno tentate connessioni in parallelo da parte del client. Durante un failover della subnet, il [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] riproverà continuamente la connessione TCP.  
  
Per ulteriori informazioni sulle parole chiave di stringa di connessione in [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], vedere [le opzioni di connessione](../../connect/php/connection-options.md).  
  
Che specifica **MultiSubnetFailover = true** quando ci si connette a un elemento diverso da un listener del gruppo di disponibilità o l'istanza del Cluster di Failover può comportare un impatto negativo sulle prestazioni e non è supportata.  
  
Utilizzare le linee guida seguenti per connettersi a un server in un gruppo di disponibilità:  
  
-   Usare la proprietà di connessione **MultiSubnetFailover** in caso di connessione a una singola subnet o a più subnet, in modo da migliorare le prestazioni.  
  
-   Per eseguire la connessione a un gruppo di disponibilità, specificare il listener del gruppo di disponibilità come server nella stringa di connessione.  
  
-   La connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] configurata con più di 64 indirizzi IP determinerà un errore di connessione.  
  
-   Il comportamento di un'applicazione in cui viene usata la proprietà di connessione **MultiSubnetFailover** non è influenzato dal tipo di autenticazione, cioè dall'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], dall'autenticazione Kerberos, o dall’autenticazione di Windows.  
  
-   Aumentare il valore di **loginTimeout** per adattarlo alla durata del failover e ridurre i ripetuti tentativi di connessione dell'applicazione.  
  
-   Le transazioni distribuite non sono supportate.  
  
Se il routing di sola lettura non è attivo, non è possibile stabilire una connessione a un percorso di replica secondaria in un gruppo di disponibilità nelle situazioni seguenti:  
  
1.  Se il percorso di replica secondaria non è configurato per accettare le connessioni.  
  
2.  Se un'applicazione usa **ApplicationIntent=ReadWrite** (vedere di seguito) e il percorso di replica secondaria è configurato per l'accesso in sola lettura.  
  
Una connessione non riesce se una replica primaria è configurata per rifiutare i carichi di lavoro in sola lettura e la stringa di connessione contiene **ApplicationIntent=ReadOnly**.  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>Aggiornamento per l'utilizzo di cluster su più subnet dal mirroring del database  
Si verificherà un errore di connessione se nella stringa di connessione sono presenti le parole chiave di connessione **MultiSubnetFailover** e **Failover_Partner**. Si verificherà un errore anche se viene usato **MultiSubnetFailover** e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] restituisce una risposta del partner di failover in cui viene indicato che fa parte di una coppia del mirroring del database.  
  
Se si aggiorna un [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] applicazione che utilizza il mirroring del database a uno scenario su più subnet, è necessario rimuovere il **Failover_Partner** proprietà di connessione e sostituirla con **MultiSubnetFailover**  impostato su **Sì** e sostituire il nome del server nella stringa di connessione con un listener del gruppo di disponibilità. Se viene utilizzata una stringa di connessione **Failover_Partner** e **MultiSubnetFailover = true**, il driver genererà un errore. Tuttavia, se viene utilizzata una stringa di connessione **Failover_Partner** e **MultiSubnetFailover = false** (o **ApplicationIntent = ReadWrite**), l'applicazione utilizzerà database il mirroring.  
  
Il driver restituirà un errore se il mirroring del database viene utilizzato nel database primario del gruppo di disponibilità e **MultiSubnetFailover = true** viene utilizzata nella stringa di connessione che si connette a un database primario anziché a un gruppo di disponibilità listener.  


[!INCLUDE[specify-application-intent_read-only-routing](~/includes/paragraph-content/specify-application-intent-read-only-routing.md)]


## <a name="see-also"></a>Vedere anche  
[Connessione al server](../../connect/php/connecting-to-the-server.md)  
  
