---
title: Duplicare le tabelle | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: table-view-index, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- copying tables
- tables [SQL Server], duplicating
- duplicating tables
- table copying [SQL Server]
ms.assetid: c6b07423-d1e5-4e5e-8681-5088921f5df3
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6df05fc03563c88a10a7c56b71536e41068ffb05
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47845479"
---
# <a name="duplicate-tables"></a>Duplicare le tabelle
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  È possibile duplicare una tabella esistente in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)] creando una nuova tabella e copiando quindi le informazioni di colonna da una tabella esistente.  
  
> [!IMPORTANT]  
>  Questa operazione consente di duplicare solo la struttura di una tabella, non le righe della tabella.  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Security](#Security)  
  
-   **Per duplicare una tabella:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 È necessaria l'autorizzazione CREATE TABLE nel database di destinazione.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-duplicate-a-table"></a>Per duplicare una tabella  
  
1.  Verificare di essere connessi al database in cui si desidera creare la tabella e che tale database sia selezionato in Esplora oggetti.  
  
2.  In Esplora oggetti fare clic con il pulsante destro del mouse su **Tabelle** e scegliere **Nuova tabella**.  
  
3.  In Esplora oggetti fare clic con il pulsante destro del mouse sulla tabella da copiare e scegliere **Progetta**.  
  
4.  Selezionare le colonne della tabella esistente e quindi scegliere **Copia** dal menu **Modifica**.  
  
5.  Tornare nella nuova tabella e selezionare la prima riga.  
  
6.  Scegliere **Incolla** dal menu **Modifica**.  
  
7.  Scegliere **Salva***nome tabella* dal menu **File**.  
  
8.  Nella finestra di dialogo **Scegli nome** digitare un nome per la nuova tabella e quindi fare clic su **OK**.  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
  
#### <a name="to-duplicate-a-table-in-query-editor"></a>Per duplicare una tabella in Editor di query  
  
1.  Verificare di essere connessi al database in cui si desidera creare la tabella e che tale database sia selezionato in Esplora oggetti.  
  
2.  Fare clic con li pulsante destro del mouse sulla tabella da duplicare, scegliere **Crea script per tabella**, quindi **CREATE in**e selezionare **Nuova finestra editor di query**.  
  
3.  Consente di modificare il nome della tabella.  
  
4.  Rimuovere qualsiasi colonna non necessaria nella nuova tabella.  
  
5.  Fare clic su **Esegui**.  
  
  
