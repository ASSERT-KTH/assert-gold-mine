# How to run computational experiments?

This document describes the alternatives we have to run our experiments.

## 1. Physical machines hosted in Assert

* Individual NUC
* repairnator: 130.237.222.185, 125GB RAM, two GPUs
* pellow: 130.237.224.46, 46GB RAM, one GPU
* tiramisu: 130.237.224.95, 46GB RAM, one GPU

## 2. Physical machines hosted at KTH/PDC

* croaker: croaker.pdc.kth.se, 130.242.72.40, 500GB RAM, 128 processors (AMD EPYC 7742 64-Core Processor, 1495 Mhz) 

For more machines, see <https://intra.kth.se/en/it/arbeta-pa-distans/unix/servers-1.971157>

## 3. SNIC Cluster

We have SNIC projects in two clusters, HPC2N and PDC.

Open an account on https://supr.snic.se/, and ask to join an existing project on https://supr.snic.se/project/

Expert in the team for questions: Zimin, Javier Ron, Zhongxing

See documentation at <https://github.com/gluckzhang/assert-gold-mine/blob/master/docs/snic-run-experiments.md>

## 4. Cloud machines

### VM on Microsoft Azure

We can spawn a VM on Azure. The costs are paid on a research grant. Monthly budget for the whole team: 10,000 SEK.

Expert in the team for questions: Cesar, Zimin, Javier

### VM on Ericsson WASP Cluster

We can have virtual machines in the WASP cluster operated by Ericsson. 
OpenShift interface

We self-operate(d) a Kubernetes cluster there. Can be used with [argo](https://github.com/argoproj/argo) (Javier has done this)

### VM on Google Cloud

We have a GCP account.

## 6. Google Colab

If the experiment is in Python, Google Colab is an option @Ye

## Not enough?

Just ask on the mailing-list :)
