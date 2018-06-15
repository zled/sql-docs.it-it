---
title: Sulle origini dati e i driver | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC data source administrator [ODBC], concepts
ms.assetid: 2bb83ef1-4bbe-4be3-8c32-c4d1140aae1d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 15b6a801fe6c768df9b0eb92a3faf917ac5a0b86
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32904966"
---
# <a name="about-drivers-and-data-sources"></a>Sui driver e origini dati
*I driver* sono i componenti che elaborano le richieste ODBC e restituiscono dati all'applicazione. Se necessario, i driver di modificare la richiesta di un'applicazione in un formato che è stato riconosciuto dall'origine dati. Per aggiungere o eliminare un driver dal computer, è necessario utilizzare il programma di installazione del driver.  
  
 *Origini dati* sono i database o i file aperti da un driver e sono identificati da un nome di origine dati (DSN). Utilizzare Amministrazione origine dati ODBC per aggiungere, configurare ed eliminare origini dati dal sistema. Nella tabella seguente sono descritti i tipi di origini dati che possono essere utilizzate.  
  
|Origine dati|Description|  
|-----------------|-----------------|  
|Utente|I DSN utente sono locali in un computer e possono essere utilizzati solo per l'utente corrente. Vengono registrati nel sottoalbero del Registro di sistema HKEY_CURRENT_USER.|  
|Sistema|DSN di sistema sono locali in un computer anziché dedicato a un utente. Il sistema o qualsiasi utente con privilegi è possibile utilizzare un'origine dati configurato con un DSN di sistema. DSN di sistema vengono registrati nel sottoalbero HKEY_LOCAL_MACHINE del Registro di sistema.|  
|File|DSN su file sono origini basate su file che possono essere condivise tra tutti gli utenti che hanno gli stessi driver installati, quindi hanno accesso al database. Queste origini dati non devono essere dedicate a un utente, né essere locale in un computer. Nomi delle origini dati di file non sono identificate dalle voci del Registro di sistema dedicata; al contrario, vengono identificati da un nome di file con estensione DSN.|  
  
 Origini dati utente e di sistema sono noti come *macchina* origini dati, perché sono locali in un computer.  
  
 Ognuna di queste origini dati è disponibile una scheda di **Amministrazione origine dati ODBC** la finestra di dialogo. Per altre informazioni sulle origini dati, vedere [Origini dati](../../odbc/reference/data-sources.md).
