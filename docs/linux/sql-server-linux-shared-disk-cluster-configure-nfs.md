---
title: Configurare l'archiviazione failover istanza cluster NFS - SQL Server in Linux | Documenti Microsoft
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/28/2017
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.openlocfilehash: 62cce3bc883321df820a6f5b9eb45e7359498e24
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="configure-failover-cluster-instance---nfs---sql-server-on-linux"></a>Configurare i cluster di failover - NFS - SQL Server in Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In questo articolo viene illustrato come configurare l'archiviazione NFS per un'istanza del cluster di failover (FCI) in Linux. 

NFS o network file system, è un metodo comune per la condivisione di dischi in Linux world ma non di uno. Analogamente a iSCSI, NFS può essere configurato in un server o un tipo di dispositivo o l'unità di archiviazione, purché soddisfi i requisiti di archiviazione per SQL Server.

## <a name="important-nfs-server-information"></a>Importanti informazioni del server NFS

L'origine hosting NFS (un server Linux o altro) deve essere utilizzando/conforme con la versione 4.2 o versioni successive. Le versioni precedenti non funzioneranno con SQL Server in Linux.

Quando si configurano le cartelle per essere condivisa nel server NFS, assicurarsi che le funzioni seguono queste opzioni di linee guida generali:
- `rw` Per garantire che la cartella possono essere essere letti e scritti
- `sync` Per garantire operazioni di scrittura per la cartella è garantito
- Non utilizzare `no_root_squash` un rischio per la sicurezza viene considerato come un'opzione.
- Verificare che la cartella disponga di diritti completi (777) applicati

Verificare che gli standard di sicurezza vengono applicati per l'accesso. Quando si configura la cartella, assicurarsi che solo i server che fanno parte dell'istanza FCI devono visualizzare la cartella NFS. Un esempio di un /etc/exports modificato in una soluzione basata su Linux NFS è illustrato di seguito in cui la cartella è limitata a FCIN1 e FCIN2.

![05 nfsacl][1]

## <a name="instructions"></a>Istruzioni

1. Scegliere uno dei server che farà parte della configurazione di FCI. Non è importante quale. 

2. Verificare che il server possa vedere il mount(s) nel server NFS.

    ```bash
    sudo showmount -e <IPAddressOfNFSServer>
    ```

    \<IPAddressOfNFSServer > è l'indirizzo IP del server NFS che si desidera utilizzare.

