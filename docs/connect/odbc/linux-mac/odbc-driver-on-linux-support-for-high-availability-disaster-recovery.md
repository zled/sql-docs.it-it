---
title: "Driver ODBC in Linux e macOS - disponibilità elevata e ripristino di emergenza | Documenti Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa656c5b-a935-40bf-bc20-e517ca5cd0ba
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d7b6c72d350b718a7676bffd72c261b7cfa72667
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="odbc-driver-on-linux-and-macos-support-for-high-availability-and-disaster-recovery"></a>Driver ODBC in Linux e macOS il supporto per la disponibilità elevata e ripristino di emergenza
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Il driver ODBC per il supporto di Linux e macOS [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)]. Per ulteriori informazioni su [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)], vedere:  
  
-   [Listener del gruppo di disponibilità, connettività Client e Failover dell'applicazione (SQL Server)](http://msdn.microsoft.com/library/hh213417.aspx)  
  
-   [Creazione e configurazione di gruppi di disponibilità (SQL Server)](http://msdn.microsoft.com/library/ff878265.aspx)  
  
-   [Clustering di failover e gruppi di disponibilità AlwaysOn (SQL Server)](http://msdn.microsoft.com/library/ff929171.aspx)  
  
-   [Repliche secondarie attive: Repliche secondarie leggibili (gruppi di disponibilità AlwaysOn)](http://msdn.microsoft.com/library/ff878253.aspx)  
  
È possibile specificare il listener di un determinato gruppo di disponibilità nella stringa di connessione. Se un'applicazione ODBC in Linux o macOS è connesso a un database in un gruppo di disponibilità che esegue il failover, la connessione originale viene interrotta e l'applicazione deve aprire una nuova connessione per continuare a funzionare dopo il failover.

Il driver ODBC in Linux e macOS scorrere in sequenza tutti gli indirizzi IP associati a un nome host DNS se non si connette a un listener del gruppo di disponibilità e più indirizzi IP sono associati con il nome host.

Se il primo indirizzo IP restituito del server DNS non è collegabile, queste iterazioni possono richiedere molto tempo. Quando ci si connette a un listener del gruppo di disponibilità, il driver tenta di stabilire connessioni a tutti gli indirizzi IP in parallelo. Se un tentativo di connessione ha esito positivo, il driver ignora tutti i tentativi di connessione in sospeso.

> [!NOTE]  
> Poiché una connessione può non riuscire a causa di un failover del gruppo di disponibilità, implementare una logica di ripetizione tentare una connessione non riuscita fino a quando la connessione viene ristabilita. L'aumento del timeout di connessione e l'implementazione di una logica di ripetizione dei tentativi per le connessioni aumentano le probabilità di connessione a un gruppo di disponibilità.

## <a name="connecting-with-multisubnetfailover"></a>Connessione con MultiSubnetFailover

Specificare sempre **MultiSubnetFailover = Yes** (o **= True**) durante la connessione a un [!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)] listener del gruppo di disponibilità o [!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)] istanza Cluster di Failover. **MultiSubnetFailover** consente il failover più veloce per tutti i gruppi di disponibilità e istanza del cluster di failover in [!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)]. **MultiSubnetFailover** riduce anche notevolmente il tempo di failover per le topologie AlwaysOn singole e su più subnet. Durante un failover su più subnet, vengono tentate connessioni in parallelo da parte del client. Durante un failover della subnet, il driver Ritenta in modo insistente la connessione TCP.

La proprietà di connessione **MultiSubnetFailover** indica che l'applicazione è in corso di distribuzione in un gruppo di disponibilità o in un'istanza del cluster di failover. Il driver tenta di connettersi al database del server primario [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] istanza tentando di connettersi a tutti gli IP indirizzi. Quando ci si connette con **MultiSubnetFailover = Yes**, il client riesegue i tentativi di connessione TCP più velocemente rispetto a intervalli di ritrasmissione TCP predefinita del sistema operativo. Dopo il failover,**MultiSubnetFailover = Yes** consente una riconnessione più veloce di un gruppo di disponibilità AlwaysOn o di un'istanza del cluster di failover AlwaysOn. **MultiSubnetFailover = Yes** si applica a singolo e con più subnet gruppi di disponibilità sia istanze Cluster di Failover.  

Usare **MultiSubnetFailover=Yes** in caso di connessione al listener di un gruppo di disponibilità o a un'istanza del cluster di failover. In caso contrario, le prestazioni dell'applicazione possono essere influenzate negativamente.

Quando ci si connette a un server in un gruppo di disponibilità o l'istanza del Cluster di Failover, tenere presente quanto segue:
  
-   Specificare **MultiSubnetFailover = Yes** per migliorare le prestazioni durante la connessione a una singola subnet o un gruppo di disponibilità su più subnet.

-   Specificare il listener del gruppo di disponibilità del gruppo di disponibilità del server nella stringa di connessione.
  
-   È possibile connettersi a un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] istanza configurata con più di 64 indirizzi IP.

