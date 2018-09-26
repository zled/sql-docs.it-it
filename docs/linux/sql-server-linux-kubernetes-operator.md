---
title: SQL Server Always On gruppo Kubernetes operatore globali requisiti di disponibilità
description: Questo articolo illustra i parametri per Kubernetes Always On di SQL Server requisiti di disponibilità gruppo operatore globali
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 2d5699ae16a02346f9dded732180b16615087d16
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2018
ms.locfileid: "46715206"
---
# <a name="sql-server-always-on-availability-group-kubernetes-operator-parameters"></a>SQL Server Always On gruppo Kubernetes operatore i parametri di disponibilità

Un gruppo di disponibilità Always On su Kubernetes richiede un operatore. Viene descritto l'operatore in un file con estensione yaml.  Vedere un esempio della specifica nella [in questa esercitazione](tutorial-sql-server-ag-kubernetes.md).

Questo articolo illustra le variabili di ambiente globali operatore.

## <a name="example"></a>Esempio

L'esempio seguente illustra una distribuzione per il `mssql-operator`.

## <a name="global-environment-variables"></a>Variabili di ambiente globali

* `MSSQL_K8S_POD_NAMESPACE` 
  * Obbligatorio
  * **Descrizione**: lo spazio dei nomi Kubernetes dell'operatore.

* `MSSQL_K8S_SQL_WRITE_LEASE_PERIOD_SECONDS`
  * Facoltativo
  * **Descrizione**: la durata di sql server esterne scrivere lease per mantenere scrivibile sql server ed evitare gli scenari di "split Brain". Repliche secondarie attendere la scadenza dopo la designazione di un nuovo leader.

* `MSSQL_K8S_MONITOR_PERIOD_SECONDS`
  * Facoltativo
  * **Descrizione**: il periodo per il monitoraggio se lo stato del gruppo di disponibilità. Determina la rapidità le repliche vengono aggiunti ed eliminate. Deve essere minore di `MSSQL_K8S_SQL_WRITE_LEASE_PERIOD_SECONDS`.
  * **Default**: 1

* `MSSQL_K8S_LEASE_DURATION_SECONDS`
  * Facoltativo
  * **Descrizione**: durata del lease responsabile gruppo di disponibilità. Determina il tempo di attesa nelle repliche secondarie prima bacino di utenza nuovamente se la replica primaria arrestato in modo anomalo. Ciò è diverso da quello di lease di scrittura di SQL Server. 
  * **Default**: 10
  
  >[!NOTE]
  >Altre impostazioni calcolato automaticamente in base `MSSQL_K8S_LEASE_DURATION_SECONDS`.

* `MSSQL_K8S_RENEW_DEADLINE_SECONDS`
  * Facoltativo
  * **Descrizione**: durata che la replica primaria acting Ritenta leadership l'aggiornamento prima di rinunciare. Deve essere minore di `MSSQL_K8S_LEASE_DURATION_SECONDS`.
  * **Default**:  `MSSQL_K8S_LEASE_DURATION_SECONDS` /2

* `MSSQL_K8S_RETRY_PERIOD_SECONDS`
  * Facoltativo
  * **Descrizione**: durata di acting [master](http://kubernetes.io/docs/concepts/architecture/master-node-communication/) attenderà prima di rinnovare il lease leader. Deve essere minore di `MSSQL_K8S_LEASE_DURATION_SECONDS`.
  * **Default**:  `MSSQL_K8S_RENEW_DEADLINE_SECONDS` /2

* `MSSQL_K8S_ACQUIRE_PERIOD_SECONDS` 
  * Facoltativo
  * **Descrizione**: periodo di repliche secondarie di eseguire il polling se il lease leader è scaduto. 
  * **Default**: 1


  ## <a name="next-steps"></a>Passaggi successivi

[Gruppo di disponibilità SQL Server in cluster Kubernetes](sql-server-ag-kubernetes.md)