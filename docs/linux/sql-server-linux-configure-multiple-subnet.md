---
title: Configurare più subnet gruppi di disponibilità AlwaysOn e istanze del cluster di failover in Linux | Documenti Microsoft
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 12/1/2017
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: 612ac9c684fa8e0383981a32a94cf82d8ec68678
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2018
ms.locfileid: "34321902"
---
# <a name="configure-multiple-subnet-always-on-availability-groups-and-failover-cluster-instances"></a>Configurare più subnet gruppi di disponibilità AlwaysOn e istanze del cluster di failover

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Quando un'istanza del cluster sempre nel gruppo di disponibilità (AG) o il failover (FCI) si estende su più di un sito, ogni sito in genere ha una propria rete. Spesso questo significa che ogni sito ha un proprio gli indirizzi IP. Gli indirizzi del sito, ad esempio, avviare con 192.168.1. *x* e gli indirizzi del sito B iniziano con 192.168.2. *x*, dove *x* fa parte dell'indirizzo IP univoco per il server. Senza una qualche forma di routing sul posto a livello di rete, questi server non sarà in grado di comunicare tra loro. Esistono due modi per gestire questo scenario: configurare una rete che collega le due diverse subnet, nota come una VLAN, oppure configurare il routing tra subnet.

## <a name="vlan-based-solution"></a>Soluzione basata su VLAN
 
**Prerequisiti**: basata su VLAN per una soluzione, in ogni server che fanno parte di un gruppo di disponibilità o FCI necessario due schede di rete (NIC) per la disponibilità corretta (una scheda NIC a porta doppia sarebbe un singolo punto di errore in un server fisico), in modo che gli indirizzi IP può essere assegnato in la subnet nativa nonché uno nella VLAN. Si tratta di oltre a eventuali altre esigenze di rete, ad esempio iSCSI, che deve anche una propria rete.

La creazione di indirizzi IP per il gruppo di disponibilità o FCI viene eseguita nella VLAN. Nell'esempio seguente, la VLAN dispone di una subnet di 192.168.3. *x*, pertanto l'indirizzo IP per il gruppo di disponibilità o FCI è 192.168.3.104. Nothing aggiuntive deve essere configurato, perché è presente un singolo indirizzo IP assegnato al gruppo di disponibilità o FCI.

![](./media/sql-server-linux-configure-multiple-subnet/image1.png)

## <a name="configuration-with-pacemaker"></a>Configurazione con Pacemaker

Nel mondo Windows, un Failover del Cluster WSFC (Windows Server) in modo nativo supporta più subnet e gestisce più indirizzi IP tramite una dipendenza o sull'indirizzo IP. In Linux, non è presente alcuna dipendenza OR, ma è un modo per realizzare una corretta su più subnet in modo nativo con Pacemaker, come illustrato di seguito. Non è possibile farlo usando semplicemente la riga di comando Pacemaker normale per modificare una risorsa. È necessario modificare le informazioni del cluster base (implementazione). L'implementazione è un file XML con la configurazione Pacemaker.

![](./media/sql-server-linux-configure-multiple-subnet/image2.png)

### <a name="update-the-cib"></a>Aggiornare l'implementazione

1.  Esportare l'implementazione.

    **Red Hat Enterprise Linux (RHEL) e Ubuntu**

    ```bash
    sudo pcs cluster cib <filename>
    ```

    **SUSE Linux Enterprise Server (SLES)**

    ```bash
    sudo cibadmin -Q > <filename>
    ```

    Dove *filename* è il nome che si desidera chiamare l'implementazione.

2.  Modificare il file che è stato generato. Cercare il `<resources>` sezione. Si noterà che le varie risorse che sono state create per il gruppo di disponibilità o FCI. Individuare quello associato all'indirizzo IP. Aggiungere un `<instance attributes>` sezione con le informazioni per il secondo indirizzo IP di sopra o di sotto di quello esistente, ma prima `<operations>`. È simile alla sintassi seguente:

    ```xml
    <instance attributes id="<NameForAttribute>" score="<Score>">
        <rule id="<RuleName>" score="INFINITY">
            <expression id="<ExpressionName>" attribute="\#uname" operation="eq" value="<NodeNameInSubnet2>" />
        </rule>
        <nvpair id="<NameForSecondIP>" name="ip" value="<IPAddress>"/>
        <nvpair id="<NameForSecondIPNetmask>" name="cidr\_netmask" value="<Netmask>"/>
    </instance attributes>
    ```
    
    dove *NameForAttribute* è il nome univoco per questo attributo, *punteggio* è il numero assegnato all'attributo, che deve essere maggiore della subnet primaria, *RuleName*è il nome della regola, *ExpressionName* è il nome dell'espressione, *NodeNameInSubnet2* è il nome del nodo della subnet, *NameForSecondIP* è il nome associato al secondo indirizzo IP, *IPAddress* è l'indirizzo IP per la seconda subnet *NameForSecondIPNetmask* è il nome associato la subnet mask, e *Netmask* è la subnet mask per la subnet del secondo.
    
    Di seguito viene riportato un esempio.
    
    ```xml
    <instance attributes id="Node3-2nd-IP" score="2">
        <rule id="Subnet2-IP" score="INFINITY">
            <expression id="Subnet2-Node" attribute="\#uname" operation="eq" value="Node3" />
        </rule>
        <nvpair id="IP-In-Subnet-2" name="ip" value="192.168.2.102"/>
        <nvpair id="Netmask-For-IP2" name="cidr\_netmask" value="24" />
    </instance attributes>
    ```

3.  Importare l'implementazione modificato e riconfigurare il Pacemaker.

    **RHEL/Ubuntu**
    
    ```bash
    sudo pcs cluster cib-push <filename>
    ```

    **SLES**
    
    ```bash
    sudo cibadmin -R -x <filename>
    ```

    dove *filename* è il nome del file di implementazione con le informazioni sull'indirizzo IP modificati.

### <a name="check-and-verify-failover"></a>Controllare e verificare il failover

1.  Dopo l'implementazione viene applicato correttamente con la configurazione aggiornata, il nome DNS associato alla risorsa di indirizzo IP in Pacemaker il ping. Deve riflettere l'indirizzo IP associato alla subnet che ospita il gruppo di disponibilità o FCI.
2.  È in grado di gruppo di disponibilità o FCI altre subnet.
3.  Dopo il gruppo di disponibilità o FCI è completamente online, eseguire il ping il nome DNS associato all'indirizzo IP. Deve riflettere l'indirizzo IP nella subnet secondo.
4.  Se si desidera, il gruppo di disponibilità o FCI esito negativo alla subnet originale.
