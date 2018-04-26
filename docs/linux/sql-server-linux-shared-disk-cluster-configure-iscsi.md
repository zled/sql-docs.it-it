---
title: Configurare il failover del cluster istanza archiviazione iSCSI, SQL Server in Linux | Documenti Microsoft
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/28/2017
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.workload: Inactive
ms.openlocfilehash: 4033289cb388e9ba06260b482af613054e70760c
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="configure-failover-cluster-instance---iscsi---sql-server-on-linux"></a>Configurare l'istanza del cluster di failover SQL Server in Linux - iSCSI:

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In questo articolo viene illustrato come configurare l'archiviazione iSCSI per un'istanza cluster di failover (FCI) in Linux. 

## <a name="configure-iscsi"></a>Configurare iSCSI 
iSCSI utilizza la rete per presentare i dischi da un server noto come una destinazione ai server. I server di connessione alla destinazione iSCSI richiedono che sia configurato un iniziatore iSCSI. I dischi di destinazione vengono concesse le autorizzazioni esplicite in modo che solo gli iniziatori che devono essere in grado di accedere a tali possono farlo. Alla destinazione stessa deve essere affidabile e a disponibilità elevata.

### <a name="important-iscsi-target-information"></a>Informazioni di destinazione iSCSI importanti
Mentre non illustra come configurare una destinazione iSCSI, poiché è specifica per il tipo di origine che verrà utilizzato in questa sezione, verificare che sia configurata la sicurezza per i dischi che verranno utilizzati dai nodi del cluster.  

La destinazione non deve essere configurata mai in uno dei nodi istanza cluster di failover se si usa una destinazione iSCSI basate su Linux. Per prestazioni e disponibilità, delle reti iSCSI dovrebbero essere separate da quelle utilizzate da regolare traffico di rete in cui sia il server di origine e il client. Le reti utilizzate per iSCSI devono essere rapida. Tenere presente che rete utilizzare alcuni larghezza di banda del processore, pertanto, pianificare di conseguenza se si utilizza un normale server.
La cosa più importante per garantire completata nella destinazione è i dischi che vengono creati sono assegnati le autorizzazioni appropriate in modo che solo i server che fanno parte dell'istanza FCI possano accedervi. Un esempio è illustrato di seguito dalla destinazione iSCSI Microsoft in cui linuxnodes1 è il nome creato e in questo caso, gli indirizzi IP dei nodi vengono assegnati in modo che appaia NewFCIDisk1.vhdx ad essi.

![Initiator][1]

### <a name="instructions"></a>Istruzioni

In questa sezione illustra le procedure configurare un iniziatore iSCSI nel server che fungerà da nodi per l'istanza FCI. Le istruzioni dovrebbero funzionare come in RHEL e Ubuntu.

