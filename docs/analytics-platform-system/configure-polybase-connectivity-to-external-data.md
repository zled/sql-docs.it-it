---
title: "Configurare la connettività di PolyBase ai dati esterni (Analitica piattaforma sistema)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6f14ac21-a086-4c05-861f-0a12bf278259
caps.latest.revision: "43"
ms.openlocfilehash: 7d486992f688b5bc914508ef000f23209b4bde89
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="configure-polybase-connectivity-to-external-data"></a>Configurazione della connettività di PolyBase per i dati esterni
Viene descritto come configurare PolyBase in SQL Server PDW per connettersi a Microsoft Azure o Hadoop archiviazione blob le origini dati esterne. Usare PolyBase per eseguire query che si integrano dati da più origini, tra cui Hadoop, archiviazione blob di Azure e SQL Server PDW.  
  
### <a name="to-configure-connectivity"></a>Per configurare la connettività  
  
1.  Aprire uno strumento di query, ad esempio sqlcmd o SQL Server Data Tools (SSDT) ed eseguire sp_configure per visualizzare le impostazioni di 'hadoop connectivity' corrente.  
  
    ![impostazione di connettività di Hadoop](./media/configure-polybase-connectivity-to-external-data/APS_PDW_sp_configure.png "APS_PDW_sp_configure")  
  
