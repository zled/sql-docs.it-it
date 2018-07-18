---
title: Configurare la connettività di PolyBase - sistema di piattaforma Analitica | Microsoft Docs
description: Viene illustrato come configurare PolyBase in Parallel Data Warehouse, per connettersi a Hadoop o in Microsoft Azure storage blob origini dati esterne. Usare PolyBase per eseguire query che si integrano dati da più origini, inclusi Hadoop, archiviazione blob di Azure e Parallel Data Warehouse.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 26eeffb1d2a27ee49f01114b015ab4051b145d64
ms.sourcegitcommit: 731c5aed039607a8df34c63e780d23a8fac937e1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/07/2018
ms.locfileid: "37909871"
---
# <a name="configure-polybase-connectivity-to-external-data"></a>Configurare la connettività di PolyBase ai dati esterni
Viene illustrato come configurare PolyBase in Parallel Data Warehouse, per connettersi a Hadoop o in Microsoft Azure storage blob origini dati esterne. Usare PolyBase per eseguire query che si integrano dati da più origini, inclusi Hadoop, archiviazione blob di Azure e Parallel Data Warehouse.  
  
### <a name="to-configure-connectivity"></a>Per configurare la connettività  
  
1.  Aprire uno strumento di query, ad esempio sqlcmd o SQL Server Data Tools (SSDT) ed eseguire sp_configure per visualizzare le impostazioni di 'hadoop connectivity' corrente.  
  
    ![impostazione di connettività di Hadoop](./media/configure-polybase-connectivity-to-external-data/APS_PDW_sp_configure.png "APS_PDW_sp_configure")  
  
