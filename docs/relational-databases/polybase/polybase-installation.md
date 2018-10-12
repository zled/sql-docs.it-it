---
title: Installare PolyBase in Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: polybase
ms.topic: conceptual
helpviewer_keywords:
- PolyBase, installation
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 01182a581f231ffed82be26698e8e50bf82df9e5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47842549"
---
# <a name="install-polybase-on-windows"></a>Installare PolyBase in Windows

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Per installare una versione di valutazione di SQL Server, visitare [SQL Server Valutazioni](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016). 
   
## <a name="prerequisites"></a>Prerequisites  
   
- Copia di valutazione di SQL Server a 64 bit  
   
- Microsoft .NET Framework 4.5.  

- Oracle Java SE Runtime Environment (JRE). Sono supportate la versione 7 (a partire da 7.51) e 8 (la versione [JRE](http://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html) o [JRE Server](http://www.oracle.com/technetwork/java/javase/downloads/server-jre8-downloads-2133154.html)). Passare a [Java SE downloads](http://www.oracle.com/technetwork/java/javase/downloads/index.html)(Download di Java SE). Il programma di installazione avrà esito negativo se JRE non è presente. JRE9 e JRE10 non sono supportati.

- Memoria minima: 4 GB  
   
- Spazio su disco minimo: 2 GB  
   
- Polybase funziona correttamente se è abilitato il protocollo TCP/IP. TCP/IP è abilitato per impostazione predefinita in tutte le edizioni di SQL Server tranne le edizioni Developer e SQL Server Express. Perché Polybase funzioni correttamente nelle edizioni Developer ed Express è necessario abilitare la connettività TCP/IP (vedere [Abilitare o disabilitare un protocollo di rete del server](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)).

- Un'origine dati esterna, ovvero un BLOB di Azure o un cluster Hadoop. Per le versioni supportate di Hadoop, vedere [Configurazione di PolyBase](#supported). 
- Installazione di MSVC++ 2012  

> [!NOTE]
> Se si prevede di usare la funzionalità di distribuzione di calcolo su Hadoop, è necessario assicurarsi che il cluster Hadoop di destinazione disponga dei componenti principali di HDFS, Yarn/MapReduce con server Jobhistory abilitato. PolyBase invia la query di distribuzione tramite MapReduce e recupera lo stato dal server JobHistory. Senza uno dei due componenti la query avrà esito negativo.

**Note**  

È possibile installare PolyBase in una sola istanza di SQL Server per computer.  
   
## <a name="single-node-or-polybase-scaleout-group"></a>Singolo nodo o gruppo di scalabilità orizzontale di PolyBase

Prima di iniziare a installare PolyBase nelle istanze di SQL Server, è consigliabile pianificare se si vuole eseguire un'installazione in un singolo nodo o in un gruppo con scalabilità orizzontale PolyBase. 

Per un gruppo con scalabilità orizzontale PolyBase, è necessario verificare le condizioni seguenti: 

- Tutti i computer si trovano nello stesso dominio.
- Usare lo stesso account del servizio e la stessa password durante l'installazione.
- Le istanze di SQL Server possono comunicare tra loro in rete.
- Le istanze di SQL Server sono tutte della stessa versione di SQL Server.

Dopo aver installato PolyBase in un nodo singolo o in un gruppo di scalabilità orizzontale, non sarà più possibile apportare modifiche. Sarà necessario disinstallare e reinstallare la funzionalità per modificare questa impostazione.

## <a name="install-using-the-installation-wizard"></a>Installare PolyBase tramite l'Installazione guidata  
   
1. Eseguire **Centro installazione SQL Server**. Inserire il supporto di installazione di SQL Server e fare doppio clic su **Setup.exe**.  
   
2. Fare clic su **Installazione**e quindi scegliere **Nuova installazione di SQL Server autonomo o aggiunta di funzionalità**.  
   
3. Nella pagina Selezione funzionalità scegliere **Servizio query PolyBase per i dati esterni**.  
   
4. Nella pagina Configurazione server configurare il **servizio motore PolyBase di SQL Server** e SQL Server PolyBase Data Movement Service per l'esecuzione con lo stesso account.  
   
   > **IMPORTANTE** In un gruppo con scalabilità orizzontale di PolyBase, il motore PolyBase e il servizio di spostamento dati di PolyBase su tutti i nodi devono essere eseguiti con lo stesso account di dominio.  
   > Vedere Scalabilità orizzontale di PolyBase.  
   
5. Nella **pagina Configurazione di PolyBase**selezionare una delle due opzioni. Per altre informazioni, vedere [PolyBase scale-out groups](../../relational-databases/polybase/polybase-scale-out-groups.md) (Gruppi con scalabilità orizzontale PolyBase).  
   
   - Usare un'istanza di SQL Server come istanza abilitata di PolyBase autonoma.  
   
     Scegliere questa opzione per usare l'istanza di SQL Server come nodo head autonomo.  
   
   - Usare l'istanza di SQL Server come parte di un gruppo con scalabilità orizzontale di PolyBase.  Questa opzione apre il firewall per consentire le connessioni in ingresso al motore di database di SQL Server, al motore PolyBase di SQL Server, a SQL Server PolyBase Data Movement Service e a SQL Browser. Il firewall viene aperto per consentire le connessioni in ingresso da altri nodi in un gruppo con scalabilità orizzontale di PolyBase.  
   
     Questa opzione abilita anche le connessioni al firewall di Microsoft Distributed Transaction Coordinator (MSDTC) e modifica le impostazioni del registro di MSDTC.  
   
6. Nella **pagina Configurazione di PolyBase**, specificare un intervallo di porte che comprenda almeno sei porte. L'installazione di SQL Server allocherà le prime sei porte disponibili dell'intervallo.  

<!--SQL Server 2019-->
::: moniker range=">= sql-server-ver15 || =sqlallproducts-allversions"

Dopo l'installazione, è necessario [abilitare la funzionalità PolyBase](#enable).

::: moniker-end

##  <a name="installing"></a> Installare usando un prompt dei comandi  

Usare i valori in questa tabella per creare gli script di installazione. Il **servizio motore PolyBase di SQL Server** e **SQL Server PolyBase Data Movement Service** devono essere eseguiti con lo stesso account. In un gruppo con scalabilità orizzontale di PolyBase, i servizi di PolyBase su tutti i nodi devono essere eseguiti con lo stesso account di dominio.  
   
<!--SQL Server 2016/2017-->
::: moniker range="= sql-server-2016 || = sql-server-2017"

|componente di SQL Server|Parametro e valori|Descrizione|  
|--------------------------|--------------------------|-----------------|  
|Controllo dell'installazione di SQL Server|**Required**<br /><br /> /FEATURES=PolyBase|Viene selezionata la funzionalità PolyBase.|  
|servizio motore PolyBase di SQL Server|**Facoltativo**<br /><br /> /PBENGSVCACCOUNT|Viene specificato l'account per il servizio motore. L'impostazione predefinita è **NT Authority\NETWORK SERVICE**.|  
|Motore di PolyBase per SQL Server|**Facoltativo**<br /><br /> /PBENGSVCPASSWORD|Viene specificata la password per l'account del servizio motore.|  
|Motore di PolyBase per SQL Server|**Facoltativo**<br /><br /> /PBENGSVCSTARTUPTYPE|Viene specificata la modalità di avvio per il servizio motore PolyBase: automatico (predefinito), disabilitato o manuale.|  
|SQL Server PolyBase Data Movement Service|**Facoltativo**<br /><br /> /PBDMSSVCACCOUNT|Viene specificato l'account per il servizio di spostamento dati. L'impostazione predefinita è **NT Authority\NETWORK SERVICE**.|  
|Servizio spostamento dati di PolyBase per SQL Server|**Facoltativo**<br /><br /> /PBDMSSVCPASSWORD|Viene specificata la password per l'account di spostamento dati.|  
|Servizio spostamento dati di PolyBase per SQL Server|**Facoltativo**<br /><br /> /PBDMSSVCSTARTUPTYPE|Viene specificata la modalità di avvio per il servizio di spostamento dati: automatico (predefinito), disabilitato o manuale.|  
|PolyBase|**Facoltativo**<br /><br /> /PBSCALEOUT|Viene indicato se l'istanza di SQL Server verrà usata come parte del gruppo di calcolo con scalabilità orizzontale di PolyBase. <br />Valori supportati: **True**, **False**|  
|PolyBase|**Facoltativo**<br /><br /> /PBPORTRANGE|Viene specificato un intervallo di porte con almeno 6 porte per i servizi PolyBase. Esempio:<br /><br /> `/PBPORTRANGE=16450-16460`|  

::: moniker-end
<!--SQL Server 2019-->
::: moniker range=">= sql-server-ver15 || =sqlallproducts-allversions"

|componente di SQL Server|Parametro e valori|Descrizione|  
|--------------------------|--------------------------|-----------------|  
|Controllo dell'installazione di SQL Server|**Obbligatorio**<br /><br /> /FEATURES=PolyBaseCore, PolyBaseJava, PolyBase | **PolyBaseCore** installa il supporto per tutte le funzionalità di PolyBase, ad eccezione della connettività Hadoop. **PolyBaseJava** abilita la connettività Hadoop. **PolyBase** installa entrambe le funzionalità. |  
|Motore di PolyBase per SQL Server|**Facoltativo**<br /><br /> /PBENGSVCACCOUNT|Viene specificato l'account per il servizio motore. L'impostazione predefinita è **NT Authority\NETWORK SERVICE**.|  
|Motore di PolyBase per SQL Server|**Facoltativo**<br /><br /> /PBENGSVCPASSWORD|Viene specificata la password per l'account del servizio motore.|  
|Motore di PolyBase per SQL Server|**Facoltativo**<br /><br /> /PBENGSVCSTARTUPTYPE|Viene specificata la modalità di avvio per il servizio motore PolyBase: automatico (predefinito), disabilitato o manuale.|  
|SQL Server PolyBase Data Movement Service|**Facoltativo**<br /><br /> /PBDMSSVCACCOUNT|Viene specificato l'account per il servizio di spostamento dati. L'impostazione predefinita è **NT Authority\NETWORK SERVICE**.|  
|Servizio spostamento dati di PolyBase per SQL Server|**Facoltativo**<br /><br /> /PBDMSSVCPASSWORD|Viene specificata la password per l'account di spostamento dati.|  
|Servizio spostamento dati di PolyBase per SQL Server|**Facoltativo**<br /><br /> /PBDMSSVCSTARTUPTYPE|Viene specificata la modalità di avvio per il servizio di spostamento dati: automatico (predefinito), disabilitato o manuale.|  
|PolyBase|**Facoltativo**<br /><br /> /PBSCALEOUT|Viene indicato se l'istanza di SQL Server verrà usata come parte del gruppo di calcolo con scalabilità orizzontale di PolyBase. <br />Valori supportati: **True**, **False**|  
|PolyBase|**Facoltativo**<br /><br /> /PBPORTRANGE|Viene specificato un intervallo di porte con almeno 6 porte per i servizi PolyBase. Esempio:<br /><br /> `/PBPORTRANGE=16450-16460`|  

::: moniker-end

<!--SQL Server 2019-->
::: moniker range=">= sql-server-ver15 || =sqlallproducts-allversions"

Dopo l'installazione, è necessario [abilitare la funzionalità PolyBase](#enable).

::: moniker-end

**Esempio**

Mostra un esempio di script di installazione.  

```cmd
   
Setup.exe /Q /ACTION=INSTALL /IACCEPTSQLSERVERLICENSETERMS /FEATURES=SQLEngine,Polybase   
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="\<fabric-domain>\Administrator"   
/INSTANCEDIR="C:\Program Files\Microsoft SQL Server" /PBSCALEOUT=TRUE   
/PBPORTRANGE=16450-16460 /SECURITYMODE=SQL /SAPWD="<StrongPassword>"   
/PBENGSVCACCOUNT="<DomainName>\<UserName>" /PBENGSVCPASSWORD="<StrongPassword>"   
/PBDMSSVCACCOUNT="<DomainName>\<UserName>" /PBDMSSVCPASSWORD="<StrongPassword>"  
   
```  

<!--SQL Server 2019-->
::: moniker range=">= sql-server-ver15 || =sqlallproducts-allversions"
## <a id="enable"></a> Abilitare PolyBase

A partire da SQL Server 2019 CTP 2.0, è necessario abilitare PolyBase dopo l'installazione usando il comando Transact-SQL seguente:

```sql
sp_configure @configname = 'polybase enabled', @configvalue = 1;
```

::: moniker-end

## <a name="post-installation-notes"></a>Note di post-installazione  

PolyBase installa tre database utente, DWConfiguration, DWDiagnostics e DWQueue.   I database sono destinatati all'uso con PolyBase e non devono essere modificati o eliminati.  
   
### <a id="confirminstall"></a> Come confermare l'installazione  

Eseguire il comando seguente. Se installato, PolyBase restituisce 1; in caso contrario, restituisce 0.  

```sql  
SELECT SERVERPROPERTY ('IsPolybaseInstalled') AS IsPolybaseInstalled;  
```  

### <a name="firewall-rules"></a>Regole del firewall  

L'installazione di PolyBase di SQL Server crea sul computer le regole del firewall seguenti.  
   
- PolyBase di SQL Server - Motore di database - \<NomeIstanzaSQLServer> (TCP-In)  
   
- PolyBase di SQL Server - Servizi PolyBase - \<NomeIstanzaSQLServer> (TCP-In)  

- PolyBase di SQL Server - SQL Browser - (UDP-In)  
   
Al momento dell'installazione, se si sceglie di usare l'istanza di SQL Server come parte di un gruppo di scalabilità orizzontale di PolyBase, queste regole vengono attivate e il firewall si apre per consentire le connessioni in ingresso al motore di database di SQL Server, al motore PolyBase di SQL Server, a SQL Server PolyBase Data Movement Service e a SQL Browser. Tuttavia, se il servizio Firewall nel computer non è in esecuzione durante l'installazione, l'installazione di SQL Server non è in grado di attivare queste regole. In tal caso, è necessario avviare il servizio Firewall sul computer e abilitare queste regole dopo l'installazione.  
   
#### <a name="to-enable-the-firewall-rules"></a>Per abilitare le regole del firewall  

- Aprire il **Pannello di controllo**.  

- Fare clic su **Sistema e sicurezza**e quindi su **Windows Firewall**.  
   
- Fare clic su **Impostazioni avanzate**e quindi su **Regole connessioni in entrata**.  
   
- Fare clic con il pulsante destro del mouse sulla regola disattivata e scegliere **Abilita regola**.  
   
### <a name="polybase-service-accounts"></a>Account del servizio PolyBase

Per modificare gli account del servizio per il motore PolyBase e PolyBase Data Movement Service, disinstallare e reinstallare la funzionalità PolyBase.

## <a name="next-steps"></a>Passaggi successivi  

Vedere [PolyBase configuration](../../relational-databases/polybase/polybase-configuration.md).
