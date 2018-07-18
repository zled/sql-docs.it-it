---
title: Distribuire un cluster Pacemaker per SQL Server in Linux | Documenti Microsoft
description: In questa esercitazione viene illustrato come distribuire un cluster Pacemaker per SQL Server in Linux.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 12/11/2017
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: 239d4418c5e7d59a980d9028e2533dd9d7a2c566
ms.sourcegitcommit: fc3cd23685c6b9b6972d6a7bab2cc2fc5ebab5f2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/25/2018
---
# <a name="deploy-a-pacemaker-cluster-for-sql-server-on-linux"></a>Distribuire un cluster Pacemaker per SQL Server in Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In questa esercitazione illustra le attività necessarie per distribuire un cluster Linux Pacemaker per un [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] sempre nel gruppo di disponibilità (AG) o l'istanza del cluster di failover (FCI). A differenza dei Server Windows accoppiamento /[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] dello stack, la creazione di cluster Pacemaker, nonché configurazione gruppo di disponibilità in Linux può essere eseguita prima o dopo l'installazione di [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]. Dopo aver configurato il cluster, viene eseguita l'integrazione e la configurazione delle risorse per la parte Pacemaker di una distribuzione del gruppo di disponibilità o FCI.
> [!IMPORTANT]
> Un gruppo di disponibilità con un tipo di cluster None *non* richiede un cluster Pacemaker, né possono essere gestito da Pacemaker. 

> [!div class="checklist"]
> * Installare il componente aggiuntivo la disponibilità elevata e Pacemaker.
> * Preparare i nodi per Pacemaker (RHEL e Ubuntu solo).
> * Creare il cluster Pacemaker.
> * Installare i pacchetti di SQL Server a disponibilità elevata e SQL Server Agent.
 
## <a name="prerequisite"></a>Prerequisiti
[Installazione di SQL Server 2017](sql-server-linux-setup.md).

## <a name="install-the-high-availability-add-on"></a>Installare il componente aggiuntivo la disponibilità elevata
Utilizzare la sintassi seguente per installare i pacchetti che costituiscono il componente aggiuntivo a disponibilità elevata (HA) per ogni distribuzione di Linux. 

**Red Hat Enterprise Linux (RHEL)**
1.  Registrare il server utilizzando la sintassi seguente. Viene chiesto di immettere un nome utente valido e una password.
    
    ```bash
    sudo subscription-manager register
    ```
    
2.  Elenca i pool disponibili per la registrazione.
    
    ```bash
    sudo subscription-manager list --available
    ```

3.  Eseguire il comando seguente per associare la disponibilità elevata RHEL con la sottoscrizione
    
    ```bash
    sudo subscription-manager attach --pool=<PoolID>
    ```
    
    dove *PoolId* è l'ID del pool per la sottoscrizione a disponibilità elevata nel passaggio precedente.
    
4.  Abilitare il repository in grado di utilizzare il componente aggiuntivo la disponibilità elevata.
    
    ```bash
    sudo subscription-manager repos --enable=rhel-ha-for-rhel-7-server-rpms
    ```
    
5.  Installare Pacemaker.
    
    ```bash
    sudo yum install pacemaker pcs fence-agents-all resource-agents
    ```

**Ubuntu**

```bash
sudo apt-get install pacemaker pcs fence-agents resource-agents
```

**SUSE Linux Enterprise Server (SLES)**

Installare il modello di disponibilità elevata in YaST oppure eseguire l'operazione come parte dell'installazione del server principale. L'installazione può essere eseguita con un ISO/DVD come origine o caricandolo in linea.
> [!NOTE]
> In SLES, il componente aggiuntivo a disponibilità elevata viene inizializzato durante la creazione del cluster.

