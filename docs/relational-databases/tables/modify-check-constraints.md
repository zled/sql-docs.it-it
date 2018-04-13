---
title: Modificare vincoli CHECK | Microsoft Docs
ms.custom: ''
ms.date: 06/28/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-tables
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CHECK constraints, modifying
- modifying constraints
- constraints [SQL Server], check
- constraints [SQL Server], modifying
ms.assetid: f22daef8-e350-40ef-8ff0-b5f87d1d9e56
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 23af1baa5b43796d326aea114e4b2ae2a3a30382
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/10/2018
---
# <a name="modify-check-constraints"></a>Modifica di vincoli CHECK
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  È possibile modificare un vincolo CHECK in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)] quando si desidera modificare l'espressione del vincolo o le opzioni che lo abilitano o disabilitano al verificarsi di specifiche condizioni.  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Sicurezza](#Security)  
  
-   **Per modificare un vincolo CHECK:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 È necessario disporre dell'autorizzazione ALTER per la tabella.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-modify-a-check-constraint"></a>Per modificare un vincolo CHECK  
  
1.  In **Esplora oggetti**fare clic con il pulsante destro del mouse sulla tabella che contiene il vincolo CHECK e selezionare **Progetta**.  
  
2.  Scegliere **Vincoli CHECK...** nel menu **Progettazione tabelle**.  
  
3.  Nella finestra di dialogo **Vincoli CHECK** selezionare il vincolo che si desidera modificare in **Vincolo CHECK selezionato**.  
  
4.  Completare un'operazione dalla tabella seguente:  
  
    |Per|seguire le operazioni di seguito riportate|  
    |--------|------------------------|  
    |Modificare l'espressione del vincolo|Digitare la nuova espressione nel campo **Espressione** .|  
    |Rinominare il vincolo|Digitare un nuovo nome nel campo **Nome** .|  
    |Applicare il vincolo a dati esistenti|Selezionare l'opzione **Verifica dati esistenti durante la creazione o l'attivazione** .|  
    |Disabilitare il vincolo in caso di aggiunta di nuovi dati alla tabella o di aggiornamento di dati esistenti nella tabella|Deselezionare l'opzione **Attiva vincolo per istruzioni INSERT e UPDATE** .|  
    |Disabilitare il vincolo quando un agente di replica accoda o aggiorna dati nella tabella.|Deselezionare l'opzione **Attiva per replica** .|  
  
    > [!NOTE]  
    >  Alcuni database dispongono di funzionalità differenti per i vincoli CHECK.  
  
5.  Scegliere **Chiudi**.  
  
6.  Scegliere **Salva***nome tabella* dal menu **File**.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 **Per modificare un vincolo CHECK**  
  
 Per modificare un vincolo `CHECK` utilizzando [!INCLUDE[tsql](../../includes/tsql-md.md)], è innanzitutto necessario eliminare il vincolo `CHECK` esistente e quindi crearlo di nuovo con la nuova definizione. Per altre informazioni, vedere [Eliminazione dei vincoli CHECK](../../relational-databases/tables/delete-check-constraints.md) e [Creare vincoli CHECK](../../relational-databases/tables/create-check-constraints.md).  
  
###  <a name="TsqlExample"></a>  
