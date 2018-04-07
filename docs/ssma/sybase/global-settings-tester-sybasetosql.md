---
title: Impostazioni globali (Tester) (SybaseToSQL) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 6f0b9cea-5a24-4e42-8bbf-c4516b00da23
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8091140978d417fa33beed187f055b26af2b9d31
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="global-settings-tester-sybasetosql"></a>Impostazioni globali (Tester) (SybaseToSQL)
Utilizzare la pagina Tester del **impostazioni globali** la finestra di dialogo per specificare le impostazioni per SSMA Tester.  
  
Per accedere a impostazioni di Tester, scegliere il **strumenti** dal menu **impostazioni globali**e fare clic su **Tester** nella parte inferiore del riquadro a sinistra.  
  
## <a name="options"></a>Opzioni  
**Analisi oggetto testabili**  
Questa impostazione specifica se eseguire l'analisi degli oggetti testabile. Selezionare **Sì** se si desidera che il Tester di SSMA per analizzare e controllare automaticamente gli oggetti dipendenti. Set di opzioni predefinito è **Sì**.  
  
Le opzioni seguenti sono disponibili per questa impostazione:  
  
1.  Sì  
  
2.  no  
  
**Modalità di salvataggio di tabelle ausiliarie**  
Questa impostazione specifica la modalità salvare le tabelle ausiliarie interne create durante l'esecuzione di test case. Per questa impostazione specifica è possibile impostare le opzioni seguenti:  
  
1.  Elimina sempre  
  
2.  Salva sempre  
  
3.  Se il confronto tra le tabelle non è stato possibile salvare  
  
4.  Chiedere utente se confronto tra le tabelle non riuscito  
  
È impostata l'opzione predefinita: **Elimina sempre**.  
  
**Eseguire il rollback di dati**  
Questa impostazione specifica se eseguire un'operazione di rollback dopo l'esecuzione di ogni test case. Set di opzioni predefinito è **n**.  
  
Le opzioni seguenti sono disponibili per questa impostazione:  
  
1.  Sì  
  
2.  no  
  
**Arrestare l'esecuzione di test dopo il primo errore**  
Questa impostazione specifica se interrompere l'esecuzione test case corrente, se si è verificato un errore durante l'esecuzione. Set di opzioni predefinito è **Sì**.  
  
Le opzioni seguenti sono disponibili per questa impostazione:  
  
1.  Sì  
  
2.  no  
  
## <a name="see-also"></a>Vedere anche  
[Completamento della preparazione del Test Case &#40;SybaseToSQL&#41;](../../ssma/sybase/finishing-test-case-preparation-sybasetosql.md)  
  
