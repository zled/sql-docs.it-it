---
title: Creazione di file di valore della variabile (OracleToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Variable Value File Creation
- Variable Value File, Variable Value File Validation
ms.assetid: f583d81a-8e34-41b1-8100-ee3a6a82213b
caps.latest.revision: 26
author: sabotta
ms.author: carlasab
manager: v-thobro
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3ba4def7c054b0d5a65a8ac93698cf6cb432845a
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="creating-variable-value-files-oracletosql"></a>Creazione di file di valore della variabile (OracleToSQL)
File valore variabile è un file XML che include i valori dei parametri dei comandi ad esempio, il nome del server di origine o di destinazione che cambiano spesso dalla migrazione di un server a un altro. Quando si verifica un numero elevato di migrazioni di database, verranno creati e a cui fa riferimento in un file di script master con più file di variabile per archiviare il valore di ogni server di origine di **– v** passare alla riga di comando. Ciò consente di mantenere i valori statici, in alcuni file di script con i valori delle variabili in più file di variabile.  
  
> [!NOTE]  
> 1.  I nomi delle variabili sono preceduti e seguiti da un simbolo di dollaro $. Se le variabili non vengono assegnate un valore nel file del valore della variabile, si verificherà un errore durante l'analisi del file script risultante in bloccare il processo di esecuzione della console.  
> 2.  The escape character for **$** is **$$**. Se il valore di un valore statico o variabile di un parametro contiene  **$**  simbolo (dollaro), quindi  **$$**  deve essere specificata di considerarlo come un carattere anziché una variabile.  
> 3.  Per motivi di manutenzione, le variabili possono essere dichiarate all'interno di `‘variable-group’` le variabili definite elementi per la separazione logica dell'utente.  Utilizzo di questo elemento non è obbligatorio.  
  
**Esempi:**  
  
**Esempio 1:**  
  
```  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="ProjectSpecs">  
  
    <variable name="$project_folder$" value="<project-folder>"/>  
  
    <variable name="$project_name$" value="<project-name>"/>  
  
    <variable name="$project_overwrite$" value="<true/false>"/>  
  
    <variable name="$project_type$" value="<project-type>"/>  
  
  </variable-group>  
  
</variables>  
```  
**Esempio 2:**  
  
```  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="SQLServerParams">  
  
    <variable-group name="SqlServerConnectionParams">  
  
      <variable name="$TargetServerName$" value="<server-name>"/>  
  
      <variable name="$TargetDB$" value="<database-name>"/>  
  
      <variable name="$TargetUserName$" value="<user-name>"/>  
  
      <variable name="$TargetPassword$" value="<password>"/>  
  
      <variable name="$TrustedConnection$" value="<true/false>"/>  
  
    </variable-group>  
  
    <variable-group name="SqlServerObjectParams">  
  
      <variable name="$ObjectName1$" value="<object-name>"/>  
  
      <variable name="$ObjectName2$" value="<object-name>"/>  
  
    </variable-group>  
  
  </variable-group>  
  
</variables>  
```  
  
## <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo nella console di gestione è [creazione OracleToSQL i file di connessione del Server &#40; &#41;](../../ssma/oracle/creating-the-server-connection-files-oracletosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[Creazione dei file Server (Oracle)](http://msdn.microsoft.com/en-us/002f129e-0868-48ad-a4b4-c68b5007e12e)  
  