Per ulteriori informazioni sull'iniziatore iSCSI per le distribuzioni supportate, consultare i collegamenti seguenti:
- [Red Hat](http://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/iscsi-api.html)
- [SUSE](http://www.suse.com/documentation/sles11/stor_admin/data/sec_inst_system_iscsi_initiator.html) 
- [Ubuntu](https://help.ubuntu.com/lts/serverguide/iscsi-initiator.html)

1.  Scegliere uno dei server che farà parte della configurazione di FCI. Non è importante quale. iSCSI deve trovarsi in una rete dedicata, pertanto configurare iSCSI per riconoscere e usare tale rete. Eseguire `sudo iscsiadm -m iface -I <iSCSIIfaceName> -o new` dove `<iSCSIIfaceName>` è il nome descrittivo o univoco per la rete. L'esempio seguente usa `iSCSINIC`:
   
    ```bash
    sudo iscsiadm -m iface -I iSCSINIC -o new
    ```
    ![7-setiscsinetwork][6]
 
2.  Modifica `/var/lib/iscsi/ifaces/iSCSIIfaceName`. Assicurarsi che i valori seguenti compilati completamente:

    - iface.net_ifacename è il nome della scheda di rete, come illustrato nel sistema operativo.
    - iface.hwaddress è l'indirizzo MAC di un nome univoco che verrà creato per questa interfaccia riportata di seguito.
    - iface.IPAddress
    - iface.subnet_Mask 

    Vedere l'esempio seguente:

    ![iSCSITargetSettings][2]

3.  Trovare la destinazione iSCSI.

    ```bash
    sudo iscsiadm -m discovery -t sendtargets -I <iSCSINetName> -p <TargetIPAddress>:<TargetPort>
    ```

     \<iSCSINetName > è l'univoco al nome descrittivo per la rete, \<TargetIPAddress > è l'indirizzo IP di destinazione iSCSI, e \<TargetPort > è la porta di destinazione iSCSI. 

    ![iSCSITargetResults][3]

 
4.  Nella destinazione di log

    ```bash
    sudo iscsiadm -m node -I <iSCSIIfaceName> -p TargetIPAddress -l
    ```

    \<iSCSIIfaceName > è l'univoco al nome descrittivo per la rete e \<TargetIPAddress > è l'indirizzo IP di destinazione iSCSI.

    ![iSCSITargetLogin][4]

5.  Verificare che sia disponibile una connessione alla destinazione iSCSI.

    ```bash
    sudo iscsiadm -m session
    ```

    ![iSCSIVerify][5]

 
6.  Verificare i dischi iSCSI collegati

    ```bash
    sudo grep “Attached SCSI” /var/log/messages
    ```
    ![30-iSCSIattachedDisks][7]

7.  Creare un volume fisico sul disco iSCSI.

    ```bash
    sudo pvcreate /dev/<devicename>
    ```

    \<DeviceName > è il nome del dispositivo nel passaggio precedente. 

 
8.  Creare un gruppo di volumi nel disco iSCSI. Dischi assegnati a un singolo gruppo di volumi sono considerati come un pool o una raccolta. 

    ```bash
    sudo vgcreate <VolumeGroupName> /dev/devicename
    ```

    \<VolumeGroupName > è il nome del gruppo di volumi e \<devicename > è il nome del dispositivo dal passaggio 6. 
 
9.  Creare e verificare il volume del disco logico.

    ```bash
    sudo lvcreate -Lsize -n <LogicalVolumeName> <VolumeGroupName>
    ```
    
    \<dimensioni > è la dimensione del volume da creare e può essere specificato con G (gigabyte), T (terabyte), e così via,\<LogicalVolumeName > è il nome del volume logico, e \<VolumeGroupName > è il nome del gruppo nel volume di passaggio precedente. 

    Nell'esempio seguente crea un volume di 25GB.
 
    ![Create25GBVol][10]

10. Eseguire `sudo lvs` per vedere LVM che è stato creato.
 
11. Formattare il volume logico con un file System supportato. Per EXT4, usare l'esempio seguente:

    ```bash
    sudo mkfs.ext4 /dev/<VolumeGroupName>/<LogicalVolumeName>
    ```

    \<VolumeGroupName > è il nome del gruppo di volumi nel passaggio precedente. \<LogicalVolumeName > è il nome del volume logico nel passaggio precedente.  

12. Per i database di sistema o qualsiasi elemento archiviato nel percorso dati predefinito, seguire questi passaggi. In caso contrario, andare al passaggio 13.

   *    Verificare che SQL Server è stato arrestato nel server che si sta lavorando.

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```

   *    Opzione completamente all'utente avanzato. Non riceverà un acknowledgement se ha esito positivo.

    ```bash
    sudo -i
    ```

   *    Opzione per l'utente mssql. Non riceverà un acknowledgement se ha esito positivo.

    ```bash
    su mssql
    ```

   *    Creare una directory temporanea per archiviare i dati di SQL Server e i file di log. Non riceverà un acknowledgement se ha esito positivo.

    ```bash
    mkdir <TempDir>
    ```

    \<TempDir > è il nome della cartella. Nell'esempio seguente crea una cartella denominata /var/opt/mssql/TempDir.

    ```bash
    mkdir /var/opt/mssql/TempDir
    ```
    
   *    Copiare i file di dati e di log di SQL Server per la directory temporanea. Non riceverà un acknowledgement se ha esito positivo.

    ```bash
    cp /var/opt/mssql/data/* <TempDir>
    ```

    \<TempDir > è il nome della cartella nel passaggio precedente.
    
   *    Verificare che i file nella directory.

    ```bash
    ls \<TempDir>
    ```
    \<TempDir > è il nome della cartella dal passaggio d.

   *    Eliminare i file dalla directory dei dati di SQL Server esistente. Non riceverà un acknowledgement se ha esito positivo.

    ```bash
    rm – f /var/opt/mssql/data/*
    ```

   *    Verificare che i file sono stati eliminati. Nell'immagine seguente mostra un esempio dell'intera sequenza da c a h.

    ```bash
    ls /var/opt/mssql/data
    ```

    ![45-CopyMove][8]
 
   *    Tipo `exit` per tornare all'utente root.

   *    Montare il volume logico iSCSI nella cartella dati SQL Server. Non riceverà un acknowledgement se ha esito positivo.

    ```bash
    mount /dev/<VolumeGroupName>/<LogicalVolumeName> /var/opt/mssql/data
    ``` 

    \<VolumeGroupName > è il nome del gruppo di volumi e \<LogicalVolumeName > è il nome del volume logico che è stato creato. La sintassi di esempio seguente consente di ricercare il gruppo di volumi e il volume logico dal comando precedente.

    ```bash
    mount /dev/FCIDataVG1/FCIDataLV1 /var/opt/mssql/data
    ``` 

   *    Modificare il proprietario del montaggio in mssql. Non riceverà un acknowledgement se ha esito positivo.

    ```bash
    chown mssql /var/opt/mssql/data
    ```

   *    Modificare il proprietario del gruppo di montaggio per mssql. Non riceverà un acknowledgement se ha esito positivo.

    ```bash
    chgrp mssql /var/opt/mssql/data
    ``` 

   *    Passare all'utente mssql. Non riceverà un acknowledgement se ha esito positivo.

    ```bash
    su mssql
    ``` 

   *    Copiare i file da /var/opt/mssql/data la directory temporanea. Non riceverà un acknowledgement se ha esito positivo.

    ```bash
    cp /var/opt/mssql/TempDir/* /var/opt/mssql/data
    ``` 

   *    Verificare che i file sono presenti.

    ```bash
    ls /var/opt/mssql/data
    ``` 
 
   *    Immettere `exit` a non essere mssql.
    
   *    Immettere `exit` non essere radice.

   *    Avviare SQL Server. Se tutto ciò che è stata copiata correttamente e sicurezza applicata correttamente, SQL Server dovrebbe essere mostrato come avviato.

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    ``` 
 
   *    Arrestare SQL Server e verificare che viene chiuso.

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ``` 

13. Per scopi diversi da database di sistema, ad esempio i database utente o di backup, seguire questi passaggi. Se solo utilizzando il percorso predefinito, andare al passaggio 14.

   *    Opzione per l'utente avanzato. Non riceverà un acknowledgement se ha esito positivo.

    ```bash
    sudo -i
    ```

   *    Creare una cartella che verrà utilizzata da SQL Server. 

    ```bash
    mkdir <FolderName>
    ```

    \<Nome cartella > è il nome della cartella. Percorso completo della cartella deve essere specificato ma non nella posizione corretta. Nell'esempio seguente crea una cartella denominata /var/opt/mssql/userdata.

    ```bash
    mkdir /var/opt/mssql/userdata
    ```

   *    Montare il volume logico iSCSI nella cartella creata nel passaggio precedente. Non riceverà un acknowledgement se ha esito positivo.
    
    ```bash
    mount /dev/<VolumeGroupName>/<LogicalVolumeName> <FolderName>
    ```

    \<VolumeGroupName > è il nome del gruppo di volumi, \<LogicalVolumeName > è il nome del volume logico che è stato creato, e \<FolderName > è il nome della cartella. Sintassi di esempio è illustrata di seguito.

    ```bash
    mount /dev/FCIDataVG2/FCIDataLV2 /var/opt/mssql/userdata 
    ```

   *    Modificare il proprietario della cartella creata per mssql. Non riceverà un acknowledgement se ha esito positivo.

    ```bash
    chown mssql <FolderName>
    ```

    \<Nome cartella > è il nome della cartella in cui è stato creato. Di seguito è riportato un esempio.

    ```bash
    chown mssql /var/opt/mssql/userdata
    ```
  
   *    Modificare il gruppo della cartella creata per mssql. Non riceverà un acknowledgement se ha esito positivo.

    ```bash
    chown mssql <FolderName>
    ```

    \<Nome cartella > è il nome della cartella in cui è stato creato. Di seguito è riportato un esempio.

    ```bash
    chown mssql /var/opt/mssql/userdata
    ```

   *    Tipo `exit` non essere più l'utente avanzato.

   *    Per eseguire il test, creare un database in tale cartella. Nell'esempio illustrato di seguito utilizza sqlcmd per creare un database, passare il contesto, verificare i file presenti nel livello del sistema operativo e quindi Elimina il percorso temporaneo. È possibile utilizzare SQL Server Management Studio.
  
    ![50 ExampleCreateSSMS][9]

   *    Disinstallare la condivisione 

    ```bash
    sudo umount /dev/<VolumeGroupName>/<LogicalVolumeName> <FolderName>
    ```

    \<VolumeGroupName > è il nome del gruppo di volumi, \<LogicalVolumeName > è il nome del volume logico che è stato creato, e \<FolderName > è il nome della cartella. Sintassi di esempio è illustrata di seguito.

    ```bash
    sudo umount /dev/FCIDataVG2/FCIDataLV2 /var/opt/mssql/userdata 
    ```

14. Configurare il server in modo che il solo Pacemaker può attivare il gruppo di volumi.

    ```bash
    sudo lvmconf --enable-halvm --services –startstopservices
    ```
 
15. Generare un elenco di gruppi di volumi nel server. Tutti gli elementi elencati non il disco iSCSI usato dal sistema, ad esempio per il disco del sistema operativo.

    ```bash
    sudo vgs
    ```

16. Modificare la sezione di configurazione di attivazione di /etc/lvm/lvm.conf il file. Configurare la riga seguente:

    ```bash
    volume_list = [ <ListOfVGsNotUsedByPacemaker> ]
    ```

    \<ListOfVGsNotUsedByPacemaker > è riportato l'elenco di gruppi di volumi dall'output del passaggio 20 che non verrà utilizzato dall'istanza FCI. Inserire ognuno racchiuso tra virgolette e separato da una virgola. Di seguito è riportato un esempio.

    ![55-ListOfVGs][11]
 
 
17. All'avvio di Linux, esegue il montaggio del file system. Per assicurarsi che solo Pacemaker possibile montare il disco iSCSI, ricompilare l'immagine del file System radice. 

    Eseguire il comando seguente che potrebbe richiedere alcuni minuti per completare. Non si otterrà alcun messaggio di nuovo se ha esito positivo.

    ```bash
    sudo dracut -H -f /boot/initramfs-$(uname -r).img $(uname -r)
    ```

18. Riavviare il server.

19. In un altro server che farà parte nell'istanza FCI, eseguire i passaggi 1-6. Verrà visualizzata la destinazione iSCSI a SQL Server. 
 
20. Generare un elenco di gruppi di volumi nel server. Dovrebbe visualizzare il gruppo di volumi creato in precedenza. 

    ```bash
    sudo vgs
    ``` 
23. Avvio di SQL Server e verificare di che poter essere avviato su questo server.

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    ```

24. Arrestare SQL Server e verificare che sia arrestata.

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```
25. Ripetere i passaggi da 1 a 6 in qualsiasi altro server che farà parte nell'istanza FCI.

A questo punto si è pronti configurare l'istanza FCI.

|Distribuzione |Argomento 
|----- |-----
|**Red Hat Enterprise Linux con il componente aggiuntivo a disponibilità elevata** |[Configurare](sql-server-linux-shared-disk-cluster-configure.md)<br/>[Gestire](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
|**SUSE Linux Enterprise Server con il componente aggiuntivo a disponibilità elevata** |[Configurare](sql-server-linux-shared-disk-cluster-sles-configure.md)

## <a name="next-steps"></a>Passaggi successivi

[Configurare l'istanza del cluster di failover, SQL Server in Linux](sql-server-linux-shared-disk-cluster-configure.md)

<!--Image references-->
[1]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/05-initiator.png
[2]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/10-iscsiTargetSettings.png
[3]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/15-iSCSITargetResults.png
[4]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/20-iSCSITargetLogin.png
[5]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/25-iSCSIVerify.png
[6]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/7-setiscsinetwork.png
[7]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/30-iSCSIattachedDisks.png
[8]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/45-CopyMove.png
[9]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/50-ExampleCreateSSMS.png
[10]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/40-Create25GBVol.png
[11]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/55-ListOfVGs.png
