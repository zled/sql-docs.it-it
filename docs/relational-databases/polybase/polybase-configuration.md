---
title: "Configurazione di PolyBase | Microsoft Docs"
ms.custom: ""
ms.date: "11/08/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 80ff73c1-2861-438b-a13f-309155f3d6e1
caps.latest.revision: 17
author: "barbkess"
ms.author: "barbkess"
manager: "jhubbard"
caps.handback.revision: 12
---
# Configurazione di PolyBase
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Per configurare PolyBase, usare le procedure seguenti.  
  
## <a name="external-data-source-configuration"></a>Configurazione con origine dati esterna  
 È necessario verificare la connettività all'origine dati esterna da SQL Server. Il tipo di connettività influenza notevolmente le prestazioni delle query previste. Un collegamento Ethernet da 10 Gbit comporterà ad esempio tempi di risposta delle query PolyBase più rapidi rispetto a un collegamento Ethernet da 1 Gbit.  
  
 È necessario configurare SQL Server per la connessione alla versione di Hadoop in uso o all'archivio BLOB di Azure usando **sp_configure**. PolyBase supporta due distribuzioni di Hadoop: Hortonworks Data Platform (HDP) e Cloudera Distributed Hadoop (CDH).  Per un elenco completo delle origini dati esterne supportate, vedere [Configurazione della connettività di PolyBase &#40;Transact-SQL&#41;](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md).  
  
### <a name="run-spconfigure"></a>Eseguire sp_configure  
  
1.  Eseguire sp_configure 'hadoop connectivity' e impostare un valore appropriato.  Per trovare il valore, vedere [Configurazione della connettività di PolyBase &#40;Transact-SQL&#41;](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md).  
  
    ```tsql  
    -- Values map to various external data sources.  
    -- Example: value 7 stands for Azure blob storage and Hortonworks HDP 2.3 on Linux.  
    sp_configure @configname = 'hadoop connectivity', @configvalue = 7;   
    GO   
  
    RECONFIGURE   
    GO   
    ```  
  
2.  È necessario riavviare SQL Server mediante **services.msc**. Il riavvio di SQL Server comporta il riavvio di questi servizi:  
  
    -   Servizio spostamento dati di PolyBase per SQL Server  
  
    -   Motore di PolyBase per SQL Server  
  
## <a name="pushdown-configuration"></a>Configurazione della distribuzione  
 Per migliorare le prestazioni delle query, abilitare il calcolo della distribuzione in un cluster Hadoop:  
  
1.  Trovare il file **yarn-site.xml** nel percorso di installazione di SQL Server. In genere il percorso è:  
  
    ```  
    C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn\Polybase\Hadoop\conf  
    ```  
  
2.  Nel computer Hadoop trovare il file analogo nella directory di configurazione Hadoop. Nel file trovare e copiare il valore della chiave di configurazione yarn.application.classpath.  
  
3.  Nel computer SQL Server, nel **file yarn.site.xml,** trovare la proprietà **yarn.application.classpath** . Incollare il valore dal computer Hadoop nell'elemento valore.  
  
## <a name="kerberos-configuration"></a>Configurazione di Kerberos  
 Per connettersi a un cluster Hadoop protetto con Kerberos tramite MIT KDC:  
  
1.  Trovare la directory di configurazione Hadoop nel percorso di installazione di SQL Server. In genere il percorso è:  
  
    ```  
    C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn\Polybase\Hadoop\conf  
    ```  
  
2.  Trovare il valore di configurazione lato Hadoop delle chiavi di configurazione elencate nella tabella. Nel computer Hadoop trovare i file nella directory di configurazione Hadoop.  
  
3.  Copiare i valori di configurazione nella proprietà del valore nei file corrispondenti sul computer SQL Server.  
  
    |**#**|**File di configurazione**|**Chiave di configurazione**|**Azione**|  
    |------------|----------------|---------------------|----------|   
    |1|core-site.xml|polybase.kerberos.kdchost|Specificare l'area di autenticazione Kerberos. Ad esempio: AREA-DI-AUTENTICAZIONE.COM|  
    |2|core-site.xml|polybase.kerberos.realm|Specificare il nome host KDC. Ad esempio: kerberos.area-di-autenticazione.com.|  
    |3|core-site.xml|hadoop.security.authentication|Trovare la configurazione lato Hadoop e copiarla nel computer SQL Server. Ad esempio: KERBEROS<br></br>**Nota sulla sicurezza:** è necessario scrivere KERBEROS in maiuscolo. Se si usano lettere minuscole, potrebbe non essere disponibile.|   
    |4|hdfs-site.xml|dfs.namenode.kerberos.principal|Trovare la configurazione lato Hadoop e copiarla nel computer SQL Server. Ad esempio: hdfs/_HOST@YOUR-REALM.COM|  
    |5|mapred-site.xml|mapreduce.jobhistory.address|Trovare la configurazione lato Hadoop e copiarla nel computer SQL Server. Ad esempio: mapred/_HOST@YOUR-REALM.COM|  
    |6|mapred-site.xml|mapreduce.jobhistory.principal|Trovare la configurazione lato Hadoop e copiarla nel computer SQL Server. Ad esempio: 10.193.26.174:10020|  
    |7|yarn-site.xml yarn.|yarn.resourcemanager.principal|Trovare la configurazione lato Hadoop e copiarla nel computer SQL Server. Ad esempio: yarn/_HOST@YOUR-REALM.COM|  
  
4.  Creare un oggetto credenziali con ambito database per specificare le informazioni di autenticazione per ogni utente di Hadoop. Vedere [Oggetti T-SQL PolyBase](../../relational-databases/polybase/polybase-t-sql-objects.md).  
  
## <a name="next-steps"></a>Passaggi successivi  
 [Oggetti T-SQL PolyBase](../../relational-databases/polybase/polybase-t-sql-objects.md)  
  
 [Introduzione a PolyBase](../../relational-databases/polybase/get-started-with-polybase.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione della connettività di PolyBase &#40;Transact-SQL&#41;](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md)   
 [Guida a PolyBase](../../relational-databases/polybase/polybase-guide.md)  
  
  