---
title: Impostazioni (migrazione) (AccessToSQL) del progetto | Documenti Microsoft
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
helpviewer_keywords:
- Migration settings
- Project Settings dialog box, Migration
ms.assetid: 4caebc9c-8680-4b99-a8fa-89c43161c95d
caps.latest.revision: 14
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3faaf19a1c591628ef97c4fe33fa0a54d4b077d5
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="project-settings-migration-accesstosql"></a>Impostazioni del progetto (migrazione) (AccessToSQL)
Le impostazioni del progetto di migrazione consentono di configurare la modalità di migrazione dati per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure.  
  
Il riquadro di migrazione è disponibile nel **impostazioni progetto** e **impostazioni di progetto predefinite** finestre di dialogo.  
  
-   Utilizzare il **impostazioni progetto** la finestra di dialogo per impostare le opzioni di configurazione per il progetto corrente. Per accedere a impostazioni di migrazione, scegliere il **strumenti** dal menu **impostazioni progetto**, fare clic su **generale** nella parte inferiore del riquadro sinistro e quindi fare clic su **migrazione**.  
  
-   Utilizzare il **impostazioni di progetto predefinite** la finestra di dialogo per impostare le opzioni di configurazione per tutti i progetti. Per accedere a impostazioni di migrazione, scegliere il **strumenti** dal menu **impostazioni di progetto predefinite**, selezionare il tipo di progetto in **versione di destinazione della migrazione** casella combinata di cui si desidera accedere alle impostazioni, fare clic su **generale** nella parte inferiore del riquadro sinistro e quindi fare clic su **migrazione**.  
  
## <a name="options"></a>Opzioni  
**Vincoli CHECK**  
Specifica se SSMA deve verificare i vincoli durante l'aggiunta di dati alle tabelle.  
  
-   **Modalità predefinita**: False  
  
-   **Modalità ottimistica**: True  
  
-   **Modalità**: False  
  
**Attive trigger**  
Specifica se SSMA deve attivare i trigger di inserimento durante l'aggiunta di dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tabelle.  
  
-   **Modalità predefinita**: False  
  
-   **Modalità ottimistica**: True  
  
-   **Modalità**: False  
  
**Mantieni valori Identity**  
Specifica se SSMA mantiene i valori di identità di accesso durante l'aggiunta di dati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Se questo valore è False, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] assegna i valori identity.  
  
-   **Modalità predefinita**: True  
  
-   **Modalità ottimistica**: True  
  
-   **Modalità**: False  
  
**Mantieni valori Null**  
Specifica se SSMA consente di mantenere i valori null nei dati di origine durante l'aggiunta di dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], indipendentemente dal fatto che i valori predefiniti specificati nella [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
-   **Modalità predefinita**: True  
  
-   **Modalità ottimistica**: False  
  
-   **Modalità**: True  
  
**Blocchi di tabella**  
Specifica se SSMA consente di bloccare le tabelle durante l'aggiunta di dati alle tabelle durante la migrazione dei dati. Se il valore è False, SSMA Usa blocchi di riga.  
  
-   **Modalità predefinita**: True  
  
-   **Modalità ottimistica**: True  
  
-   **Modalità**: True  
  
**Sostituire le date non supportate**  
Specifica se SSMA è necessario correggere date accesso precedente a quello meno recente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] datetime data (01 gennaio 1753).  
  
-   Per mantenere i valori di data corrente, selezionare **non eseguire alcuna operazione**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]in una colonna datetime non accetta le date precedenti 01 gennaio 1753. Se si utilizzano le date precedenti, è necessario convertire i valori datetime ai valori di carattere.  
  
-   Per convertire le date precedenti 01 gennaio 1753 su NULL, selezionare **sostituire con il valore NULL**.  
  
-   Per sostituire le date precedenti 01 gennaio 1753 con una data, selezionare **sostituire con più vicino di date supportato**. Se si seleziona questo valore, per impostazione predefinita più vicina supportata data verrà selezionata come 01 gennaio 1753.  
  
**Dimensioni batch**  
Dimensioni batch utilizzate durante la migrazione dei dati. Una transazione viene registrata dopo ogni batch. Per impostazione predefinita, le dimensioni del batch per tutti gli schemi sono 10000.  
  
## <a name="see-also"></a>Vedere anche  
[Reference(Access) dell'interfaccia utente](http://msdn.microsoft.com/en-us/af24c303-4a41-449b-9c86-d6558a97e839)  
  