## <a name="prepare-the-nodes-for-pacemaker-rhel-and-ubuntu-only"></a>Preparare i nodi per Pacemaker (RHEL e Ubuntu solo)
Pacemaker stesso utilizza un utente creato alla distribuzione denominato *hacluster*. L'utente viene creata quando viene installato il componente aggiuntivo a disponibilità elevata in RHEL e Ubuntu.
1. In ogni server che fungerà da un nodo del cluster Pacemaker, creare la password per un utente da utilizzare per il cluster. Il nome utilizzato negli esempi è *hacluster*, ma è possibile utilizzare qualsiasi nome. Il nome e la password deve essere lo stesso in tutti i nodi che partecipano al cluster Pacemaker.
   
    ```bash
    sudo passwd hacluster
    ```
    
2. In ogni nodo che farà parte del cluster Pacemaker, abilitare e avviare il `pcsd` servizio con i comandi seguenti (RHEL e Ubuntu):

   ```bash
   sudo systemctl enable pcsd
   sudo systemctl start pcsd
   ```
   
   Eseguire quindi
   
   ```bash
   sudo systemctl status pcsd
   ```
   
   Per garantire che `pcsd` viene avviato.
3. Abilitare il servizio Pacemaker in ogni nodo del cluster Pacemaker possibili.
   
   ```bash
   sudo systemctl start pacemaker
   ```

   In Ubuntu, viene visualizzato un errore:
   
   *pacemaker avvio predefinita non contiene alcun runlevels, l'interruzione.*
   
   Questo errore è un problema noto. Nonostante l'errore, abilitare il servizio Pacemaker ha esito positivo e il bug verrà corretto in futuro a un certo punto.
   
4. Successivamente, creare e avviare il cluster Pacemaker. Non c'è una differenza tra RHEL e Ubuntu in questo passaggio. Mentre in entrambe le distribuzioni, installando `pcs` consente di configurare un file di configurazione predefinito per il cluster Pacemaker, su RHEL, l'esecuzione di questo comando Elimina qualsiasi configurazione esistente e crea un nuovo cluster.

<a id="create"></a>
## <a name="create-the-pacemaker-cluster"></a>Creare il cluster Pacemaker 
Questa sezione illustra come creare e configurare il cluster per ogni distribuzione di Linux.

**RHEL**

1. Autorizzare i nodi
   
   ```bash
   sudo pcs cluster auth <Node1 Node2 … NodeN> -u hacluster
   ```
   
   dove *NodeX* è il nome del nodo.
2. Creare il cluster
   
   ```bash
   sudo pcs cluster setup --name <PMClusterName Nodelist> --start --all --enable
   ```
   
   dove *PMClusterName* è il nome assegnato al cluster Pacemaker e *Nodelist* è l'elenco dei nomi dei nodi separati da uno spazio.

**Ubuntu**

Configurazione Ubuntu è simile a RHEL. Tuttavia, è la principale differenza: installare i pacchetti Pacemaker crea una configurazione di base per il cluster e attiva e avvia `pcsd`. Se si tenta di configurare il cluster Pacemaker seguendo le istruzioni di RHEL esattamente, viene visualizzato un errore. Per risolvere questo problema, eseguire la procedura seguente: 
1. Rimuovere la configurazione di Pacemaker predefinita da ciascun nodo.
   
   ```bash
   sudo pcs cluster destroy
   ```
   
2. Seguire i passaggi nella sezione per creare il cluster Pacemaker RHEL.

**SLES**

Il processo per la creazione di un cluster Pacemaker è completamente diverso in SLES si trova in RHEL e Ubuntu. I passaggi seguenti come creare un cluster con SLES del documento.
1. Avviare il processo di configurazione del cluster eseguendo 
   ```bash
   sudo ha-cluster-init
   ``` 
   
   in uno dei nodi. Potrebbe essere richiesto che NTP non è configurato e che non viene trovato alcun dispositivo watchdog. Che è appropriato per effettuare operazioni per eseguire. Se si utilizza fencing incorporato del SLES archiviazione basato su STONITH è correlato watchdog. NTP e controllo possono essere configurati in un secondo momento.
   
2. Richiesto di configurare Corosync. Richiesto per l'indirizzo di rete da associare, nonché l'indirizzo multicast e la porta. L'indirizzo di rete è la subnet in uso; ad esempio, 192.191.190.0. È possibile accettare le impostazioni predefinite in ogni prompt, o modificare se necessario.
   
