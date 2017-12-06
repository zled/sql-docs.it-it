---
title: Creazione di file di valore della variabile (SybaseToSQL) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-sybase
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Sybase Console,Creating Variable Value Files
- Sybase Console,Variable Value File Validation
ms.assetid: 395be464-4b19-44f7-91e5-b8876d6743dc
caps.latest.revision: "15"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: be0b28fd548b950851b54a320ae36f37c405ed51
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="creating-variable-value-files-sybasetosql"></a>Creazione di file di valore della variabile (SybaseToSQL)
File valore variabile è un file XML che include i valori dei parametri dei comandi ad esempio, il nome del server di origine o di destinazione che cambiano spesso dalla migrazione di un server a un altro. Quando si verifica un numero elevato di migrazioni di database, verranno creati e a cui fa riferimento in un file di script master con più file di variabile per archiviare il valore di ogni server di origine di **– v** passare alla riga di comando. Ciò consente di mantenere i valori statici, in alcuni file di script con i valori delle variabili in più file di variabile.  
  
> [!NOTE]  
> 1.  I nomi delle variabili sono preceduti e seguiti da un simbolo di dollaro $. Se le variabili non vengono assegnate un valore nel file del valore della variabile, si verificherà un errore durante l'analisi del file script risultante in bloccare il processo di esecuzione della console.  
> 2.  The escape character for **$** is **$$**. Se il valore di un valore statico o variabile di un parametro contiene  **$**  simbolo (dollaro), quindi  **$$**  deve essere specificata di considerarlo come un carattere anziché una variabile.  
> 3.  Per motivi di manutenzione, le variabili possono essere dichiarate all'interno di `‘variable-group’` le variabili definite elementi per la separazione logica dell'utente.  Utilizzo di questo elemento non è obbligatorio.  
  
**Esempi:**  
  
**Esempio 1:**  
  
```xml  
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
  
```xml  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="SQLServerParams">  
  
    <variable-group name="SqlServerConnectionParams">  
  
      <variable name="$TargetUserName$" value="<user-name>"/>  
  
      <variable name="$TargetServerName$" value="<server-name>"/>  
  
      <variable name="$TargetDB$" value="<database-name>"/>  
  
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
  
## <a name="variable-value-file-validation"></a>Valore della variabile File convalida  
L'utente facilmente è in grado di convalidare il file di valore della variabile nel file di definizione dello schema **ConsoleScriptVariablesSchema.xsd** disponibile nella cartella 'Schemi'.  
  
## <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo nella console di gestione è [creare i file di connessione del Server &#40; SybaseToSQL &#41;](../../ssma/sybase/creating-the-server-connection-files-sybasetosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[Creazione dei file Server (Sybase)](http://msdn.microsoft.com/en-us/35ef396f-9f98-429d-9fc5-4f413d08fb37)  
  
