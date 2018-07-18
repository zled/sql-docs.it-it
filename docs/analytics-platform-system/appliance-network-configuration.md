---
title: Configurazione di rete accessorio - Analitica Platform System | Documenti Microsoft
description: Il dispositivo Analitica piattaforma di strumenti compilato e configurato con un set di correzione degli indirizzi IP in tutti i server e dispositivi applicabili da stabilimento del IHV. Dopo la consegna del dispositivo, è necessario riconfigurare l'indirizzo IP di esterno (Ethernet) in base ai requisiti del cliente specifico data center.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 2db040c63d3c31f93cd0b72e48422e806aef01e0
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="appliance-network-configuration-for-analytics-platform-system"></a>Configurazione di rete dello strumento per Analitica Platform System
Il dispositivo Analitica piattaforma di strumenti compilato e configurato con un set di correzione degli indirizzi IP in tutti i server e dispositivi applicabili da stabilimento del IHV. Dopo la consegna del dispositivo, è necessario riconfigurare l'indirizzo IP di esterno (Ethernet) in base ai requisiti del cliente specifico data center.  
  
> [!NOTE]  
> PDW V1 necessari 8 IP esterno (*rivolta a clienti*) gli indirizzi per fornire connettività esterna a ogni controllo rack nodi. 2012 PDW (V2) avanzata delle comunicazioni di rete tramite l'esposizione di ogni componente del dispositivo esternamente tramite gli indirizzi IP. Questo approccio fornisce una struttura più affidabile riduce i costi e aumentando la flessibilità e migliora lo spostamento dei dati, il caricamento dei dati e l'integrazione di Hadoop. Il numero di indirizzi IP necessarie dipende dal numero di nodi nel dispositivo e la presenza di funzionalità, ad esempio HDInsight. Per gestire questo blocco più grande di indirizzi IP, il cliente deve configurare una subnet distinta per PDW. All'interno della subnet, saranno presenti sufficiente spazio degli indirizzi IP (indirizzi fino a 250) per supportare i componenti del rack PDW fino a 5.  
  
Il **configurazione di rete** pagina consente di visualizzare le impostazioni di rete accessibile pubblicamente per i nodi nel dispositivo di sistema della piattaforma Analitica. Questa pagina è di sola lettura.  
  
![Rete dello strumento DWConfig](./media/appliance-network-configuration/SQL_Server_PDW_DWConfig_ApplTopNetwork.png "SQL_Server_PDW_DWConfig_ApplTopNetwork")  
  
## <a name="to-update-the-network-configuration-on-your-appliance"></a>Per aggiornare la configurazione di rete del dispositivo  
Modificare gli indirizzi IP del dominio dell'infrastruttura, il dominio del carico di lavoro e domini di HDInsight modificando il **AplianceInfo.xml** file e quindi eseguendo il programma di installazione. Si tratta di un'operazione offline. HDInsight (se presente) sia PDW aree verranno automaticamente arrestate durante la modifica degli indirizzi IP.  
  
> [!NOTE]  
> I nomi di dominio vengono forniti durante l'installazione e vengono specificati come fino a 6 caratteri alfanumerici, a partire da una lettera. Un sistema di denominazione frequente crea un dominio dell'infrastruttura a partire da F, a un dominio di carico di lavoro PDW a partire da P e a un dominio di HDInsight a partire da H. Questo formato si presume che in tutta la Guida di file ma non è obbligatorio. <!-- MISSING LINKS For more information about the domain structure, see [PDW Domain Security &#40;SQL Server PDW&#41;](../sqlpdw/pdw-domain-security-sql-server-pdw.md) and [Understanding the Security Model of the HDInsight Region &#40;Analytics Platform System&#41;](../hdinsight/understanding-the-security-model-of-the-hdinsight-region.md)  -->  
  
#### <a name="to-change-the-ip-addresses-of-the-analytics-platform-system"></a>Per modificare gli indirizzi IP del sistema di piattaforma Analitica  
  
1.  Utilizzo di **Desktop remoto** applicazione, connettersi a **HST01** utilizzando l'account di amministratore di dominio del carico di lavoro.  
  
2.  Nel nodo HST01, aprire il file di informazioni sul dispositivo in **c:\pdwinst\media\AplianceInfo.xml**.  
  
    > [!NOTE]  
    > Se il file non è presente, potrebbe essere necessario un nuovo file da creare.  
  
3.  Aggiornare i valori Ethernet IP in base alle esigenze e salvare il file.  
  
4.  In una finestra del prompt dei comandi, eseguire il seguente comando di installazione per aggiornare gli indirizzi IP per l'area PDW, utilizzando i nomi di dominio di P/F/H e le password dell'amministratore.  
  
    ```  
    c:\pdwinst\media\setup.exe /action="ConfigureEthernet" /DomainAdminPassword="<password>" /ApplianceInfoFile="C:\PDWINST\media\ApplianceInfo.xml"  
    ```  
  
## <a name="manufacturer-references"></a>Riferimenti produttore  
Per ulteriori informazioni su accessori Dell, vedere:  
  
-   Istruzioni Switch PowerConnect [Dell PowerConnect 6200 serie sistema CLI Guida di riferimento](http://downloads.dell.com/Manuals/all-products/esuprt_ser_stor_net/esuprt_powerconnect/powerconnect-6224f_Reference%20Guide_en-us.pdf)  
  
-   iDRAC/BMC [manuale dell'utente versione 1.30.30 integrata Dell remota accesso Controller 7 (iDRAC7)](http://downloads.dell.com/Manuals/all-products/esuprt_electronics/esuprt_software/esuprt_remote_ent_sys_mgmt/integrated-dell-remote-access-cntrllr-7-v1.30.30_User%27s%20Guide_en-us.pdf?c=us&l=en&cs=555&s=biz)  
  
-   PDU **Dell a consumo Rack PDU**`ftp://ftp.dell.com/Manuals/all-products/esuprt_ser_stor_net/esuprt_rack_infrastructure/dell-metered-pdu-led_User's%20Guide_en-us.pdf`  
  
## <a name="see-also"></a>Vedere anche  
[Avviare Gestione configurazione &#40;Analitica Platform System&#41;](launch-the-configuration-manager.md)  
  
