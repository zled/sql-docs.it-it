2. In tutti i nodi del cluster, creare un file per archiviare il nome utente di SQL Server e la password per l'account di accesso Pacemaker. Il comando seguente crea e popola questo file:

   ```bash
   sudo touch /var/opt/mssql/secrets/passwd
   sudo echo '<loginName>' >> /var/opt/mssql/secrets/passwd
   sudo echo '<loginPassword>' >> /var/opt/mssql/secrets/passwd
   sudo chown root:root /var/opt/mssql/secrets/passwd 
   sudo chmod 600 /var/opt/mssql/secrets/passwd    
   ```

3. In tutti i nodi del cluster, aprire le porte del firewall Pacemaker. Per aprire queste porte con `firewalld`, eseguire il comando seguente:

   ```bash
   sudo firewall-cmd --permanent --add-service=high-availability
   sudo firewall-cmd --reload
   ```

   > Se si sta usando un altro firewall che non ha una configurazione a disponibilità elevata predefinita, è necessario aprire le porte seguenti per consentire a Pacemaker di comunicare con altri nodi del cluster
   >
   > * TCP: porte 2224, 3121, 21064
   > * UDP: porta 5405

1. Installare i pacchetti Pacemaker in ogni nodo.

   ```bash
   sudo yum install pacemaker pcs fence-agents-all resource-agents
   ```

   

2. Impostare la password per l'utente predefinito creato durante l'installazione dei pacchetti Corosync e Pacemaker. Utilizzare la stessa password in tutti i nodi. 

   ```bash
   sudo passwd hacluster
   ```

   

3. Abilitare e avviare il servizio `pcsd` e Pacemaker. In questo modo, i nodi potranno unirsi nuovamente in join con il cluster dopo il riavvio. Eseguire il comando seguente in tutti i nodi.

   ```bash
   sudo systemctl enable pcsd
   sudo systemctl start pcsd
   sudo systemctl enable pacemaker
   ```

4. Installare l'agente delle risorse FCI per SQL Server. Eseguire i comandi seguenti in tutti i nodi. 

   ```bash
   sudo yum install mssql-server-ha
   ```
