---
title: Modalità SQL (MySQLToSQL) | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-mysql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: d840ee51-b863-4e77-84aa-37d3f094bfed
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 12dbdec5d9c56f70e44933a4031c55c5e0b518a1
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="sql-modes-mysqltosql"></a>Modalità SQL (MySQLToSQL)
SSMA per MySQL può operare in modalità diverse di SQL che è possibile applicare queste modalità in modo diverso per diversi client.  
  
Modalità di definire la sintassi SQL che devono supportare MySQL e il tipo di convalida dei dati controlla che l'esecuzione di. Questo rende più semplice per utilizzare MySQL in ambienti diversi e utilizzare MySQL con SQL Server.  
  
## <a name="sql-modes-grid"></a>SQL modalità griglia:  
  
-   SQL modalità griglia a livello di radice contiene le colonne seguenti: **nome modalità SQL**, **caricati modalità SQL**, e **efficace modalità SQL**.  
  
-   Griglia di modalità SQL al database categorie, Database, tabella categoria, le istruzioni, categoria di viste, tabella, vista, funzioni, procedure, funzione definita dall'utente e il livello di oggetto evento contiene le colonne seguenti: **nome modalità SQL**, **ereditata modalità SQL**, e **efficace modalità SQL**.  
  
-   SQL modalità griglia a livello di Stored Procedure, una funzione archiviata e Trigger contiene le colonne seguenti: **nome modalità SQL**, **modalità originale di SQL**, e **efficace modalità SQL**.  
  
> [!NOTE]  
> Modalità gruppo verrà visualizzata grassetto, sotto la colonna 'SQL modalità Name'.  
  
## <a name="loaded-sql-modes"></a>Modalità di caricamento di SQL  
Queste sono le modalità di SQL, che possono essere IMPOSTATI a livello di sessione o radice. Impossibile modificare o modificare le modalità SQL una volta caricati nel database di destinazione.  
  
## <a name="inherited-sql-modes"></a>Modalità ereditato SQL  
Queste sono le modalità di SQL, vengono ereditati dal nodo padre corrispondente.  
  
Ad eccezione delle categorie di funzioni, procedure, categoria di eventi e trigger, tali modalità SQL sono presenti tutti i livelli (oggetto di database, tabella categorie, categoria di istruzioni, viste, tabella, vista, funzioni, procedure, funzione definita dall'utente ed evento).  
  
> [!NOTE]  
> Selezionando il **eredita da padre** casella di controllo ereditate modalità SQL può essere ereditata dal nodo padre. Per impostazione predefinita, questa casella di controllo rimanga selezionata.  
  
## <a name="original-sql-modes"></a>Modalità originale di SQL  
Queste sono le modalità di SQL presenti solo livelli di funzione, Stored Procedure e Trigger.  
  
> [!NOTE]  
> Selezionando il **Usa originale** controllare, le modalità di SQL che sono stati originariamente utilizzata nella funzione corrispondente o è possibile utilizzare stored procedure o trigger. Per impostazione predefinita, questa casella di controllo rimanga selezionata.  
  
## <a name="effective-sql-modes"></a>Modalità efficace SQL  
Modalità SQL effettivo può essere definita a vari livelli nel modo seguente:  
  
-   **A livello di sessione:**  
  
    1.  Tutte le modalità di SQL caricati possono essere chiamate, "Modalità valide di SQL".  
  
    2.  A questo livello, le modalità valide di SQL possono essere direttamente e in modo esplicito modificate.  
  
    3.  La modalità di SQL effettivo che è impostato in modo esplicito non vengono riportata come caricato in modalità SQL e infine viene applicata all'oggetto.  
  
-   **A livello di funzione o stored procedure o trigger:**  
  
    1.  Tutte le modalità di SQL originale può essere chiamato, "Modalità valide di SQL".  
  
    2.  A questo livello, la modalità effettiva di SQL in modo esplicito modificabili solo quando il **Usa originale** casella di controllo è deselezionata.  
  
    3.  La modalità di SQL effettivo che è impostato in modo esplicito non vengono riportata come modalità SQL originale e infine viene applicata all'oggetto.  
  
-   **In nodi diversi da quelli a livello di funzione o stored procedure o trigger:**  
  
    1.  Tutte le modalità di SQL ereditato può essere chiamate, "Modalità valide di SQL".  
  
    2.  A questo livello, la modalità effettiva di SQL in modo esplicito modificabili solo quando il **eredita da padre** casella di controllo è deselezionata.  
  
    3.  La modalità di SQL effettivo che è impostato in modo esplicito non vengono riportata come ereditata modalità SQL e infine viene applicata all'oggetto.  
  
