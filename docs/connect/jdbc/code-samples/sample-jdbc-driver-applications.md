---
title: Applicazioni del Driver JDBC di esempio | Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e136b87c-a138-45d6-8c3e-bcef94b7e483
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c62942580b403bbacd62c6fc65e0a19b0960f1e6
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 08/02/2018
ms.locfileid: "39457815"
---
# <a name="sample-jdbc-driver-applications"></a>Applicazioni di esempio del driver JDBC

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Le applicazioni di esempio [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] illustrano diverse funzionalità del driver JDBC. Illustrano anche le regole di programmazione ottimali a cui attenersi quando si usa il driver JDBC con un database di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].  
  
Tutte le applicazioni di esempio sono contenute nei file di codice *.java che è possibile compilare ed eseguire nel computer locale e che si trovano in varie sottocartelle nel seguente percorso:  

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples  
```

 Negli argomenti di questa sezione viene descritto come configurare ed eseguire le applicazioni di esempio ed è inclusa una trattazione su ciò che è stato illustrato nelle applicazioni di esempio.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
| Argomento                                                                                                                  | Descrizione                                                                                                                                                                                                                                                                   |
| ---------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Connessione e recupero dei dati](../../../connect/jdbc/code-samples/connecting-and-retrieving-data.md)                              | Queste applicazioni di esempio illustrano come connettersi a un database di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]. Descrivono anche le diverse modalità di recupero dei dati da un database di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]. |
| [Uso dei tipi di dati &#40;JDBC&#41;](../../../connect/jdbc/code-samples/working-with-data-types-jdbc.md)                        | Queste applicazioni di esempio illustrano come usare i metodi del tipo di dati del driver JDBC per lavorare con i dati in un database di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].                                                                                              |
| [Utilizzo dei set di risultati](../../../connect/jdbc/code-samples/working-with-result-sets.md)                                          | Queste applicazioni di esempio illustrano come usare i set di risultati per elaborare i dati contenuti in un database di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].                                                                                                            |
| [Utilizzo di dati di grandi dimensioni](../../../connect/jdbc/code-samples/working-with-large-data.md)                                            | Queste applicazioni di esempio illustrano come usare il buffer adattivo per recuperare dati con valori di grandi dimensioni da un database di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] senza l'overhead dei cursori server.                                                         |
| [Individuazione dati e classificazione SQL](../../jdbc/code-samples/data-discovery-and-classification-sample.md) | Questa applicazione di esempio viene illustrato come recuperare le informazioni di individuazione dati e classificazione contenuti in un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] database da un oggetto set di risultati tramite il Driver JDBC.                                            |
  
## <a name="see-also"></a>Vedere anche

[Panoramica del driver JDBC](../../../connect/jdbc/overview-of-the-jdbc-driver.md)