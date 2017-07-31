---
title: Installazione di PolyBase | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 08/31/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-polybase
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PolyBase, installation
ms.assetid: 3a1e64be-9bfc-4408-accd-35990e1a6b52
caps.latest.revision: 25
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 6aa73e749d4f308265dfe27a160802c15a391a3e
ms.openlocfilehash: 9a4f230e8c25a24f85f36f3a1aaf82fbf247cd9a
ms.contentlocale: it-it
ms.lasthandoff: 07/31/2017

---
# <a name="polybase-installation"></a>Installazione di PolyBase
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Per installare una versione di valutazione di SQL Server, visitare [SQL Server Valutazioni](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016). 
  
## <a name="prerequisites"></a>Prerequisiti  
  
-   Copia di valutazione di SQL Server a 64 bit  
  
-   Microsoft .NET Framework 4.5.  
  
-   Oracle Java SE RunTime Environment (JRE) versione 7.51 o successiva (64 bit) (è valido sia [JRE](http://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html) che [JRE Server](http://www.oracle.com/technetwork/java/javase/downloads/server-jre8-downloads-2133154.html) ). Passare a [Java SE downloads](http://www.oracle.com/technetwork/java/javase/downloads/index.html)(Download di Java SE). Il programma di installazione avrà esito negativo se JRE non è presente.  
  
-   Memoria minima: 4 GB  
  
-   Spazio su disco minimo: 2 GB  
  
-   Polybase funziona correttamente se è abilitato il protocollo TCP/IP. TCP/IP è abilitato per impostazione predefinita in tutte le edizioni di SQL Server tranne le edizioni Developer e SQL Server Express. Perché Polybase funzioni correttamente nelle edizioni Developer ed Express è necessario abilitare la connettività TCP/IP (vedere [Abilitare o disabilitare un protocollo di rete del server](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)).
  
 **Note**  
  
 È possibile installare PolyBase in una sola istanza di SQL Server per computer.  
  
## <a name="single-node-or-polybase-scaleout-group"></a>Singolo nodo o gruppo di scalabilità orizzontale di PolyBase
Prima di iniziare a installare PolyBase nelle istanze di SQL Server, è consigliabile pianificare se si desidera eseguire un'installazione in un singolo nodo o in un gruppo di scalabilità orizzontale di PolyBase. Per un gruppo di scalabilità orizzontale di PolyBase, è necessario verificare le condizioni seguenti. 
- Tutti i computer si trovano nello stesso dominio.
- Usare lo stesso account del servizio e la stessa password durante l'installazione.
- Le istanze di SQL Server possono comunicare tra loro in rete.

Dopo aver installato PolyBase in un nodo singolo o in un gruppo di scalabilità orizzontale, non sarà più possibile apportare modifiche. Sarà necessario disinstallare e reinstallare la funzionalità per modificare questa impostazione.

## <a name="install-using-the-installation-wizard"></a>Installare PolyBase tramite l'Installazione guidata  
  
1.  Eseguire **Centro installazione SQL Server**. Inserire il supporto di installazione di SQL Server e fare doppio clic su **Setup.exe**.  
  
2.  Fare clic su **Installazione**e quindi scegliere **Nuova installazione di SQL Server autonomo o aggiunta di funzionalità**.  
  
3.  Nella pagina Selezione funzionalità scegliere **Servizio query PolyBase per i dati esterni**.  
  
4.  Nella pagina Configurazione server configurare il **servizio motore PolyBase di SQL Server** e SQL Server PolyBase Data Movement Service per l'esecuzione con lo stesso account.  
  
    > **IMPORTANTE** In un gruppo con scalabilità orizzontale di PolyBase, il motore PolyBase e il servizio di spostamento dati di PolyBase su tutti i nodi devono essere eseguiti con lo stesso account di dominio.  
    > Vedere Scalabilità orizzontale di PolyBase.  
  
5.  Nella **pagina Configurazione di PolyBase**selezionare una delle due opzioni. Per altre informazioni, vedere [PolyBase scale-out groups](../../relational-databases/polybase/polybase-scale-out-groups.md) (Gruppi con scalabilità orizzontale PolyBase).  
  
    -   Usare un'istanza di SQL Server come istanza abilitata di PolyBase autonoma.  
  
         Scegliere questa opzione per usare l'istanza di SQL Server come nodo head autonomo.  
  
    -   Usare l'istanza di SQL Server come parte di un gruppo con scalabilità orizzontale di PolyBase.  Questa opzione apre il firewall per consentire le connessioni in ingresso al motore di database di SQL Server, al motore PolyBase di SQL Server, a SQL Server PolyBase Data Movement Service e a SQL Browser. Il firewall viene aperto per consentire le connessioni in ingresso da altri nodi in un gruppo con scalabilità orizzontale di PolyBase.  
  
         Questa opzione abilita anche le connessioni al firewall di Microsoft Distributed Transaction Coordinator (MSDTC) e modifica le impostazioni del registro di MSDTC.  
  
6.  Nella **pagina Configurazione di PolyBase**, specificare un intervallo di porte che comprenda almeno sei porte. L'installazione di SQL Server allocherà le prime sei porte disponibili dell'intervallo.  
  
##  <a name="installing"></a> Installare usando un prompt dei comandi  
 Usare i valori in questa tabella per creare gli script di installazione. Il **servizio motore PolyBase di SQL Server** e **SQL Server PolyBase Data Movement Service** devono essere eseguiti con lo stesso account. In un gruppo con scalabilità orizzontale di PolyBase, i servizi di PolyBase su tutti i nodi devono essere eseguiti con lo stesso account di dominio.  
  
|componente di SQL Server|Parametro e valori|Descrizione|  
|--------------------------|--------------------------|-----------------|  
|Controllo dell'installazione di SQL Server|**Required**<br /><br /> /FEATURES=PolyBase|Viene selezionata la funzionalità PolyBase.|  
|servizio motore PolyBase di SQL Server|**Facoltativo**<br /><br /> /PBENGSVCACCOUNT|Viene specificato l'account per il servizio motore. L'impostazione predefinita è **NT Authority\NETWORK SERVICE**.|  
|servizio motore PolyBase di SQL Server|**Facoltativo**<br /><br /> /PBENGSVCPASSWORD|Viene specificata la password per l'account del servizio motore.|  
|servizio motore PolyBase di SQL Server|**Facoltativo**<br /><br /> /PBENGSVCSTARTUPTYPE|Viene specificata la modalità di avvio per il servizio motore PolyBase: automatico (predefinito), disabilitato o manuale.|  
|SQL Server PolyBase Data Movement Service|**Facoltativo**<br /><br /> /PBDMSSVCACCOUNT|Viene specificato l'account per il servizio di spostamento dati. L'impostazione predefinita è **NT Authority\NETWORK SERVICE**.|  
|SQL Server PolyBase Data Movement Service|**Facoltativo**<br /><br /> /PBDMSSVCPASSWORD|Viene specificata la password per l'account di spostamento dati.|  
|SQL Server PolyBase Data Movement Service|**Facoltativo**<br /><br /> /PBDMSSVCSTARTUPTYPE|Viene specificata la modalità di avvio per il servizio di spostamento dati: automatico (predefinito), disabilitato o manuale.|  
|PolyBase|**Facoltativo**<br /><br /> /PBSCALEOUT|Viene indicato se l'istanza di SQL Server verrà usata come parte del gruppo di calcolo con scalabilità orizzontale di PolyBase. <br />Valori supportati: **True**, **False**|  
|PolyBase|**Facoltativo**<br /><br /> /PBPORTRANGE|Viene specificato un intervallo di porte con almeno 6 porte per i servizi PolyBase. Esempio:<br /><br /> `/PBPORTRANGE=16450-16460`|  
  
 **Esempio**  
  
 Mostra un esempio di script di installazione.  
  
```  
  
Setup.exe /Q /ACTION=INSTALL /IACCEPTSQLSERVERLICENSETERMS /FEATURES=SQLEngine,Polybase   
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="\<fabric-domain>\Administrator"   
/INSTANCEDIR="C:\Program Files\Microsoft SQL Server" /PBSCALEOUT=TRUE   
/PBPORTRANGE=16450-16460 /SECURITYMODE=SQL /SAPWD="<StrongPassword>"   
/PBENGSVCACCOUNT="<DomainName>\<UserName>" /PBENGSVCPASSWORD="<StrongPassword>"   
/PBDMSSVCACCOUNT="<DomainName>\<UserName>" /PBDMSSVCPASSWORD="<StrongPassword>"  
  
```  
  
## <a name="post-installation-notes"></a>Note di post-installazione  
 PolyBase installa tre database utente, DWConfiguration, DWDiagnostics e DWQueue.   I database sono destinatati all'uso con PolyBase e non devono essere modificati o eliminati.  
  
### <a name="how-to-confirm-installation"></a>Procedura per confermare l'installazione  
 Eseguire il comando seguente. Se installato, PolyBase restituisce 1; in caso contrario, restituisce 0.  
  
```tsql  
SELECT SERVERPROPERTY ('IsPolybaseInstalled') AS IsPolybaseInstalled;  
```  
  
### <a name="firewall-rules"></a>Regole del firewall  
 L'installazione di PolyBase di SQL Server crea sul computer le regole del firewall seguenti.  
  
-   PolyBase di SQL Server - Motore di database - \<NomeIstanzaSQLServer> (TCP-In)  
  
-   PolyBase di SQL Server - Servizi PolyBase - \<NomeIstanzaSQLServer> (TCP-In)  
  
-   PolyBase di SQL Server - SQL Browser - (UDP-In)  
  
 Al momento dell'installazione, se si sceglie di usare l'istanza di SQL Server come parte di un gruppo di scalabilità orizzontale di PolyBase, queste regole vengono attivate e il firewall si apre per consentire le connessioni in ingresso al motore di database di SQL Server, al motore PolyBase di SQL Server, a SQL Server PolyBase Data Movement Service e a SQL Browser. Tuttavia, se il servizio Firewall nel computer non è in esecuzione durante l'installazione, l'installazione di SQL Server non è in grado di attivare queste regole. In tal caso, è necessario avviare il servizio Firewall sul computer e abilitare queste regole dopo l'installazione.  
  
#### <a name="to-enable-the-firewall-rules"></a>Per abilitare le regole del firewall  
  
-   Aprire il **Pannello di controllo**.  
  
-   Fare clic su **Sistema e sicurezza**e quindi su **Windows Firewall**.  
  
-   Fare clic su **Impostazioni avanzate**e quindi su **Regole connessioni in entrata**.  
  
-   Fare clic con il pulsante destro del mouse sulla regola disattivata e scegliere **Abilita regola**.  
  
### <a name="polybase-service-accounts"></a>Account del servizio PolyBase
Per modificare gli account del servizio per il motore PolyBase e PolyBase Data Movement Service, disinstallare e reinstallare la funzionalità PolyBase.
   
## <a name="next-steps"></a>Passaggi successivi  
 Vedere [PolyBase configuration](../../relational-databases/polybase/polybase-configuration.md).  
  
  

