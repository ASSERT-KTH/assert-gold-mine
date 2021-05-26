# How to run computational experiments?

This document describes the alternatives we have to run our experiments.

## 1. Physical machines hosted in Assert

* Individual NUC
* The Repairnator machine (130.237.222.185, 125GB RAM, two GPUs)
* The Pellow machine (130.237.224.46, one GPU)
* The Tiramisu machine (130.237.224.95, 46GB RAM, one GPU)

## 2. Shared Unix servers from KTH/EECS

Connection through SSH, see <https://intra.kth.se/en/it/arbeta-pa-distans/unix/servers-1.971157>

(Martin uses `tray`)

## 3. SNIC Cluster

We have SNIC projects in two clusters, HPC2N and PDC.

Open an account on https://supr.snic.se/, and ask to join an existing project on https://supr.snic.se/project/

Expert in the team for questions: Zimin, Javier Ron, Zhongxing

See documentation at <https://github.com/gluckzhang/assert-gold-mine/blob/master/docs/snic-run-experiments.md>

## 4. Virtual machines

### VM on Microsoft Azure

We can spawn a VM on Azure. The costs are paid on a research grant. Monthly budget for the whole team: 10,000 SEK.

Expert in the team for questions: Cesar, Zimin, Javier

### VM on WASP Cluster

We can have virtual machines in the WASP cluster operated by Ericsson. 
OpenShift interface

Ask long to have a VM

## 5. Kubernetes cluster

Long is running a Kubernetes cluster. Can be used with [argo](https://github.com/argoproj/argo) (Javier has done this)

## 6. Google Colab

If the experiment is in Python, Google Colab is an option @Ye

## Dedicated server hosted at PDC  (Down now :( )

We have a server at PDC. Docker is available.

Expert in the team for questions: Javier and Nicolas

## Not enough?

Just ask on the mailing-list :)
