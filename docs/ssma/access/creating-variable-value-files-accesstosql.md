---
title: Creazione di file di valore della variabile (AccessToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 808595c3-8ef1-40bd-a93e-5cf237950e08
caps.latest.revision: 15
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2ebc00ea1b5fc7eb9ca2383d8887b522f59428d1
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="creating-variable-value-files-accesstosql"></a>Creazione di file di valore della variabile (AccessToSQL)
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
  
## <a name="variable-value-file-validation"></a>Valore della variabile File convalida  
L'utente facilmente è in grado di convalidare il file di valore della variabile nel file di definizione dello schema **ConsoleScriptVariablesSchema.xsd** disponibile nella cartella 'Schemi'.  
  
## <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo nella console di gestione è [creare i file di connessione del Server &#40; AccessToSQL &#41;](../../ssma/access/creating-the-server-connection-files-accesstosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[Creazione dei file di connessione del Server (accesso)](http://msdn.microsoft.com/en-us/829153be-aa8e-4162-87e8-69882feecf19)  
  

