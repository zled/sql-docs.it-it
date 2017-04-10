---
title: "Gestione connessione Hadoop | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.designer.hadoopconn.f1"
ms.assetid: 8bb15b97-9827-46bc-aca6-068534ab18c4
caps.latest.revision: 7
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 7
---
# Gestione connessione Hadoop
  Il componente Gestione connessione Hadoop consente di connettere un pacchetto SSIS a un cluster Hadoop usando i valori specificati per le proprietà.  
  
## Configurare la gestione connessione Hadoop  
  
1.  Nella finestra di dialogo **Aggiungi gestione connessione SSIS** selezionare **Hadoop**, quindi fare clic su **Aggiungi**. Verrà visualizzata la finestra di dialogo **Editor gestione connessione Hadoop** .  
  
2.  Scegliere la scheda **WebHCat** o **WebHDFS** nel riquadro a sinistra per configurare le informazioni del cluster Hadoop correlate.  
  
3.  Se si abilita l'opzione **WebHCat** per richiamare un processo Hive o Pig in Hadoop, eseguire le operazioni seguenti.  
  
    1.  Per **Host WebHCat**, immettere il server che ospita il servizio WebHCat.  
  
    2.  Per **Porta WebHCat**, immettere la porta del servizio WebHCat, che per impostazione predefinita è 50111.  
  
    3.  Selezionare il metodo di **Autenticazione** per accedere al servizio WebHCat. I valori disponibili sono **Base** e **Kerberos**.  
  
         ![Hadoop connection manager editor with basic authentication](../../integration-services/connection-manager/media/hadoop-cm-basic.png "Hadoop connection manager editor with basic authentication")  
  
         ![Hadoop connection manager editor with Kerberos authentication](../../integration-services/connection-manager/media/hadoop-cm-kerberos.png "Hadoop connection manager editor with Kerberos authentication")  
  
    4.  Per **Utente WebHCat**immettere l' **Utente** autorizzato ad accedere a WebHCat.  
  
    5.  Se si seleziona l'autenticazione **Kerberos** , immettere la **Password** e il **Dominio**dell'utente.  
  
4.  Se si abilita l'opzione **WebHDFS** per copiare i dati da o a HDFS, eseguire le operazioni seguenti.  
  
    1.  Per **Host WebHDFS**, immettere il server che ospita il servizio WebHDFS.  
  
    2.  Per **Porta WebHDFS**, immettere la porta del servizio WebHDFS, che per impostazione predefinita è 50070.  
  
    3.  Selezionare il metodo di **Autenticazione** per accedere al servizio WebHDFS. I valori disponibili sono **Base** e **Kerberos**.  
  
    4.  Per **Utente WebHDFS**immettere l'utente autorizzato ad accedere a HDFS.  
  
    5.  Se si seleziona l'autenticazione **Kerberos** , immettere la **Password** e il **Dominio**dell'utente.  
  
5.  Fare clic su **Test connessione** per testare la connessione. (verrà testata solo la connessione abilitata).  
  
6.  Scegliere **OK** per chiudere la finestra di dialogo.  
  
## Vedere anche  
 [Attività Hive Hadoop](../../integration-services/control-flow/hadoop-hive-task.md)   
 [Attività Pig Hadoop](../../integration-services/control-flow/hadoop-pig-task.md)   
 [Attività File system Hadoop](../../integration-services/control-flow/hadoop-file-system-task.md)  
  
  