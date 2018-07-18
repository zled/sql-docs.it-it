---
title: Aggiungere colonne a una tabella (motore di database) | Microsoft Docs
ms.custom: ''
ms.date: 10/27/2016
ms.prod: sql
ms.prod_service: table-view-index, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- inserting columns
- columns [SQL Server], adding
- adding columns
ms.assetid: abeb8d52-d562-4e29-9e1e-2923ae874859
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: a2785f0ebfd810d95f50f741d8544170730da52f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33005848"
---
# <a name="add-columns-to-a-table-database-engine"></a>Aggiungere colonne a una tabella (Motore di database)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

 > Per il contenuto relativo alle versioni precedenti di SQL Server, vedere [Aggiungere colonne a una tabella (Motore di database)](https://msdn.microsoft.com/en-US/library/ms190238(SQL.120).aspx).


  In questo argomento viene descritto come aggiungere nuove colonne a una tabella in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  

  ##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
 L'utilizzo dell'istruzione ALTER TABLE per aggiungere automaticamente colonne a una tabella aggiunge tali colonne alla fine della tabella. Se si desidera le colonne in un ordine specifico all'interno della tabella, utilizzare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Tuttavia, notare che questa non è una procedura consigliata di progettazione del database. La procedura consigliata è specificare l'ordine nel quale le colonne vengono restituite all'applicazione e il livello della query. Non è necessario basarsi sull'utilizzo di SELECT * per restituire tutte le colonne nell'ordine previsto basato sull'ordine nel quale sono definiti nella tabella. Nelle query e nelle applicazioni, specificare sempre le colonne per nome nell'ordine nel quale si desidera visualizzarle.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 È necessario disporre dell'autorizzazione ALTER per la tabella.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-insert-columns-into-a-table-with-table-designer"></a>Per inserire colonne in una tabella con Progettazione tabelle  
  
1.  In **Esplora oggetti**fare clic con il pulsante destro del mouse sulla tabella a cui si vogliono aggiungere colonne e scegliere **Progetta**.  
  
2.  Fare clic sulla prima cella vuota nella colonna **Nome colonna** .  
  
3.  Immettere il nome della colonna nella cella. Il nome della colonna non può essere omesso.  
  
4.  Premere TAB per posizionarsi sulla cella **Tipo di dati** e selezionare un tipo di dati dall'elenco a discesa. Si tratta di un valore obbligatorio. Se non viene specificato, verrà assegnato un valore predefinito.  
  
    > [!NOTE]  
    >  Il valore predefinito può essere modificato nella finestra di dialogo **Opzioni** in **Strumenti di database**.  
  
5.  Proseguire con la definizione delle altre proprietà della colonna nella scheda **Proprietà colonne** .  
  
    > [!NOTE]  
    >  Quando si crea una nuova colonna, le vengono assegnati i valori predefiniti per le diverse proprietà. Tali valori possono comunque essere modificati nella scheda **Proprietà colonne** .  
  
6.  Dopo avere completato l'aggiunta delle colonne, scegliere **Salva** **nome tabella**  dal menu *File*.  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
  
#### <a name="to-insert-columns-into-a-table"></a>Per inserire le colonne in una tabella  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Negli esempi seguenti vengono aggiunte due colonne alla tabella `dbo.doc_exa`. Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**.  
  
```  
ALTER TABLE dbo.doc_exa ADD column_b VARCHAR(20) NULL, column_c INT NULL ;  
```  
  
####  <a name="FollowUp"></a> Per altre informazioni, vedere [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
  
  
