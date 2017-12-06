---
title: Creazione di file di valore della variabile (AccessToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-access
ms.custom: 
ms.date: 08/17/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 808595c3-8ef1-40bd-a93e-5cf237950e08
caps.latest.revision: "15"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ef98e5026d0cb488f0edfc4fccd386c0b1539bcd
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="creating-variable-value-files-accesstosql"></a>Creazione di file di valore della variabile (AccessToSQL)
Un File di valore di variabile è un file XML che include i valori dei parametri dei comandi (ad esempio il nome di server di origine o di destinazione) che cambiano spesso tra le migrazioni a server. Quando si verifica un numero elevato di migrazioni di database, più file di variabile per archiviare il valore di ogni server di origine vengono creati e a cui fa riferimento in un file di script master con il **– v** passare alla riga di comando. Questo comportamento consente di mantenere i valori statici, in alcuni file di script con i valori delle variabili in più file di variabile.  
  
> [!NOTE]  
> -  I nomi delle variabili sono preceduti e seguiti da un simbolo di dollaro $. Se una variabile non viene assegnata un valore nel file del valore della variabile, verificherà un errore durante l'analisi del file di script, risultante in bloccare il processo di esecuzione della console.  
> -  The escape character for **$** is **$$**. Se il valore di un valore statico o variabile di un parametro contiene un  **$**  simbolo (dollaro), quindi  **$$**  deve essere specificata di considerarlo come un carattere anziché una variabile.  
> -  Per motivi di manutenzione, le variabili possono essere dichiarate all'interno di `‘variable-group’` elementi per la separazione logica delle variabili definite dall'utente.  Utilizzo di questo elemento non è obbligatorio.  
  
**Esempi:**  
  
**Esempio 1:**  
  
```xml  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="ProjectSpecs">  
  
    <variable name="$type$" value="MyProject"/>  
  
    <variable name="$project_folder$" value=".\$project_name$"/>  
  
    <variable name="$project_name$" value="$type$ConsoleProject"/>  
  
    <variable name="$project_overwrite$" value="true"/>  
  
    <variable name="$project_type$" value="sql-server-2008"/>  
  
  </variable-group>  
  
</variables>  
```  
**Esempio 2:**  
  
```xml  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="SQLServerParams">  
  
    <variable-group name="SqlServerConnectionParams">  
  
      <variable name="$TargetServerName$" value="xxx"/>  
  
      <variable name="$TargetDB$" value="xxx"/>  
  
      <variable name="$TargetUserName$" value="xxx"/>  
  
      <variable name="$TargetPassword$" value="xxx"/>  
  
      <variable name="$TargetIsTrusted$" value="xxx"/>  
  
      <variable name="$TrustedConnection$" value="xxx"/>  
  
    </variable-group>  
  
    <variable-group name="SqlServerObjectParams">  
  
      <variable name="$ObjectName1$" value="TestTable1"/>  
  
      <variable name="$ObjectName2$" value="TestProc1"/>  
  
    </variable-group>  
  
  </variable-group>  
  
</variables>  
```  
  
## <a name="variable-value-file-validation"></a>Convalida file di valore della variabile  
L'utente facilmente è in grado di convalidare il file di valore della variabile nel file di definizione dello schema **ConsoleScriptVariablesSchema.xsd** disponibile nella cartella 'Schemi'.  
  
## <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo nella console di gestione è [creare i file di connessione del Server &#40; AccessToSQL &#41;](../../ssma/access/creating-the-server-connection-files-accesstosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[Creazione dei file di connessione del Server (accesso)](http://msdn.microsoft.com/829153be-aa8e-4162-87e8-69882feecf19)  
  
