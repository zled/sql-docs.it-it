---
title: Estensione del linguaggio Java in SQL Server 2019 | Microsoft Docs
description: Eseguire codice Java usando l'estensione del linguaggio Java di SQL Server 2019.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/24/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 8acb0a72435306cdec8740ffb41ff499eea61fac
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2018
ms.locfileid: "46715158"
---
# <a name="java-language-extension-in-sql-server-2019"></a>Estensione del linguaggio Java in SQL Server 2019 

A partire da SQL Server 2019, è possibile eseguire codice Java personalizzato nel [framework di estendibilità](../concepts/extensibility-framework.md) come componente aggiuntivo per l'istanza del motore di database. 

Il framework di estendibilità è un'architettura per l'esecuzione di codice esterno: (a partire in SQL Server 2019), Java [Python (a partire da SQL Server 2017)](../concepts/extension-python.md), e [R (a partire da SQL Server 2016)](../concepts/extension-r.md). L'esecuzione di codice è isolato da processi del motore di base, ma completamente integrato con l'esecuzione di query di SQL Server. Ciò significa che è possibile inserire i dati da qualsiasi query di SQL Server per il runtime esterno e utilizzare o rendere persistenti i risultati in SQL Server.

Come con qualsiasi estensione del linguaggio di programmazione, stored procedure di sistema [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) è l'interfaccia per l'esecuzione di codice Java pre-compilato.

## <a name="1---feature-installation"></a>1 = la funzionalità installazione

Eseguire il programma di installazione di SQL Server 2019 in Windows o Linux per installare l'estensione del linguaggio Java. È necessaria un'istanza di motore di database di SQL Server 2019. È possibile aggiungere l'integrazione di Java a versioni precedenti.

In Windows, avviare il [installazione guidata](../install/sql-machine-learning-services-windows-install.md). In Selezione funzionalità selezionare **Machine Learning Services (in-database)**. Anche se l'integrazione di Java non viene fornito con librerie di machine learning, questa è l'opzione nel programma di installazione che fornisce il framework di estendibilità. Se si vuole, è possibile omettere R e Python.