3. Per i database di sistema o qualsiasi elemento archiviato nel percorso dati predefinito, seguire questi passaggi. In caso contrario, andare al passaggio 4.
 
   * Verificare che SQL Server è stato arrestato nel server che si sta lavorando.

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```
   * Opzione completamente all'utente avanzato. Non riceverà un acknowledgement se ha esito positivo.

    ```bash
    sudo -i
    ```

   * Opzione per l'utente mssql. Non riceverà un acknowledgement se ha esito positivo.

    ```bash
    su mssql
    ```

   * Creare una directory temporanea per archiviare i dati di SQL Server e i file di log. Non riceverà un acknowledgement se ha esito positivo.

    ```bash
    mkdir <TempDir>
    ```

    \<TempDir > è il nome della cartella. Nell'esempio seguente viene creata una cartella denominata /var/opt/mssql/tmp.

    ```bash
    mkdir /var/opt/mssql/tmp
    ```

   * Copiare i file di dati e di log di SQL Server per la directory temporanea. Non riceverà un acknowledgement se ha esito positivo.
    
    ```bash
    cp /var/opt/mssql/data/* <TempDir>
    ```

    \<TempDir > è il nome della cartella nel passaggio precedente.

   * Verificare che i file nella directory.

    ```bash
    ls TempDir
    ```

    \<TempDir > è il nome della cartella dal passaggio d.

   * Eliminare i file dalla directory dei dati di SQL Server esistente. Non riceverà un acknowledgement se ha esito positivo.

    ```bash
    rm – f /var/opt/mssql/data/*
    ```

   * Verificare che i file sono stati eliminati. 

    ```bash
    ls /var/opt/mssql/data
    ```
    
   * Digitare exit per tornare all'utente root.

   * Montare la condivisione NFS nella cartella dati SQL Server. Non riceverà un acknowledgement se ha esito positivo.

    ```bash
    mount -t nfs4 <IPAddressOfNFSServer>:<FolderOnNFSServer> /var/opt/mssql/data -o nfsvers=4.2,timeo=14,intr
    ```

    \<IPAddressOfNFSServer > è l'indirizzo IP del server NFS che si desidera utilizzare 

    \<FolderOnNFSServer > è il nome della condivisione NFS. La sintassi di esempio seguente corrisponde alle informazioni di NFS dal passaggio 2.

    ```bash
    mount -t nfs4 200.201.202.63:/var/nfs/fci1 /var/opt/mssql/data -o nfsvers=4.2,timeo=14,intr
    ```

   * Verificare che il montaggio ha esito negativo generando montaggio senza opzioni.

    ```bash
    mount
    ```

    ![10 mountnoswitches][2]

   * Passare all'utente mssql. Non riceverà un acknowledgement se ha esito positivo.

    ```bash
    su mssql
    ```

   * Copiare i file da /var/opt/mssql/data la directory temporanea. Non riceverà un acknowledgement se ha esito positivo.

    ```bash
    cp /var/opt/mssql/tmp/* /var/opt/mssqldata
    ```

   * Verificare che i file sono presenti.

    ```bash
    ls /var/opt/mssql/data
    ```

   * Immettere l'uscita da non mssql 
    
   * Immettere l'uscita da non radice

   * Avviare SQL Server. Se tutto ciò che è stata copiata correttamente e sicurezza applicata correttamente, SQL Server dovrebbe essere mostrato come avviato.

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    ```
    
   * Creare un database per verificare che la protezione è stata impostata correttamente. L'esempio seguente mostra che viene eseguita tramite codice Transact-SQL può essere eseguita tramite SQL Server Management Studio.
 
    ![CreateTestdatabase][3]

   * Arrestare SQL Server e verificare che viene chiuso.

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```

   * Se non si sta creando eventuali altri mount NFS, disinstallare la condivisione. Se si è, non disinstallare.

    ```bash
    sudo umount <IPAddressOfNFSServer>:<FolderOnNFSServer> <FolderToMountIn>
    ```

    \<IPAddressOfNFSServer > è l'indirizzo IP del server NFS che si desidera utilizzare

    \<FolderOnNFSServer > è il nome della condivisione NFS

    \<FolderMountedIn > è la cartella creata nel passaggio precedente. 

4. Per scopi diversi da database di sistema, ad esempio i database utente o di backup, seguire questi passaggi. Se solo utilizzando il percorso predefinito, andare al passaggio 5.

   * Opzione per l'utente avanzato. Non riceverà un acknowledgement se ha esito positivo.

    ```bash
    sudo -i
    ```

   * Creare una cartella che verrà utilizzata da SQL Server. 

    ```bash
    mkdir <FolderName>
    ```

    \<Nome cartella > è il nome della cartella. Percorso completo della cartella deve essere specificato ma non nella posizione corretta. Nell'esempio seguente viene creata una cartella denominata /var/opt/mssql/userdata.

    ```bash
    mkdir /var/opt/mssql/userdata
    ```

   * Montare la condivisione NFS nella cartella creata nel passaggio precedente. Non riceverà un acknowledgement se ha esito positivo.

    ```bash
    Mount -t nfs4 <IPAddressOfNFSServer>:<FolderOnNFSServer> <FolderToMountIn> -o nfsvers=4.2,timeo=14,intr
    ```

    \<IPAddressOfNFSServer > è l'indirizzo IP del server NFS che si desidera utilizzare

    \<FolderOnNFSServer > è il nome della condivisione NFS

    \<FolderToMountIn > è la cartella creata nel passaggio precedente. Di seguito è riportato un esempio. 

    ```bash
    mount -t nfs4 200.201.202.63:/var/nfs/fci2 /var/opt/mssql/userdata -o nfsvers=4.2,timeo=14,intr
    ```

   * Verificare che il montaggio ha esito negativo generando montaggio senza opzioni.
  
   * Digitare exit per non essere più l'utente avanzato.

   * Per eseguire il test, creare un database in tale cartella. L'esempio seguente usa sqlcmd per creare un database, passare il contesto, verificare i file presenti nel livello del sistema operativo e quindi Elimina il percorso temporaneo. È possibile utilizzare SQL Server Management Studio.

    ![15 createtestdatabase][4]
 
   * Disinstallare la condivisione 

    ```bash
    sudo umount <IPAddressOfNFSServer>:<FolderOnNFSServer> <FolderToMountIn>
    ```

    \<IPAddressOfNFSServer > è l'indirizzo IP del server NFS che si desidera utilizzare
    
    \<FolderOnNFSServer > è il nome della condivisione NFS

    \<FolderMountedIn > è la cartella creata nel passaggio precedente. Di seguito è riportato un esempio. 
 
5. Ripetere i passaggi in altri nodi.


## <a name="next-steps"></a>Passaggi successivi

[Configurare l'istanza del cluster di failover, SQL Server in Linux](sql-server-linux-shared-disk-cluster-configure.md)

<!--Image references-->
[1]: ./media/sql-server-linux-shared-disk-cluster-configure-nfs/05-nfsacl.png
[2]: ./media/sql-server-linux-shared-disk-cluster-configure-nfs/10-mountnoswitches.png
[3]: ./media/sql-server-linux-shared-disk-cluster-configure-nfs/20-createtestdatabase.png
[4]: ./media/sql-server-linux-shared-disk-cluster-configure-nfs/15-createtestdatabase.png
