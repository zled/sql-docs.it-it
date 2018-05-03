---
title: Configurare il failover del cluster istanza archiviazione SMB - SQL Server in Linux | Documenti Microsoft
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
ms.openlocfilehash: b2ac145fa2103fa88d6eb94c91fcd573b822a8a6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="configure-failover-cluster-instance---smb---sql-server-on-linux"></a>Configurazione di cluster di failover - SMB - SQL Server in Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In questo articolo viene illustrato come configurare l'archiviazione SMB per un'istanza cluster di failover (FCI) in Linux. 
 
Nel mondo non Windows, SMB è spesso definita per la condivisione come Common Internet File System (CIFS) e implementata tramite Samba. Nel mondo Windows, l'accesso a una condivisione SMB viene eseguita in questo modo: \\nomeserver\nomecondivisione. Per le installazioni di SQL Server basati su Linux, la condivisione SMB deve essere montata come cartella.

## <a name="important-source-and-server-information"></a>Importanti informazioni di origine e di server

Ecco alcuni suggerimenti e le note per l'utilizzo di SMB correttamente:
- La condivisione SMB può essere in Windows, Linux, o anche da un dispositivo come fino a quando utilizza SMB 3.0 o versione successiva. Per ulteriori informazioni su Samba e SMB 3.0, vedere [SMB 3.0](https://wiki.samba.org/index.php/Samba3/SMB2#SMB_3.0) per verificare se l'implementazione Samba è compatibile con SMB 3.0.
- La condivisione SMB deve essere a disponibilità elevata.
- Protezione deve essere impostata in modo corretto nella condivisione SMB. Di seguito è riportato un esempio da /etc/samba/smb.conf, dove SQLData1 è il nome della condivisione.

![05 smbsource][1]

## <a name="instructions"></a>Istruzioni

1.  Scegliere uno dei server che farà parte della configurazione di FCI. Non è importante quale.

2.  Ottenere informazioni sull'utente mssql.

    ```bash
    sudo id mssql
    ```
    
    Si noti l'uid, gid e gruppi. 

3. Eseguire `sudo smbclient -L //NameOrIP/ShareName -U User`.

    \<NameOrIP > è il nome DNS o l'indirizzo IP del server che ospita la condivisione SMB.

    \<Nomecondivisione > è il nome della condivisione SMB. 

4. Per sistema database o qualsiasi elemento archiviato nel percorso dati predefinito seguire questi passaggi. In caso contrario, andare al passaggio 5. 

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

    <TempDir> è il nome della cartella. Nell'esempio seguente viene creata una cartella denominata /var/opt/mssql/tmp.

    ```bash
    mkdir /var/opt/mssql/tmp
    ```

   *    Copiare i file di dati e di log di SQL Server per la directory temporanea. Non riceverà un acknowledgement se ha esito positivo.

    ```bash
    cp /var/opt/mssql/data/* <TempDir>
    ```

    \<TempDir > è il nome della cartella nel passaggio precedente.
    
   *    Verificare che i file nella directory.

    ```bash
    ls <TempDir>
    ```

    \<TempDir > è il nome della cartella dal passaggio d.
    
   *    Eliminare i file dalla directory dei dati di SQL Server esistente. Non riceverà un acknowledgement se ha esito positivo.
 
    ```bash
    rm – f /var/opt/mssql/data/*
    ```

   *    Verificare che i file sono stati eliminati. 

    ```bash
    ls /var/opt/mssql/data
    ```
 
   *    Digitare exit per tornare all'utente root.

   *    Montare la condivisione SMB nella cartella dati SQL Server. Non riceverà un acknowledgement se ha esito positivo. In questo esempio viene illustrata la sintassi per la connessione a una condivisione SMB 3.0 basato su Windows Server.

    ```bash
    Mount -t cifs //<ServerName>/<ShareName> /var/opt/mssql/data -o vers=3.0,username=<UserName>,password=<Password>,domain=<domain>,uid=<mssqlUID>,gid=<mssqlGID>,file_mode=0777,dir_mode=0777
    ```

    \<NomeServer > è il nome del server con la condivisione SMB
    
    \<Nomecondivisione > è il nome della condivisione

    \<Nome utente > è il nome dell'utente per accedere alla condivisione

    \<Password > è la password per l'utente

    \<dominio > è il nome di Active Directory

    \<mssqlUID > è l'UID dell'utente mssql 
 
    \<mssqlGID > è GID dell'utente mssql
 
   *    Verificare che il montaggio ha esito negativo generando montaggio senza opzioni.

    ```bash
    mount
    ```
 
   *    Passare all'utente mssql. Non riceverà un acknowledgement se ha esito positivo.

    ```bash
    su mssql
    ```

   *    Copiare i file da /var/opt/mssql/data la directory temporanea. Non riceverà un acknowledgement se ha esito positivo.

    ```bash
    cp /var/opt/mssql/tmp/* /var/opt/mssql/data
    ```

   *    Verificare che i file sono presenti.

    ```bash
    ls /var/opt/mssql/data
    ```

   *    Immettere l'uscita da non mssql 

   *    Immettere l'uscita da non radice

   *    Avviare SQL Server. Se tutto ciò che è stata copiata correttamente e sicurezza applicata correttamente, SQL Server dovrebbe essere mostrato come avviato.

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    ```
 
   *    Per testare ulteriormente, creare un database per verificare che le autorizzazioni sono supportate. L'esempio seguente Usa codice Transact-SQL è possibile utilizzare SQL Server Management Studio.

    ![10_testcreatedb][2] 
  
   *    Arrestare SQL Server e verificare che viene chiuso. Se si desidera aggiungere o test altri dischi, non arrestare SQL Server fino a quando non quelli vengono aggiunti e testati.

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```

   *    Solo se completato, disinstallare la condivisione. In caso contrario, disinstallare dopo aver completato i test o aggiunta di dischi aggiuntivi.

    ```bash
    sudo umount //<IPAddressorServerName>/<ShareName /<FolderMountedIn>
    ```

    \<IPAddressOrServerName > è l'indirizzo IP o nome dell'host SMB

    \<Nomecondivisione > è il nome della condivisione
    
    \<FolderMountedIn > è il nome della cartella in cui viene montata SMB

5.  Per scopi diversi da database di sistema, ad esempio i database utente o di backup, seguire questi passaggi. Se solo utilizzando il percorso predefinito, andare al passaggio 14.
    
   *    Opzione per l'utente avanzato. Non riceverà un acknowledgement se ha esito positivo.

    ```bash
    sudo -i
    ```
    
   *    Creare una cartella che verrà utilizzata da SQL Server. 

    ```bash
    mkdir <FolderName>
    ```

    \<Nome cartella > è il nome della cartella. Percorso completo della cartella deve essere specificato ma non nella posizione corretta. Nell'esempio seguente viene creata una cartella denominata /var/opt/mssql/userdata.

    ```bash
    mkdir /var/opt/mssql/userdata
    ```

   *    Montare la condivisione SMB nella cartella dati SQL Server. Non riceverà un acknowledgement se ha esito positivo. In questo esempio viene illustrata la sintassi per la connessione a una condivisione Samba basato su SMB 3.0.

    ```bash
    Mount -t cifs //<ServerName>/<ShareName> <FolderName> -o vers=3.0,username=<UserName>,password=<Password>,uid=<mssqlUID>,gid=<mssqlGID>,file_mode=0777,dir_mode=0777
    ```

    \<NomeServer > è il nome del server con la condivisione SMB

    \<Nomecondivisione > è il nome della condivisione

    \<Nome cartella > è il nome della cartella creata nel passaggio precedente  

    \<Nome utente > è il nome dell'utente per accedere alla condivisione

    \<Password > è la password per l'utente

    \<mssqlUID > è l'UID dell'utente mssql

    \<mssqlGID > è GID dell'utente mssql.
 
   * Verificare che il montaggio ha esito negativo generando montaggio senza opzioni.
 
   * Digitare exit per non essere più l'utente avanzato.

   * Per eseguire il test, creare un database in tale cartella. L'esempio seguente usa sqlcmd per creare un database, passare il contesto, verificare i file presenti nel livello del sistema operativo e quindi Elimina il percorso temporaneo. È possibile utilizzare SQL Server Management Studio.
 
   * Disinstallare la condivisione 

    ```bash
    sudo umount //<IPAddressorServerName>/<ShareName> /<FolderMountedIn>
    ```
    
    \<IPAddressOrServerName > è l'indirizzo IP o nome dell'host SMB
 
    \<Nomecondivisione > è il nome della condivisione
 
    \<FolderMountedIn > è il nome della cartella in cui viene montata SMB.
 
6.  Ripetere i passaggi in altri nodi.

A questo punto si è pronti configurare l'istanza FCI.

## <a name="next-steps"></a>Passaggi successivi

[Configurare l'istanza del cluster di failover, SQL Server in Linux](sql-server-linux-shared-disk-cluster-configure.md)

<!--Image references-->
[1]: ./media/sql-server-linux-shared-disk-cluster-configure-smb/05-smbsource.png 
[2]: ./media/sql-server-linux-shared-disk-cluster-configure-smb/10-testcreatedb.png 