3. Successivamente, viene chiesto se si desidera configurare SBD, ovvero il geofencing basate su disco. Questa configurazione può essere eseguita in un secondo momento, se desiderato. Se SBD non è configurato, a differenza di RHEL e Ubuntu, `stonith-enabled` per impostazione predefinita verrà essere impostato su false.
   
4. Infine, viene chiesto se si desidera configurare un indirizzo IP per l'amministrazione. Questo indirizzo IP è facoltativo, ma le funzioni simile all'indirizzo IP per un cluster di failover di Windows Server (WSFC) nel senso che crea un indirizzo IP del cluster da utilizzare per connettersi tramite a disponibilità elevata Web Konsole (HAWK). Questa configurazione, è facoltativa.
   
5. Verificare che il cluster sia in esecuzione eseguendo 
   ```bash
   sudo crm status
   ```
   
6. Modifica il *hacluster* password con 
   ```bash
   sudo passwd hacluster
   ```
   
7. Se è stato configurato un indirizzo IP per l'amministrazione, è possibile eseguirne il test in un browser, i test anche la modifica della password per *hacluster*.
   ![](./media/sql-server-linux-deploy-pacemaker-cluster/image2.png)
   
8. In un altro server SLES che rappresenterà un nodo del cluster, eseguire 
   ```bash
   sudo ha-cluster-join
   ```
   
9. Quando richiesto, immettere il nome o indirizzo IP del server in cui è stato configurato come il primo nodo del cluster nei passaggi precedenti. Il server viene aggiunto come un nodo al cluster esistente.
   
10. Verificare che l'aggiunta del nodo eseguendo 
   ```bash
   sudo crm status
   ```
   
11. Modifica il *hacluster* password con 
   ```bash
   sudo passwd hacluster
   ```
   
12. Ripetere i passaggi da 8 a 11 per tutti gli altri server da aggiungere al cluster.

## <a name="install-the-sql-server-ha-and-sql-server-agent-packages"></a>Installare i pacchetti di SQL Server a disponibilità elevata e SQL Server Agent
Utilizzare i comandi seguenti per installare il pacchetto SQL Server a disponibilità elevata e [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] agente, se non sono già installati. Installazione del pacchetto a disponibilità elevata dopo l'installazione di [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] richiede il riavvio del [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] per poter essere utilizzato. Queste istruzioni presuppongono che il repository per i pacchetti Microsoft sono già state impostate, poiché [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] deve essere installato a questo punto.
> [!NOTE]
> - Se non si utilizzerà [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] agente per la distribuzione dei log o qualsiasi altro utilizzo, non deve essere installato, pertanto il pacchetto *mssql-server agent* può essere ignorata.
> - Gli altri pacchetti facoltativi per [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] su Linux, [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] ricerca Full-Text (*mssql-server-fts*) e [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Integration Services (*mssql server è*), non sono obbligatorio per la disponibilità elevata per un'istanza FCI o un gruppo di disponibilità.

**RHEL**

```bash
sudo yum install mssql-server-ha mssql-server-agent
sudo systemctl restart mssql-server
```

**Ubuntu**

```bash
sudo apt-get install mssql-server-ha mssql-server-agent
sudo systemctl restart mssql-server
```

**SLES**

```bash
sudo zypper install mssql-server-ha mssql-server-agent
sudo systemctl restart mssql-server
```

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione è stato descritto come distribuire un cluster Pacemaker per SQL Server in Linux. Si è appreso per:
> [!div class="checklist"]
> * Installare il componente aggiuntivo la disponibilità elevata e Pacemaker.
> * Preparare i nodi per Pacemaker (RHEL e Ubuntu solo).
> * Creare il cluster Pacemaker.
> * Installare i pacchetti di SQL Server a disponibilità elevata e SQL Server Agent.

Per creare e configurare un gruppo di disponibilità per SQL Server in Linux, vedere:

> [!div class="nextstepaction"]
> [Creare e configurare un gruppo di disponibilità per SQL Server in Linux](sql-server-linux-create-availability-group.md).

