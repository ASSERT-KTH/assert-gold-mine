# How to run computational experiments?

This document describes the alternatives we have to run our experiments.

## Physical machines hosted in Assert

* Individual NUC
* repairnator: 130.237.222.185, 125GB RAM, two GPUs
* pellow: 130.237.224.46, 46GB RAM, one GPU
* tiramisu: 130.237.224.95, 46GB RAM, one GPU

## Physical machines hosted at KTH/PDC

* croaker: croaker.eecs.kth.se, 130.237.72.200, 500GB RAM, 128 processors (AMD EPYC 7742 64-Core Processor, 1495 Mhz) 

For more machines, see <https://intra.kth.se/en/it/arbeta-pa-distans/unix/servers-1.971157>

## SNIC Cluster

We have/had SNIC projects in four clusters, HPC2N, PDC, Alvis@C3SE, and Berzelius@NSC.
The last two are suited for GPU-intensive jobs.

Open an account on https://supr.snic.se/, and ask to join an existing project on https://supr.snic.se/project/.

For Berzelius the PI is He Ye (search for her name). 
For the others the PI is Martin Monperrus.

Expert in the team for questions: Zimin, Javier Ron, Zhongxing

See documentation at the official documentation websites and at <https://github.com/gluckzhang/assert-gold-mine/blob/master/docs/snic-run-experiments.md>

## WASP Cluster

We can have virtual machines in the WASP cluster operated by Ericsson. 
OpenShift interface

We self-operate(d) a Kubernetes cluster there. Can be used with [argo](https://github.com/argoproj/argo) (Javier has done this)


## Cloud

We can spawn VMs or any other cloud services on Azure. The costs are paid on a research grant. 

### Microsoft Azure

We have a Microsoft Azure account. Expert in the team for questions: Cesar, Zimin, Javier

### Google Cloud

We have a Google Cloud GCP account. 

Expert in the team for questions: Cesar, Zimin

### VM on Google Cloud

We have a GCP account.

## Not enough?

Just ask on the mailing-list :)
