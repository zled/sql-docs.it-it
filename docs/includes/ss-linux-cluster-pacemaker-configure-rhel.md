
3. In entrambi i nodi del cluster aprire le porte del firewall di Pacemaker. Per aprire queste porte con `firewalld`, eseguire il comando seguente:

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

   

2. Impostare la password per l'utente predefinito creato durante l'installazione dei pacchetti Corosync e Pacemaker. Usare la stessa password in entrambi i nodi. 

   ```bash
   sudo passwd hacluster
   ```

   

3. Abilitare e avviare il servizio `pcsd` e Pacemaker. In questo modo, i nodi potranno unirsi nuovamente in join con il cluster dopo il riavvio. Eseguire il comando seguente in entrambi i nodi.

   ```bash
   sudo systemctl enable pcsd
   sudo systemctl start pcsd
   sudo systemctl enable pacemaker
   ```

4. Creare il cluster. Per creare il cluster, eseguire il comando seguente:

   ```bash
   sudo pcs cluster auth <nodeName1> <nodeName2…> -u hacluster -p <password for hacluster>
   sudo pcs cluster setup --name <clusterName> <nodeName1> <nodeName2…> 
   sudo pcs cluster start --all
   ```
   
   >[!NOTE]
   >Se in precedenza è stato configurato un cluster negli stessi nodi, è necessario usare l'opzione '--force' quando si esegue 'pcs cluster setup'. Si noti che ciò equivale all'esecuzione di 'pcs cluster destroy' e il servizio Pacemaker deve essere riabilitato usando 'sudo systemctl enable pacemaker'.

5. Installare l'agente delle risorse SQL Server per SQL Server. Eseguire i comandi seguenti in entrambi i nodi. 

   ```bash
   sudo yum install mssql-server-ha
   ```
