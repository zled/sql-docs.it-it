---
title: Gestione connessione Azure HDInsight | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPHDICM.F1
- SQL11.DTS.DESIGNER.AFPHDICM.F1
ms.assetid: 850a978d-5dba-45b6-a10e-306aafbc353d
caps.latest.revision: 2
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: eb0ab3ce5576297b1c3b8667883b2f23f125913f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37324681"
---
# <a name="azure-hdinsight-connection-manager"></a>Gestione connessione Azure HDInsight
La **gestione connessione Azure HDInsight** consente a un pacchetto SSIS di connettersi a un cluster HDInsight di Azure.

Per creare e configurare una **gestione connessione Azure HDInsight**, eseguire la procedura seguente:

1. Nella finestra di dialogo **Aggiungi gestione connessione SSIS** selezionare **AzureHDInsight**e fare clic su **Aggiungi**.
2. Nella finestra di dialogo **Editor gestione connessione Azure HDInsight** specificare il **nome DNS del cluster** (senza il prefisso del protocollo), il **nome utente** e la **password** del cluster HDInsight a cui connettersi.
3. Scegliere **OK** per chiudere la finestra di dialogo.
4. È possibile visualizzare le proprietà del componente Gestione connessione create nella finestra **Proprietà** .