In Linux, installare il [motore di database](https://docs.microsoft.com/sql/linux/sql-server-linux-setup), nonché il [estendibilità e il pacchetto di estensione Java](../../linux/sql-server-linux-setup-machine-learning.md).

Gli esempi seguenti illustrano la sintassi per ogni sistema operativo Linux.

```bash
# RedHat install commands
sudo yum install mssql-server-extensibility
sudo yum install mssql-server-extensibility-java

# Ubuntu install commands
sudo apt-get install mssql-server-extensibility
sudo apt-get install mssql-server-extensibility-java

# USE install commands
sudo zypper install mssql-server-extensibility
sudo zypper install mssql-server-extensibility-java
```

## <a name="2---configuration"></a>2 - configurazione

Utilizzando SQL Server Management Studio o un altro strumento che esegue script Transact-SQL, configurare l'esecuzione dello script esterno nell'istanza del motore di database.

  ```sql
  EXEC sp_configure 'external scripts enabled', 1
  RECONFIGURE WITH OVERRIDE
-- No restart is required after this step as of SQl Server 2019
 ```

## <a name="3---bring-your-own-java"></a>3 - portare il proprio linguaggio

Una differenza dalla precedente integrazione di linguaggi come R e Python è controllata cui JVM viene utilizzato con SQL Server.

| Versione di Java | Sistema operativo |
|--------------|------------------|
| [1.10 Java](http://jdk.java.net/10/)   | Windows |
| Java 1.8   | Linux | 

Dato che Java è compatibile con le versioni precedenti, le versioni precedenti potrebbero funzionare, ma le versioni testate e supportate per questa versione CTP iniziale sono elencate nella tabella.

> [!Note]
>Per eseguire Java con SQL Server, è tecnicamente necessario solo il [Java Runtime Environment](http://www.oracle.com/technetwork/java/javase/downloads/jre10-downloads-4417026.html) installato (JRE). Il pacchetto JDK è una soluzione di sviluppo tra cui il compilatore Java e altri development kit relativi pacchetti. Se già si dispone di un ambiente di sviluppo ed è necessario solo un runtime di Java nel computer server, è possibile ignorare le istruzioni di installazione di JDK e solo installare JRE.

## <a name="jdk-on-windows"></a>JDK in Windows

Scaricare la versione Windows del [Java SE Development Kit (JDK)](http://www.oracle.com/technetwork/java/javase/downloads/jdk10-downloads-4416644.html).

Installare il pacchetto JDK sotto l'impostazione predefinita i file /Program / lettura cartella se si desidera evitare di dover concedere l'autorizzazione per **tutti i pacchetti di applicazione** e il **SQLRUserGroup** i gruppi di sicurezza in un percorso alternativo . Le stesse linee guida si applicano per l'accesso alle cartelle classpath Java, in cui si mantengono i file con estensione class o con estensione jar. 

> [!Note]
> Il modello di autorizzazione e isolamento per le estensioni è stato modificato in questa versione. Per altre informazioni, vedere [differenze in un'installazione di servizi di SQL Server Machine 2019 Learning](../install/sql-machine-learning-services-ver15.md).

<a name="perms-nonwindows"></a>

### <a name="grant-access-to-non-default-jdk-folder-windows-only"></a>Concedere l'accesso alla cartella JDK diverso (solo Windows)

È possibile ignorare questo passaggio se è installato JDK/JRE nella cartella predefinita. Per un'installazione di cartella diverso, eseguire gli script di PowerShell seguenti per concedere l'accesso per il **SQLRUsergroup** e account del servizio SQL Server (in ALL_APPLICATION_PACKAGES) per l'accesso a JVM e il classpath Java.

#### <a name="sqlrusergroup-permissions"></a>SQLRUserGroup autorizzazioni

```powershell
$Acl = Get-Acl "<YOUR PATH TO JDK / CLASSPATH>"
$Ar = New-Object  system.security.accesscontrol.filesystemaccessrule("SQLRUsergroup","FullControl","Allow")
$Acl.SetAccessRule($Ar)
Set-Acl ""<YOUR PATH TO JDK / CLASSPATH>" $Acl 
```

#### <a name="appcontainer-permissions"></a>Autorizzazioni di AppContainer

```powershell
$Acl = Get-Acl "<YOUR PATH TO JDK / CLASSPATH>" 
$Ar = New-Object  system.security.accesscontrol.filesystemaccessrule("ALL APPLICATION PACKAGES","FullControl","Allow") 
$Acl.SetAccessRule($Ar) 
Set-Acl "<YOUR PATH TO JDK / CLASSPATH>" $Acl 
```

### <a name="add-the-jdk-path-to-javahome"></a>Aggiungere il percorso JDK JAVA_HOME
È anche necessario aggiungere il percorso di installazione di JDK/JRE (ad esempio, "c:\Programmi\Microsoft Files\Java\jdk-10.0.2") a una variabile di ambiente di sistema che è denominata "JAVA_HOME". 

Per creare una variabile di sistema, utilizzare Pannello di controllo > sistema e sicurezza > sistema per accedere **delle proprietà di sistema avanzate**. Fare clic su **variabili di ambiente** e quindi creare una nuova variabile di sistema per JAVA_HOME.

![Variabile di ambiente Java domestico](../media/java/env-variable-java-home.png "di installazione per Java")

## <a name="jdk-on-linux"></a>JDK in Linux

In Linux, il pacchetto mssql-server-extensibility-java installa automaticamente ambiente JRE 1.8 se non è già installato. Aggiungerà anche il percorso della JVM a una variabile di ambiente JAVA_HOME chiamata.

## <a name="limitations-in-ctp-20"></a>Limitazioni nella versione CTP 2.0

* Non può superare il numero di valori nei buffer di input e output `MAX_INT (2^31-1)` perché è questo il numero massimo di elementi che possono essere allocati in una matrice nel linguaggio.

* Parametri di output in sp_execute_external_script non sono supportati in questa versione.

* Nessun tipo di dati LOB supporto per i set di dati di input e output in questa versione. Visualizzare [tipi di dati di SQL Server e Java](java-sql-datatypes.md) per informazioni dettagliate su quali dati sono supportati in questa versione CTP.

* Lo streaming tramite il parametro sp_execute_external_script @r_rowsPerRead non è supportata in questa versione CTP.

* Partizionamento utilizzando il parametro sp_execute_external_script @input_data_1_partition_by_columns non è supportata in questa versione CTP.

## <a name="next-steps"></a>Passaggi successivi

+ [Come chiamare Java in SQL Server](howto-call-java-from-sql.md)
+ [Esempio di Java in SQL Server](java-first-sample.md)
+ [Tipi di dati Java e SQL Server](java-sql-datatypes.md)