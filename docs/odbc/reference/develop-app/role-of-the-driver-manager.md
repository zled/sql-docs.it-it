---
title: Ruolo di gestione Driver | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- diagnostic information [ODBC], SqlGetDiagField
- diagnostic information [ODBC], driver manager error checking
- SQLGetDiagField function [ODBC], driver manager
- SQLGetDiagRec function [ODBC], driver manager
- ODBC driver manager [ODBC]
- diagnostic information [ODBC], SqlGetDiagRec
- driver manager [ODBC], error checking
ms.assetid: 7b861c82-357e-4590-8074-45136e9ed15e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 89d4b99deb3599765dfec30c5d2ec28975c8f875
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="role-of-the-driver-manager"></a>Ruolo di gestione Driver
Gestione Driver determina l'ordine finale in cui restituire i record di stato che viene generata. In particolare, determina il record è il valore più alto e deve essere restituito prima. Il driver è responsabile per l'ordinamento dei record di stato che viene generata. Se i record di stato vengono registrati da Gestione Driver sia il driver, Driver Manager è responsabile ordinandoli. Per ulteriori informazioni, vedere [sequenza di record di stato](../../../odbc/reference/develop-app/sequence-of-status-records.md).  
  
 Il gestore di Driver non più errori possibile. In questo modo ogni driver di controllo per gli stessi errori. Ad esempio, se un argomento di funzione accetta un numero discreto di valori, ad esempio *operazione* in **SQLSetPos**, Driver Manager verifica che il valore specificato è valido.  
  
 Nelle sezioni seguenti vengono descritti i tipi di condizioni controllate da Gestione Driver. Non sono progettati per essere completo; per un elenco completo di SQLSTATE restituisce gestione Driver, vedere la sezione "Diagnostics" di ogni funzione. la descrizione di ogni controllo apportata da Gestione Driver viene avviato con le lettere "(DM)". Vedere anche le tabelle di transizione di stato in [tabelle di transizione dello stato di appendice b: ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md); gli errori indicati tra parentesi vengono rilevati da Gestione Driver.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Controlli del valore dell'argomento](../../../odbc/reference/develop-app/argument-value-checks.md)  
  
-   [Controlli della transizione di stato](../../../odbc/reference/develop-app/state-transition-checks.md)  
  
-   [Controlli degli errori generali](../../../odbc/reference/develop-app/general-error-checks.md)  
  
-   [Errore di Gestione driver e controlli di avviso](../../../odbc/reference/develop-app/driver-manager-error-and-warning-checks.md)
