1. **In entrambi i nodi del cluster creare un file per archiviare nome utente e password di SQL Server per l'accesso a Pacemaker**. Il comando seguente crea e popola questo file:

    ```bash
    sudo touch /var/opt/mssql/secrets/passwd
    sudo echo '<loginName>' >> /var/opt/mssql/secrets/passwd
    sudo echo '<loginPassword>' >> /var/opt/mssql/secrets/passwd
    sudo chown root:root /var/opt/mssql/secrets/passwd 
    sudo chmod 600 /var/opt/mssql/secrets/passwd
    ```
2. **Tutti i nodi del cluster devono essere in grado di accedere uno all'altro tramite SSH**. Strumenti come hb_report o crm_report (per la risoluzione dei problemi) e History Explorer di Hawk richiedono l'accesso a SSH tra i nodi senza password, in caso contrario possono raccogliere dati solo dal nodo corrente. Nel caso in cui si usi una porta SSH non standard, usare l'opzione -X (vedere la pagina relativa a man). Se, ad esempio, la porta SSH è 3479, richiamare un oggetto hb_report con:

    ```bash
    crm_report -X "-p 3479" [...]
    ```

    Per altre informazioni, vedere i [requisiti di sistema e consigli nella documentazione di SUSE](https://www.suse.com/documentation/sle_ha/book_sleha/data/sec_ha_requirements_other.html).

3. **Installare l'estensione per la disponibilità elevata**. Per installare l'estensione, seguire la procedura nell'argomento SUSE seguente:
    
    [Installation and Setup Quick Start](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html) (Guida introduttiva all'installazione e alla configurazione)

4. **Installare l'agente delle risorse FCI per SQL Server**. Eseguire i comandi seguenti in entrambi i nodi:

    ```bash
    sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server.repo
    sudo zypper --gpg-auto-import-keys refresh
    sudo zypper install mssql-server-ha
    ```

5. **Configurare automaticamente il primo nodo**. Il passaggio successivo consiste nel configurare un cluster a un nodo in esecuzione configurando il primo nodo, SLES1. Seguire le istruzioni nell'argomento SUSE [Setting Up the First Node](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.setup.1st-node) (Configurazione del primo nodo).

    Al termine, verificare lo stato del cluster con `crm status`:
    ```bash
    crm status
    ```

    Dovrebbe indicare che il nodo, SLES1, è configurato.

6. **Aggiungere nodi a un cluster esistente**. Aggiungere quindi il nodo SLES2 al cluster. Seguire le istruzioni nell'argomento SUSE [Adding the Second Node](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.setup.2nd-node) (Aggiunta del secondo nodo).
    
    Al termine, verificare lo stato del cluster con **crm status**. Se il secondo nodo è stato aggiunto correttamente, l'output sarà simile al seguente:
        
    ```
    2 nodes configured
    1 resource configured
    Online: [ SLES1 SLES2 ]
    Full list of resources:
    admin_addr     (ocf::heartbeat:IPaddr2):       Started SLES1
    ```

    > [!NOTE]
    > **admin_addr** è la risorsa cluster IP virtuale configurata durante l'installazione iniziale del cluster a un nodo.

7.    **Procedure di rimozione**. Se si vuole rimuovere un nodo dal cluster, usare lo script di bootstrap **ha-cluster-remove**. Per altre informazioni, vedere [Overview of the Bootstrap Scripts](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.bootstrap) (Panoramica degli script di bootstrap).  