-   Entrambi [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] o dall'autenticazione Kerberos può essere utilizzato con **MultiSubnetFailover = Yes** senza modificare il comportamento dell'applicazione.

-   È possibile aumentare il valore di **loginTimeout** per adattarlo alla durata del failover e ridurre il numero di nuovi tentativi di connessione dell'applicazione.

-   Le transazioni distribuite non sono supportate.  
  
Se il routing di sola lettura non è attivo, non è possibile stabilire una connessione a un percorso di replica secondaria in un gruppo di disponibilità nelle situazioni seguenti:  
  
1.  Se il percorso di replica secondaria non è configurato per accettare le connessioni.  
  
2.  Se un'applicazione usa **ApplicationIntent=ReadWrite** e il percorso di replica secondaria è configurato per l'accesso in sola lettura.  
  
Una connessione non riesce se una replica primaria è configurata per rifiutare i carichi di lavoro di sola lettura e la stringa di connessione contiene **ApplicationIntent=ReadOnly**.  
  
## <a name="specifying-application-intent"></a>Specificazione della finalità dell'applicazione  
Se **ApplicationIntent=ReadOnly**, il client richiede un carico di lavoro di lettura quando si connette a un database abilitato per AlwaysOn. Il server applica la finalità al momento della connessione e durante un'istruzione USE database, ma solo a un database AlwaysOn abilitato.

La parola chiave **ApplicationIntent** non funziona con i database legacy di sola lettura.  

Un database può consentire o impedire carichi di lavoro di lettura nel database AlwaysOn di destinazione. (Utilizzare il **ALLOW_CONNECTIONS** clausola del **PRIMARY_ROLE** e **SECONDARY_ROLE** [!INCLUDE[tsql](../../../includes/tsql_md.md)] istruzioni.)  
  
La parola chiave **ApplicationIntent** è usata per abilitare il routing di sola lettura.  
  
## <a name="read-only-routing"></a>Routing di sola lettura  
Il routing di sola lettura è una funzionalità che può garantire la disponibilità di una replica di sola lettura di un database. Per abilitare il routing di sola lettura:  
  
1.  Connettersi a un listener del gruppo di disponibilità Always On.  
  
2.  La parola chiave della stringa di connessione **ApplicationIntent** deve essere impostata su **ReadOnly**.  
  
3.  L'amministratore del database deve configurare il gruppo di disponibilità in modo da abilitare il routing di sola lettura.  
  
È possibile che più connessioni che usano il routing di sola lettura si connettano a diverse repliche di sola lettura. Le modifiche nella sincronizzazione del database o nella configurazione di routing del server possono comportare connessioni client a repliche di sola lettura diverse. Per assicurare la connessione di tutte le richieste di sola lettura alla stessa replica di sola lettura, non passare un listener del gruppo di disponibilità alla parola chiave di connessione **Server** . Specificare invece il nome dell'istanza di sola lettura.  
  
Prevedere tempi di connessione maggiori con il routing di sola lettura rispetto alla connessione al database primario. Pertanto, aumentare il timeout di accesso. Il routing di sola lettura si connette prima al database primario e quindi cerca il miglior database secondario leggibile disponibile.  
  
## <a name="odbc-syntax"></a>Sintassi ODBC

Due parole chiave di stringa di connessione ODBC supportano [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)]:  
  
-   **ApplicationIntent**  
  
-   **MultiSubnetFailover**  
  
Per altre informazioni sulle parole chiave di stringa di connessione ODBC, vedere [Utilizzo delle parole chiave delle stringhe di connessione con SQL Server Native Client](http://msdn.microsoft.com/library/ms130822.aspx).  
  
Gli attributi di connessione equivalenti sono:
  
-   **SQL_COPT_SS_APPLICATION_INTENT**  
  
-   **SQL_COPT_SS_MULTISUBNET_FAILOVER**  
  
Per ulteriori informazioni sugli attributi di connessione ODBC, vedere [SQLSetConnectAttr](http://msdn.microsoft.com/library/ms131709.aspx).  
  
Un'applicazione ODBC che utilizza [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)] per stabilire la connessione può utilizzare una delle due funzioni:  
  
|Funzione|Description|  
|------------|---------------|  
|[Funzione SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|**SQLConnect** supporta sia **ApplicationIntent** e **MultiSubnetFailover** tramite un nome origine dati (DSN) o un attributo di connessione.|  
|[Funzione SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|**SQLDriverConnect** supporta **ApplicationIntent** e **MultiSubnetFailover** tramite l'attributo di connessione, parola chiave di stringa di connessione o DSN.|
  
## <a name="see-also"></a>Vedere anche  

[Parole chiave delle stringhe di connessione e nomi delle origini dati (DSN)](../../../connect/odbc/linux-mac/connection-string-keywords-and-data-source-names-dsns.md)

[Linee guida per la programmazione](../../../connect/odbc/linux-mac/programming-guidelines.md)

[Note sulla versione](../../../connect/odbc/linux-mac/release-notes.md)  