2.  Decidere quali Hadoop connectivity impostazione esigenza e se è necessario modificare l'impostazione corrente. Questa opzione si applica all'intera area di SQL Server PDW. Per un elenco completo delle impostazioni di configurazione e le versioni, vedere [sp_configure](../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
3.  Per modificare l'impostazione di 'hadoop connectivity', eseguire sp_configure con l'istruzione RECONFIGURE. Di seguito sono riportati alcuni esempi.  
  
    ```sql  
    --Enable connectivity to Hortonworks Data Platform for Windows Server (HDP) or HDInsight’s Microsoft Azure blob storage  
    EXEC sp_configure 'hadoop connectivity', 4;   
    RECONFIGURE;  
  
    -- Enable connectivity to Hortonworks Data Platform (HDP)for Linux   
    EXEC sp_configure 'hadoop connectivity', 5;   
    RECONFIGURE;  
  
    -- Enable connectivity to Cloudera CDH for Linux   
    EXEC sp_configure 'hadoop connectivity', 3;   
    RECONFIGURE;  
  
    -- Disable the Hadoop connectivity option   
    EXEC sp_configure 'hadoop connectivity', 0;  
    RECONFIGURE;  
    ```  
  
    In esecuzione sp_configure con l'istruzione RECONFIGURE consente di impostare il valore di configurazione. L'area di riavvio è necessario impostare il valore di esecuzione. Poiché è necessario un riavvio dopo l'arresto Avanti anche, non è necessario eseguire il riavvio dopo che il passaggio successivo, che modifica core-Site. Xml.  
  
4.  Per abilitare archiviazione blob di Microsoft Azure come un'origine dati esterna, aggiungere uno o più Microsoft Azure storage account chiavi di accesso al file core-Site. XML PDW. Per aggiungere una chiave:  
  
    1.  Trovare il nome di account di archiviazione di Microsoft Azure. Per visualizzare gli account di archiviazione, account di accesso per il[portale di Azure](https://portal.azure.com) e fare clic su **account di archiviazione (versione classica)**.  
  
        ![Nome account di archiviazione di Azure](./media/configure-polybase-connectivity-to-external-data/APS_PDW_AzureStorageAccountName.png "APS_PDW_AzureStorageAccountName")  
  
    2.  Trovare la chiave di accesso di account di archiviazione di Azure. A tale scopo, fare clic sul nome dell'account di archiviazione e nel pannello impostazioni fare clic su **chiavi**. Vengono visualizzati le chiavi dell'account di archiviazione e nome.  
  
        ![Chiavi di accesso di Windows Azure storage account](./media/configure-polybase-connectivity-to-external-data/APS_PDW_AzureStorageAccountAccessKey.png "APS_PDW_AzureStorageAccountAccessKey")  
  
    3.  Aprire una connessione desktop remoto al nodo di controllo di PDW.  
  
    4.  Aprire il file C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf\core-site.xml.  
  
    5.  Aggiungere la seguente proprietà con gli attributi nome e il valore per core-Site. Xml.  
  
        ```xml  
        <property>  
          <name>fs.azure.account.key.<your storage account name>.blob.core.windows.net</name>  
          <value><your storage account access key></value>  
        </property>  
        ```  
  
        In questo esempio Usa la chiave di accesso e il nome account mostrata in precedenza.  
  
        ```xml  
        <property>  
          <name>fs.azure.account.key.CustomerX.blob.core.windows.net</name>  
          <value>yyeTfCxxxxxxxxQ5WdnapXw77W+FwzHUhX/p/f26fIpnNFGtewzyRN90e1/qmTOl1xxxxxxxxa0goG71LsNcw==</value>  
        </property>  
        ```  
  
        > [!CAUTION]  
        > Prima di archiviare la chiave di accesso in core-Site. XML, adottare precauzioni di sicurezza. Qualsiasi utente che dispone dell'autorizzazione CONTROL SERVER o ALTER ANY EXTERNAL DATA SOURCE può creare un'origine dati esterna che accede a questo account. Dopo aver creata l'origine dati esterna, tutti gli utenti di SQL Server PDW con le autorizzazioni CREATE TABLE possono creare una tabella esterna che accede a questo account di archiviazione. Gli utenti possono quindi accedere ai dati dell'account e utilizzano risorse nell'account.  
  
    6.  Salvare le modifiche al file core-Site. Xml.  
  
5.  Aggiungere proprietà CLASSPATH e i valori del file yarn-Site. Xml.  
  
    Se ci si connette a un 1.3 Hadoop esterno, ignorare questo passaggio.  
  
    A partire da Hadoop 2.0, il file yarn-Site. XML contiene le impostazioni di configurazione per il framework di Hadoop YARN. Questo file si trova nel nodo di controllo sotto **C:\program files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf\\**.  
  
    Per eseguire query di PolyBase su un Cluster di Hadoop 2.0 esterno in Windows o Linux, è necessario configurare le proprietà CLASSPATH e i valori siano coerenti con le impostazioni di yarn-Site. XML nel Hadoop Cluster esterno. Questa configurazione è necessaria anche se il Hadoop Cluster esterno Usa le impostazioni predefinite.  
  
    Esempio di impostazioni predefinite:  
  
    ```xml  
    <property>  
        <name>yarn.application.classpath</name>  
        <value>  
          %HADOOP_CONF_DIR%,  
          %HADOOP_COMMON_HOME%/share/hadoop/common/*,  
          %HADOOP_COMMON_HOME%/share/hadoop/common/lib/*,  
          %HADOOP_HDFS_HOME%/share/hadoop/hdfs/*,  
          %HADOOP_HDFS_HOME%/share/hadoop/hdfs/lib/*,  
          %HADOOP_YARN_HOME%/share/hadoop/yarn/*,  
          %HADOOP_YARN_HOME%/share/hadoop/yarn/lib/*  
         </value>  
      </property>  
    ```  
  
    Dopo aver definita tutte le proprietà in yarn-Site. XML, PolyBase Usa le impostazioni delle proprietà durante l'esecuzione di query in Hadoop. Se si prevede di eseguire query di PolyBase su Blob di archiviazione di Azure sia un Cluster di Hadoop 2.0 esterno in Windows, deve essere presente la coerenza tra tutti i file yarn-Site. XML, altrimenti le query PolyBase avrà esito negativo.  
   
6.  Riavviare l'area PDW. A tale scopo, usare lo strumento Gestione configurazione. Visualizzare [avviare Gestione configurazione &#40;sistema di piattaforma Analitica&#41;](launch-the-configuration-manager.md).  
  
7.  Verificare le impostazioni di sicurezza per le connessioni di Hadoop. Se il **autenticazione debole** su Hadoop lato abilitato utilizzando `dfs.permission = true`, è necessario creare un utente Hadoop **pdw_user** e concedono autorizzazioni di lettura completa e autorizzazioni di scrittura per questo utente. Vengono sempre emesse come SQL Server PDW e chiamate corrispondenti da SQL Server PDW **pdw_user**.  Questo è un nome utente fisso e non può essere modificato in questa versione di Hadoop connectivity e il rilascio di SQL Server PDW. Se la sicurezza in Hadoop è disabilitata tramite `dfs.permission = false`, necessario senza ulteriori azioni da intraprendere.  
  
8.  Decidere quali utenti possono creare un'origine dati esterna all'archivio blob di Microsoft Azure. Ognuno di questi utenti assegnare il nome di account di archiviazione, nonché **ALTER ANY EXTERNAL DATA SOURCE** oppure **CONTROL SERVER** l'autorizzazione.  
  
9. Per le connessioni di Hadoop, decidere quali utenti possono creare un'origine dati esterna in Hadoop. Assegnare ogni utente il numero di porta e indirizzo IP di ogni nodo del nome Hadoop e assegnarvi **ALTER ANY EXTERNAL DATA SOURCE** oppure **CONTROL SERVER** l'autorizzazione.  
  
10. La connessione a WASB richiede anche l'inoltro di DNS deve essere configurata nell'appliance. Per configurare l'inoltro DNS, vedere [usare un server d'inoltro di DNS per risolvere nomi DNS Non di Appliance &#40;sistema di piattaforma Analitica&#41;](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md).  
  
Gli utenti autorizzati a questo punto è possono creare origini dati esterne, formati di file esterni e le tabelle esterne. È possibile usarle per integrare dati provenienti da più origini, inclusi Hadoop, archiviazione blob di Microsoft Azure e SQL Server PDW.  

## <a name="kerberos-configuration"></a>Configurazione di Kerberos  
Si noti che se PolyBase esegue l'autenticazione in un cluster protetto con Kerberos, l'impostazione Hadoop deve essere impostata per l'autenticazione. La comunicazione dei dati tra i nodi Hadoop rimane non crittografata. 

 Per connettersi a un cluster Hadoop protetto con Kerberos tramite MIT KDC]:
   
  
1.  Trovare la directory di configurazione Hadoop nel percorso di installazione nel nodo di controllo:  
  
    ```  
    C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf
    ```  
  
2.  Trovare il valore di configurazione lato Hadoop delle chiavi di configurazione elencate nella tabella. Nel computer Hadoop trovare i file nella directory di configurazione Hadoop.  
  
3.  Copiare i valori di configurazione nella proprietà del valore nei file corrispondenti sul nodo di controllo.  
  
    |**#**|**File di configurazione**|**Chiave di configurazione**|**Azione**|  
    |------------|----------------|---------------------|----------|   
    |1|core-site.xml|polybase.kerberos.kdchost|Specificare il nome host KDC. Ad esempio: kerberos.area-di-autenticazione.com.|  
    |2|core-site.xml|polybase.kerberos.realm|Specificare l'area di autenticazione Kerberos. Ad esempio: AREA-DI-AUTENTICAZIONE.COM|  
    |3|core-site.xml|hadoop.security.authentication|Trovare la configurazione lato Hadoop e copiarla nel computer SQL Server. Ad esempio: KERBEROS<br></br>**Nota sulla sicurezza:** è necessario scrivere KERBEROS in maiuscolo. Se si usano lettere minuscole, potrebbe non essere disponibile.|   
    |4|hdfs-site.xml|dfs.namenode.kerberos.principal|Trovare la configurazione lato Hadoop e copiarla nel computer SQL Server. Ad esempio: hdfs/_HOST@YOUR-REALM.COM|  
    |5|mapred-site.xml|mapreduce.jobhistory.principal|Trovare la configurazione lato Hadoop e copiarla nel computer SQL Server. Ad esempio: mapred/_HOST@YOUR-REALM.COM|  
    |6|mapred-site.xml|mapreduce.jobhistory.address|Trovare la configurazione lato Hadoop e copiarla nel computer SQL Server. Ad esempio: 10.193.26.174:10020|  
    |7|yarn-site.xml yarn.|yarn.resourcemanager.principal|Trovare la configurazione lato Hadoop e copiarla nel computer SQL Server. Ad esempio: yarn/_HOST@YOUR-REALM.COM|  
  
4. Creare un oggetto credenziali con ambito database per specificare le informazioni di autenticazione per ogni utente di Hadoop. Vedere [Oggetti T-SQL PolyBase](../relational-databases/polybase/polybase-t-sql-objects.md).  

5. Riavviare l'area PDW. A tale scopo, usare lo strumento Gestione configurazione. Visualizzare [avviare Gestione configurazione &#40;sistema di piattaforma Analitica&#41;](launch-the-configuration-manager.md).
 
## <a name="see-also"></a>Vedere anche  
[La configurazione dell'Appliance &#40;sistema di piattaforma Analitica&#41;](appliance-configuration.md)  
<!-- MISSING LINKS [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md)  -->  
  