2.  Decidere quali connettività Hadoop impostazione necessario e se è necessario modificare l'impostazione corrente. Questa opzione si applica all'intera area di SQL Server PDW. Per un elenco completo delle impostazioni di configurazione e le versioni, vedere [sp_configure](../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
3.  Per modificare l'impostazione di 'hadoop connectivity', eseguire sp_configure con l'istruzione RECONFIGURE. Di seguito sono riportati alcuni esempi.  
  
    ```sql  
    --Enable connectivity to Hortonworks Data Platform for Windows Server (HDP), HDInsight on Analytics Platform System, or HDInsight’s Microsoft Azure blob storage  
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
  
    Esecuzione di sp_configure con l'istruzione RECONFIGURE imposta il valore di configurazione. L'area di riavvio è necessario impostare il valore di esecuzione. Poiché è necessario un riavvio dopo l'arresto Avanti inoltre, non è necessario eseguire il riavvio fino a dopo il passaggio successivo che modifica core-Site.Xml.  
  
4.  Per abilitare archiviazione blob di Microsoft Azure come un'origine dati esterna, aggiungere uno o più Microsoft Azure storage account chiavi di accesso al file di core-Site.XML PDW. Per aggiungere una chiave:  
  
    1.  Trovare il nome di account di archiviazione di Microsoft Azure. Per visualizzare gli account di archiviazione, l'account di accesso per il[portale di Azure](https://portal.azure.com) e fare clic su **gli account di archiviazione (classico)**.  
  
        ![Nome account di archiviazione Windows Azure](./media/configure-polybase-connectivity-to-external-data/APS_PDW_AzureStorageAccountName.png "APS_PDW_AzureStorageAccountName")  
  
    2.  Trovare la chiave di accesso di account di archiviazione di Azure. A tale scopo, scegliere il nome di account di archiviazione, quindi nel pannello delle impostazioni **chiavi**. Verranno visualizzati per le chiavi dell'account di archiviazione e nome.  
  
        ![Chiavi di accesso di account di archiviazione Windows Azure](./media/configure-polybase-connectivity-to-external-data/APS_PDW_AzureStorageAccountAccessKey.png "APS_PDW_AzureStorageAccountAccessKey")  
  
    3.  Aprire una connessione desktop remoto al nodo di controllo di PDW.  
  
    4.  Aprire il file C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf\core-site.xml.  
  
    5.  Aggiungere la seguente proprietà con gli attributi nome e valore core-Site.Xml.  
  
        ```xml  
        <property>  
          <name>fs.azure.account.key.<your storage account name>.blob.core.windows.net</name>  
          <value><your storage account access key></value>  
        </property>  
        ```  
  
        In questo esempio Usa la chiave di accesso e sul nome di account illustrata in precedenza.  
  
        ```xml  
        <property>  
          <name>fs.azure.account.key.CustomerX.blob.core.windows.net</name>  
          <value>yyeTfCxxxxxxxxQ5WdnapXw77W+FwzHUhX/p/f26fIpnNFGtewzyRN90e1/qmTOl1xxxxxxxxa0goG71LsNcw==</value>  
        </property>  
        ```  
  
        > [!CAUTION]  
        > Prima di archiviare la chiave di accesso in core-Site.XML, adottare precauzioni di sicurezza. Qualsiasi utente che dispone dell'autorizzazione CONTROL SERVER o ALTER ANY EXTERNAL DATA SOURCE è possibile creare un'origine dati esterna che accede a questo account. Una volta creato l'origine dati esterna, tutti gli utenti di SQL Server PDW che dispone dell'autorizzazione per creare tabelle possono creare una tabella esterna che accede a questo account di archiviazione. Gli utenti saranno quindi possibile accedere ai dati dell'account e utilizzare le risorse nell'account.  
  
    6.  Salvare le modifiche in core-Site.Xml.  
  
5.  Aggiungere il file yarn-Site.XML yarn proprietà e valori.  
  
    Se ci si connette a un 1.3 Hadoop esterno, ignorare questo passaggio.  
  
    A partire da Hadoop 2.0, il file yarn-Site.XML contiene le impostazioni di configurazione per il framework di YARN Hadoop. Questo file si trova nel nodo di controllo in **C:\program files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf\\**.  
  
    Per eseguire le query PolyBase su un Cluster di 2.0 esterno Hadoop in Windows o Linux, è necessario configurare le proprietà yarn e i valori siano coerenti con le impostazioni di yarn-Site.XML il cluster Hadoop esterno. Questa configurazione è necessaria anche se il Hadoop Cluster esterno utilizza le impostazioni predefinite.  
  
    Esempio di impostazioni predefiniti:  
  
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
  
    Dopo aver definita una proprietà in yarn-Site.XML, PolyBase utilizzerà le impostazioni di proprietà durante l'esecuzione di query con l'area di HDInsight. Se si prevede di eseguire le query PolyBase sia l'area di HDInsight e un Cluster di 2.0 Hadoop esterno in Windows, deve essere presente la coerenza fra tutti i file yarn-Site.XML, altrimenti la query di PolyBase avranno esito negativo.  
  
    Per eseguire PolyBase su sia l'area di HDInsight e un Cluster di 2.0 Hadoop esterno, usare le impostazioni predefinite yarn-Site.XML il cluster Hadoop esterno.  
  
6.  Riavviare l'area PDW. A tale scopo, utilizzare lo strumento di Configuration Manager. Vedere [avviare Gestione configurazione &#40; Sistema della piattaforma Analitica &#41; ](launch-the-configuration-manager.md).  
  
7.  Verificare le impostazioni di sicurezza per le connessioni di Hadoop. Se il **autenticazione debole** in Hadoop lato abilitato utilizzando `dfs.permission = true`, è necessario creare un utente di Hadoop **pdw_user** e concedono autorizzazioni di lettura completa e delle autorizzazioni di scrittura a questo utente. SQL Server PDW e chiamate corrispondenti da SQL Server PDW sono sempre generate come **pdw_user** che è un nome utente fisso e non può essere modificato in questa versione di connettività di Hadoop e la versione di SQL Server PDW. Se la sicurezza in Hadoop è disabilitata tramite `dfs.permission = false`, quindi non occorre effettuare alcuna azione ulteriore.  
  
8.  Decidere quali utenti possono creare un'origine dati esterna per l'archiviazione blob di Microsoft Azure. Assegnare il nome di account di archiviazione a ciascuno di questi utenti nonché **ALTER ANY EXTERNAL DATA SOURCE** o **CONTROL SERVER** autorizzazione.  
  
9. Per le connessioni di Hadoop, decidere quali utenti possono creare un'origine dati esterna in Hadoop. Concedere a ciascuno di questi utenti il numero di porta e indirizzo IP di ogni nodo del nome di Hadoop e fornire loro **ALTER ANY EXTERNAL DATA SOURCE** o **CONTROL SERVER** autorizzazione.  
  
10. Connessione a WASB richiede anche l'inoltro di DNS da configurare nel dispositivo. Per configurare l'inoltro di DNS, vedere [utilizzare un server d'inoltro DNS per risolvere nomi DNS Non dispositivo &#40; Sistema della piattaforma Analitica &#41; ](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md).  
  
Gli utenti autorizzati a questo punto è possono creare origini dati esterne, formati di file esterni e le tabelle esterne. È possibile utilizzarli per integrare dati da più origini, tra cui Hadoop, archiviazione blob di Microsoft Azure e SQL Server PDW.  
  
## <a name="see-also"></a>Vedere anche  
[Configurazione del dispositivo &#40; Sistema della piattaforma Analitica &#41;](appliance-configuration.md)  
<!-- MISSING LINKS [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md)  -->  
  
